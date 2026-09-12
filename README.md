# Microgrid Islanding and Scenario Analysis

MATLAB/Simulink simulation of a PV–BESS based microgrid under grid-connected and islanded operating conditions.

## Overview

This project models a microgrid consisting of photovoltaic (PV) generation, a battery energy storage system (BESS), a utility grid, and an electrical load.

The simulation is used to study the response of the microgrid when it transitions from grid-connected operation to islanded operation. The main disturbance occurs at **t = 2 s**, when the utility grid is disconnected and the PV generation is reduced.

The model also includes a simplified frequency-dynamics model, BESS state-of-charge (SOC) calculation, power-balance monitoring, BESS power limitation, and automatic load shedding.

## System Configuration

The simulated system includes:

* 100 kW PV generation
* 100 kW electrical load
* Utility grid
* Battery Energy Storage System (BESS)
* Frequency-dynamics model
* BESS SOC calculation
* Power-balance calculation
* Automatic load-shedding logic
* Simulink Scopes for monitoring system variables

## Simulation Scenarios

### Scenario 1 – Grid-Connected Operation

From 0 to 2 s, the microgrid operates while connected to the utility grid.

* PV power: 100 kW
* Grid power: 50 kW
* Load power: 100 kW
* Initial BESS SOC: 60%

### Scenario 2 – Islanded Operation

At **t = 2 s**, the utility grid is disconnected. The PV output is simultaneously reduced from 100 kW to 10 kW.

The BESS responds to the resulting power deficit, with its discharge power limited to 80 kW. The load-shedding logic can subsequently reduce the load from 100 kW to 90 kW according to the defined control conditions.

## Main Features

### Grid Disconnection

The utility grid is disconnected at 2 s to initiate islanded operation.

### PV Power Disturbance

PV generation is reduced from:

```text
100 kW → 10 kW
```

after the disturbance.

### BESS Support

The BESS supplies power to the islanded microgrid. Its discharge power is limited using a Saturation block:

```text
BESS maximum discharge = 80 kW
```

### SOC Monitoring

The BESS starts with an initial SOC of:

```text
SOC = 60%
```

The SOC is calculated by integrating the battery power with the required scaling factors.

### Frequency Dynamics

A simplified swing-equation based model is used to observe the frequency response following the change in power balance.

The nominal frequency is:

```text
50 Hz
```

### Load Shedding

Automatic load shedding is implemented using frequency and BESS/SOC operating conditions.

The conditions are combined using an OR gate, which controls a Switch block:

```text
Normal load      = 100 kW
Shed load        = 90 kW
```

## Key Simulation Results

The simulation demonstrates:

* Grid power changing from 50 kW to 0 kW after islanding
* PV power reduction from 100 kW to 10 kW
* BESS response to the resulting power deficit
* BESS reaching its 80 kW power limit
* Automatic reduction of load from 100 kW to 90 kW
* Frequency variation during islanded operation
* BESS SOC variation
* Monitoring of the generation-load power imbalance

## Repository Contents

```text
Simulink/
    microgrid_islanding.slx

Report/
    Microgrid_Islanding_and_Scenario_Analysis.pdf

Results/
    Simulation result plots and Scope screenshots

Documentation/
    Final Simulink model/block diagram
```

## Software

* MATLAB
* Simulink

## Report

The complete simulation methodology, model description, results, discussion, and conclusion are available in the project report.
