# mobile-ecg
STM32 based mobile ECG device

This project is an integrated ECG and Heart Rate Monitoring system designed in Altium Designer. It captures biopotential signals from the body, processes them digitally, and visualizes the waveform and heart rate (BPM) on a color TFT display.

## System Overview
The hardware architecture is divided into three primary stages: Signal Acquisition, Processing, and Visualization.

1. Analog Front End (AD8232)
The AD8232 is an integrated signal conditioning block for ECG and other biopotential measurement applications.

Function: It extracts, amplifies, and filters small biopotential signals in the presence of noisy conditions (like those created by motion or remote electrode placement).

Key Features: Integrated Right Arm Drive (RAD) amplifier, leads-off detection, and a two-pole adjustable high-pass filter.

2. Microcontroller (STM32L432KC)
The STM32L432KC (Nucleo-32 form factor compatible) acts as the brain of the system.

ADC: Samples the analog output from the AD8232 at a frequency of 200–500 Hz.

DSP: Implements a digital notch filter (50/60 Hz) and a peak-detection algorithm to calculate the R-R interval.

Communication: Uses SPI to drive the LCD and GPIO for leads-off interrupts.

3. Display (ILI9341)
A 2.4" TFT LCD driven by the ILI9341 controller.

Interface: 4-wire SPI.

Output: Real-time scrolling ECG waveform, Heart Rate (BPM), and Oxygen Saturation (Pulse Ox) placeholders.

## Project Structure (Altium)
The repository contains 2 complete Altium Designer projects:
- Control - the controlling panel with a rotary encoder
- ECG - the mainboard of the device