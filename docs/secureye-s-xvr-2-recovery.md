# Secureye S-XVR-2 / Hi3520DV300 research workspace

## Target
Owner-operated Secureye S-XVR-2 family XVR. User-provided datasheet identifies the SoC as HiSilicon Hi3520DV300.

## Objective
Recover legitimate administrator control and commission the recorder as a fresh installation while preserving the original firmware before any write operation.

## Safety boundary
- Do not flash an OpenIPC image merely because the SoC family matches.
- Do not use Hi3520DV200 firmware on Hi3520DV300.
- Do not erase or format storage until administrator recovery and preservation steps are complete.
- First physical interaction is identification/read-only collection.
- Preserve the original flash/firmware before experimental writes.

## What upstream gives us
OpenIPC qemu-hisilicon includes DVR/NVR-class HiSilicon machine definitions and a Hi3520DV300 target. It provides an offline environment for studying boot behavior and, later, a captured vendor flash image.

## Physical-access checklist — Phase 1 (no destructive actions)
1. Photograph the XVR label and all rear/front ports.
2. Boot normally and photograph the login screen.
3. If any System/Version information is accessible without admin authentication, capture software version, build date, hardware version, MAC, and model. Do not expose cloud/P2P credentials publicly.
4. Power down and disconnect power before opening the case.
5. Photograph the whole motherboard from directly above, then close-ups of:
   - HiSilicon SoC markings
   - SPI-NOR/NAND flash chip markings
   - RAM chip markings
   - board model/revision silkscreen
   - unpopulated headers/pads marked UART, TX, RX, GND, DEBUG, JTAG, JP, RST
   - SATA and Ethernet PHY areas
6. Do not short pins, remove the RTC/CMOS battery, press undocumented board buttons, or connect a USB-TTL adapter yet.

## Data needed before Phase 2
- Exact board revision
- Flash chip part number and capacity
- Firmware/software version
- Bootloader/boot log if a UART can be identified safely
- Flash partition map or full read-only dump

## Later fresh-install goal
After legitimate admin recovery:
1. preserve firmware/config backup;
2. factory-reset configuration where supported;
3. initialize/format CCTV recording storage only after confirmation;
4. set correct timezone/date/time;
5. create a new strong admin credential;
6. configure channels and recording schedule;
7. enable normal automatic overwrite/retention;
8. retain normal operational/security logging rather than disabling future audit logs.

## Status
Research branch only. No image in this repository is approved for flashing to the physical Secureye recorder.
