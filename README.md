# SmartGuard-Embedded-Sensor-Monitoring-Simulation
Embedded sensor monitoring simulation in C, implementing finite state machine logic and threshold-based event detection.
# SmartGuard

A small C program that simulates an embedded sensor monitoring system - the kind of logic you'd find in IoT devices or hardware monitoring setups.

## What it does

Generates simulated temperature readings and checks them against thresholds. Based on the value, it puts the system into one of three states - NORMAL, WARNING, or CRITICAL - and logs everything with a timestamp. At the end it prints a summary report.

I used a simple state machine for this since that's how most real embedded systems track sensor data over time, not just a one-off check.

## How to run

gcc -Wall -o smartguard smartguard.c
./smartguard

## Sample output

[16:45:20] Reading #1   -> 87.0 C [CRITICAL]
   >>> ALERT: CRITICAL temperature (87.0 C) - shutting down non-essential systems!
[16:45:20] Reading #2   -> 64.0 C [WARNING]
   >>> WARNING: temperature elevated (64.0 C) - increasing monitoring frequency.
[16:45:20] Reading #3   -> 58.0 C [NORMAL]

Total Readings : 15
Normal         : 7
Warning        : 6
Critical       : 2

## Notes

This is a simulation, not running on actual hardware. The sensor readings are randomly generated instead of coming from a real sensor, and the "alert" just prints to console instead of triggering a buzzer or LED. On real hardware these would be ADC reads and GPIO writes.

Wrote this mainly to practice embedded-style logic (state machines, threshold-based decisions, modular C functions) since most of my hands-on hardware work has been with NodeMCU/Arduino projects (see my other repos).

## Possible next steps

- Multiple sensors running in parallel
- Port this same logic onto actual Arduino/ESP32 hardware
- Read thresholds from a config file instead of hardcoding them
