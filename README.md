# Autonomous Maze-Solving Robot (HCS12 Assembly)

An autonomous mobile robot programmed in **HCS12 Assembly** to navigate an unknown maze using optical line sensors and bumper feedback. The robot follows guide lines, detects intersections, makes navigation decisions, recovers from dead ends through 180° turns, and learns the correct route for reliable return traversal.

This project demonstrates low-level embedded programming, finite state machine design, real-time sensor processing, and autonomous robotic navigation on a resource-constrained microcontroller.

---

## Overview

The objective was to build an embedded navigation system capable of solving an unknown maze completely autonomously.

The robot continuously reads optical line sensors to remain on the guide path while monitoring bumper switches for collision detection. At each intersection, the navigation system determines which direction to take, records successful routes, and backtracks whenever a dead end is encountered.

Unlike a simple line-following robot, this system combines:

- Real-time line tracking
- Intersection detection
- Decision making
- Path memory
- Dead-end recovery
- Autonomous maze solving

Once the robot reaches the destination, it can retrace the learned path back to the starting position without making incorrect decisions.

---

## Features

- Autonomous maze navigation
- Optical line following using infrared sensors
- Detection of T- and L-intersections
- Dead-end detection using front bumper sensors
- Automatic 180° recovery turns
- Learned path storage for efficient return traversal
- Finite State Machine (FSM) based navigation logic
- Real-time motor control and steering
- Fully implemented in HCS12 Assembly

---

## System Architecture

```
          Optical Sensors
                 │
                 ▼
        Sensor Processing
                 │
                 ▼
       Navigation State Machine
                 │
      ┌──────────┴──────────┐
      ▼                     ▼
 Decision Logic        Path Memory
      │                     │
      └──────────┬──────────┘
                 ▼
          Motor Controller
                 │
                 ▼
          Differential Drive
```

---

## Navigation Algorithm

The robot operates using a finite state machine that continuously transitions between navigation states based on sensor input.

Typical execution flow:

1. Detect and follow the guide line.
2. Identify intersections using optical sensors.
3. Choose a branch to explore.
4. Continue until:
   - another intersection is reached, or
   - a dead end is detected.
5. If a dead end is encountered:
   - perform a 180° turn,
   - retrace the previous path,
   - mark the incorrect branch,
   - explore the remaining branch.
6. Repeat until the destination is reached.
7. Retrace the learned route back to the starting point.

This exploration strategy enables the robot to solve previously unknown mazes without prior knowledge of their layout.

---

## Software Components

### Navigation Manager

Coordinates overall robot behavior and transitions between navigation states.

---

### Guidance System

Processes optical sensor readings to maintain accurate line tracking through straight paths, curves, and S-turns.

---

### Intersection Detection

Identifies T- and L-junctions and signals the navigation controller when a routing decision is required.

---

### Motor Controller

Controls differential drive motors to perform:

- Forward movement
- Left turns
- Right turns
- Precise 180° rotations
- Path correction

---

### Collision Recovery

Front bumper switches detect dead ends and obstacles.

Upon collision the robot:

- Stops
- Executes a controlled 180° turn
- Retraces its previous path
- Updates its navigation memory
- Continues exploration

---

## Technologies Used

- HCS12 Microcontroller
- Assembly Language
- Embedded Systems
- Finite State Machines (FSM)
- Optical Line Sensors
- Bumper Switches
- Real-Time Motor Control
- Differential Drive Robotics

---

## Key Engineering Concepts

- Low-level embedded programming
- Sensor fusion
- Event-driven state machines
- Autonomous navigation
- Robot motion control
- Hardware/software integration
- Real-time decision making
- Incremental embedded system debugging

---

## Testing & Validation

The system was validated through incremental subsystem testing before full integration.

Testing included:

- Optical sensor calibration
- Line-following accuracy
- Intersection recognition
- Dead-end recovery
- 180° turning precision
- Navigation state verification
- Full autonomous maze traversal

The completed robot successfully navigated a physical maze and demonstrated reliable autonomous operation during a live class demonstration.

---

## Repository Structure

```
├── main.asm
├── navigation.asm
├── guider.asm
├── motors.asm
├── sensors.asm
├── state_machine.asm
├── interrupts.asm
├── include/
├── documentation/
└── README.md
```

*(Directory names may differ depending on your implementation.)*

---

## Future Improvements

Potential enhancements include:

- PID-based steering control
- Dynamic obstacle avoidance
- Shortest-path optimization
- Wheel encoder odometry
- IMU integration
- EEPROM storage of learned maps
- Graph-based path planning
- Wireless telemetry and debugging

---

## Demo

**Capabilities demonstrated:**

- Line tracking
- S-turn navigation
- Autonomous intersection detection
- Dead-end recovery
- 180° turning
- Maze learning
- Autonomous return traversal

---

## What I Learned

This project strengthened my understanding of:

- Embedded software architecture
- Assembly language programming
- Finite state machine design
- Hardware/software debugging
- Real-time robotic control
- Developing and testing large embedded systems
- Designing reliable autonomous behavior under hardware constraints
