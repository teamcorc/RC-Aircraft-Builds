# RC Aircraft Builds

A public engineering archive for the design, construction, configuration, manufacturing, testing, and continued development of #teamcorc RC aircraft projects.

GitHub Pages:

https://teamcorc.github.io/RC-Aircraft-Builds/

This repository is intentionally organized as an engineering record rather than a conventional build blog. The goal is to preserve enough information to understand how each aircraft was actually constructed and configured at a particular point in its development.

---

## Repository Organization

Aircraft documentation follows this hierarchy:

```text
Manufacturer
└── Aircraft Model / Family
    └── Version
        └── Physical Build
```

This keeps different manufacturers, aircraft families, design revisions, and physical aircraft isolated from one another.

Current manufacturer areas include:

- Flightory
- Nomadium Robotics
- Eclipson
- Titan Dynamics
- Additional manufacturers may be added as projects begin.

Example:

```text
aircraft/
├── flightory/
│   ├── stallion/
│   │   ├── references/
│   │   ├── v1/
│   │   │   └── build-01/
│   │   └── v2/
│   │       └── build-01/
│   ├── super-stingray-vtol/
│   ├── talon-1400/
│   └── stork/
├── eclipson/
├── nomadium-robotics/
│   └── terrahawk-fpv/
└── titan-dynamics/
```

---

## Build-Level Engineering Records

A physical build can contain some or all of the following:

```text
build-01/
├── components/
├── assembly-wiring/
├── ardupilot/
├── flight-testing/
├── engineering/
├── media/
├── downloads/
└── printing/
```

Not every aircraft or build will contain every section. Documentation reflects information actually captured for that physical aircraft.

Typical records include:

- Exact installed hardware
- Component sources and manufacturer documentation
- Firmware
- ArduPilot PARAM files and configuration baselines
- Serial/UART mapping
- Servo and motor output assignments
- Wiring and power topology
- Assembly procedures and modifications
- 3D-printing/manufacturing settings
- Modified/custom STL files
- Ready-to-fly weight and battery configuration
- Flight-test objectives and observations
- Flight videos
- ArduPilot BIN logs
- Engineering analysis
- Configuration changes
- Known issues
- Lessons learned and build-specific gotchas

The intent is **reproducibility, configuration control, and traceability**.

---

# Flightory Stallion

The Stallion family currently contains two separate physical aircraft projects:

```text
Stallion
├── References
├── V1
│   └── Build 01
└── V2
    └── Build 01
```

## Stallion References

Family-level documentation is maintained under:

```text
aircraft/flightory/stallion/references/
```

This area contains:

- Official Flightory Stallion documentation
- Official Stallion VTOL documentation
- Matek F765-Wing references
- Builder Notes — Lessons Learned & Gotchas

Family-level references are intentionally separate from configuration records belonging to a specific physical aircraft.

Where a lesson applies only to one version/build, it should be explicitly identified as such.

---

## Stallion VTOL V1 — Build 01

V1 Build 01 is an existing aircraft undergoing VTOL flight development and testing.

The V1 record includes aircraft configuration, ArduPilot information, flight testing, engineering analysis, media, and downloadable configuration artifacts.

Detailed original manufacturing information was not captured during construction, so V1 Build 01 intentionally does **not** contain a 3D Printing & Manufacturing section.

Current hover/test configuration documented by the project:

- Ready-to-fly AUW: **2150 g**
- Hover/test battery: **4S 4200 mAh LiPo**
- Flight controller: **Matek F765-Wing**
- Firmware: **ArduPlane 4.6.3**

A separate 4S4P 14,000 mAh Li-ion battery is available as an endurance option but is not the current hover-test configuration.

---

## Stallion VTOL V2 — Build 01

V2 Build 01 is the newer Stallion build and contains substantially more detailed manufacturing and construction records.

Current implemented sections include:

- **3D Printing & Manufacturing**
- **Components**
- **Assembly & Wiring**
- **Downloads**
- **Builder Notes / reference material**

Additional sections will be populated as the build progresses.

### 3D Printing & Manufacturing

The detailed manufacturing report is located at:

```text
aircraft/flightory/stallion/v2/build-01/printing/
```

The report preserves part-level information such as:

- Printer
- Material
- Slicer
- Key slicer settings
- Print time
- Filament usage
- Part weight
- Status
- Reprints
- Build-specific findings

Current slicer baseline includes **OrcaSlicer v2.4.2**.

### Key V2 Manufacturing Findings

#### Thin-Wall Parts

The following parts can be sliced successfully in OrcaSlicer and do not require Cura:

- BOOM TAIL INSERT
- BOOM FUS INSERT
- BOOM FUS MOUNT

Required configuration:

- **Detect Thin Walls:** Enabled
- **Wall Generator:** Arachne

This supersedes the earlier interim finding that Cura was required for these parts.

#### X-Y Hole Compensation

For Stallion VTOL V2 Build 01, verify:

```text
X-Y Hole Compensation: 0.30 mm
```

This setting is part of the V2 Build 01 manufacturing baseline and should be checked when preparing applicable parts with holes or fitted hardware.

### Modified V-Tail Parts

Both VTail 1 components required modification during V2 Build 01 manufacturing:

- **V TAIL 1 L (modified)**
- **V TAIL 1 R (modified)**

The exact modified STL files are preserved under:

```text
aircraft/flightory/stallion/v2/build-01/downloads/
```

The corresponding part names in the 3D Printing & Manufacturing report link directly to these files.

The modified geometry is retained as a **build-specific configuration-controlled artifact** rather than replacing the original Flightory design reference.

### Components

V2 Build 01 component documentation is maintained under:

```text
aircraft/flightory/stallion/v2/build-01/components/
```

Current recorded hardware includes:

- **Torsion Springs — 4.5 mm, 120 Degree**

Component entries may include manufacturer documentation or product/source references where appropriate.

### Assembly & Wiring

V2 Build 01 assembly notes are maintained under:

```text
aircraft/flightory/stallion/v2/build-01/assembly-wiring/
```

A current build-specific wiring procedure is the V-tail servo extension:

- Cut the V-tail servo leads immediately behind the factory connector pins.
- Extend each lead by **400 mm** using matching servo wire.
- Maintain signal, positive-power, and ground conductor order/polarity.
- Insulate and strain-relieve the splices.
- Route the extended wiring through the carbon-fiber structure to the flight controller.

The 400 mm extension provides sufficient routing length without placing the servo wiring under unnecessary tension.

### Downloads

V2 Build 01 downloadable artifacts are stored under:

```text
aircraft/flightory/stallion/v2/build-01/downloads/
```

This area may contain:

- Modified/custom STL files
- PARAM/configuration files
- Engineering reports
- Other build-specific downloadable artifacts

Downloads should remain associated with the physical build to which they apply.

---

# Configuration Control Philosophy

Documentation should describe the aircraft **as it actually existed**, not simply the intended design.

When hardware, firmware, wiring, parameters, battery configuration, manufacturing geometry, or other significant items change, the engineering record should be updated accordingly.

Build-specific changes should not silently overwrite manufacturer references or records from another aircraft version.

Examples:

- A modified V2 STL belongs to the V2 Build 01 record.
- A V1 PARAM file belongs to V1 Build 01.
- A family-level Flightory manual belongs in Stallion References.
- A test-flight BIN should remain associated with the aircraft configuration that produced it.

---

# PARAM and Flight-Test Records

Meaningful ArduPilot configuration milestones should be preserved as named PARAM snapshots.

Examples include:

- Initial configuration
- Motor/servo verification
- First hover
- Roll/pitch tuning
- Yaw tuning
- First stable hover
- QLOITER preparation
- First successful QLOITER
- Pre-transition configuration
- Post-transition tuning

Meaningful flight tests should preserve the corresponding BIN log whenever possible.

BIN logs support quantitative evaluation of:

- PID tracking
- EKF behavior
- Yaw performance
- Motor saturation
- Magnetic interference
- RC input
- GPS behavior
- Battery behavior
- Flight-mode changes
- System messages

Video documents what the aircraft appeared to do; telemetry and BIN data help establish why it did it.

---

# Website

The repository is published as a static GitHub Pages project site.

Design goals include:

- Dark engineering-oriented theme
- Responsive layout
- Card-based navigation
- Clickable breadcrumb navigation
- Relative internal links wherever practical
- No server-side dependencies
- No unnecessary web frameworks

The repository remains a GitHub Pages **project site**:

```text
https://teamcorc.github.io/RC-Aircraft-Builds/
```

The repository should remain:

```text
teamcorc/RC-Aircraft-Builds
```

It should **not** be renamed to `teamcorc.github.io`.

---

# Documentation Standards

When adding or updating project records:

1. Preserve existing working content unless it is intentionally being revised.
2. Do not invent configuration, wiring, hardware, or test details.
3. Prefer official manufacturer documentation where available.
4. Keep different aircraft versions and physical builds isolated.
5. Preserve exact filenames for configuration-controlled artifacts.
6. Use relative internal links where practical.
7. Record actual test configuration, including AUW and battery when relevant.
8. Preserve meaningful PARAM and BIN records.
9. Treat modified files as build-specific artifacts unless their applicability has been independently established more broadly.
10. Add lessons learned and gotchas as they are discovered.

---

## Project Goal

The long-term goal of **RC Aircraft Builds** is to create a durable engineering archive that allows a future reader—or the builder months or years later—to determine:

- What was built
- Which hardware was installed
- How it was configured
- How it was manufactured
- What was changed
- What was tested
- What worked
- What did not work
- Why later decisions were made

That record is intended to remain useful long after an individual build or flight-test session is complete.
