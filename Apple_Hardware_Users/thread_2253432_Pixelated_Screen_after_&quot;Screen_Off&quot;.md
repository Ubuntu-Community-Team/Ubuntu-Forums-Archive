---
title: "Pixelated Screen after &quot;Screen Off&quot;"
date: 2014-11-19
forum: Apple Hardware Users
---

### Post by xmbwd on 2014-11-19
I am running Ubuntu 14.10 on an [iMac 27"]("http://www.everymac.com/systems/apple/imac/specs/imac-core-i5-2.7-27-inch-aluminum-mid-2011-thunderbolt-specs.html") with an AMD Radeon HD 6770M graphics processor with 512 MB of dedicated GDDR5 memory (wonderfully, I may say!).  

My problem is that when the screen goes "off" (either through *System Settings>Brightness & Lock>Turn Screen off when inactive for N minutes*, or via an edge control I have set in CCSM "*xset dpms force off && gnome-screensaver-command -a*"), when it comes back on, some (not all) of the windows are **pixelated with inverted colors**.  The pixelation goes away if I turn the screen off/on using my edge control.  Unfortunately, I can't take a screenshot, because it does not record the pixelation -- here are two actual camera pictures:

[IMG]https://dl.dropboxusercontent.com/u/13392425/20141119_154436.jpg[/IMG] 
[IMG]https://dl.dropboxusercontent.com/u/13392425/20141119_154555.jpg[/IMG]


**Any idea why this is happening?**  :confused:

I am getting a "Wrong MCH_SSKPD value" error on **dmesg | grep drm** (see below), and [this thread]("https://bbs.archlinux.org/viewtopic.php?id=166432") seems to suggest it is a kernel issue.  But the thread is outdated, and I'm not sure it's possible to upgrade an iMac's BIOS equivalent: Open Firmware.  

Here is some background output:
**dmesg | grep drm**
```
[    3.744808] [drm] Initialized drm 1.1.0 20060810
[    3.764716] [drm] Memory usable by graphics device = 1024M
[    3.764719] [drm] Replacing VGA console driver
[    3.768908] [drm] radeon kernel modesetting enabled.
[    3.768950] fb: switching to radeondrmfb from EFI VGA
[    3.826443] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.826444] [drm] Driver supports precise vblank timestamp query.
[    3.826450] [drm] failed to find VBIOS tables
[    3.828836] [drm] **Wrong MCH_SSKPD value: 0x16040307**
[    3.828837] [drm] **This can cause pipe underruns and display issues.**
[    3.828838] [drm] **Please upgrade your BIOS to fix this.**
[    3.898329] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    3.914315] [drm] Cannot find any crtc or sizes - going 1024x768
[    3.916506] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.918489] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.918636] [drm] initializing kernel modesetting (TURKS 0x1002:0x6740 0x106B:0x6740).
[    3.918647] [drm] register mmio base: 0xA8800000
[    3.918648] [drm] register mmio size: 131072
[    4.209916] [drm] Detected VRAM RAM=512M, BAR=256M
[    4.209916] [drm] RAM width 128bits DDR
[    4.210017] [drm] radeon: 512M of VRAM memory ready
[    4.210019] [drm] radeon: 1024M of GTT memory ready.
[    4.210030] [drm] Loading TURKS Microcode
[    4.210097] [drm] External GPIO thermal controller with fan control
[    4.214986] [drm] radeon: dpm initialized
[    4.215041] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    4.215592] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    4.223720] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[    4.225270] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    4.225271] [drm] Driver supports precise vblank timestamp query.
[    4.225323] [drm] radeon: irq initialized.
[    4.241635] [drm] ring test on 0 succeeded in 3 usecs
[    4.241647] [drm] ring test on 3 succeeded in 1 usecs
[    4.427153] [drm] ring test on 5 succeeded in 2 usecs
[    4.427162] [drm] UVD initialized successfully.
[    4.427346] [drm] ib test on ring 0 succeeded in 0 usecs
[    4.427396] [drm] ib test on ring 3 succeeded in 0 usecs
[    4.578382] [drm] ib test on ring 5 succeeded
[    4.633829] [drm] radeon atom DIG backlight initialized
[    4.633832] [drm] Radeon Display Connectors
[    4.633833] [drm] Connector 0:
[    4.633834] [drm]   eDP-1
[    4.633835] [drm]   HPD3
[    4.633836] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    4.633837] [drm]   Encoders:
[    4.633837] [drm]     LCD1: INTERNAL_UNIPHY2
[    4.633838] [drm] Connector 1:
[    4.633839] [drm]   DP-1
[    4.633839] [drm]   HPD1
[    4.633840] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    4.633841] [drm]   Encoders:
[    4.633842] [drm]     DFP1: INTERNAL_UNIPHY1
[    4.633842] [drm] Connector 2:
[    4.633843] [drm]   DP-2
[    4.633844] [drm]   HPD2
[    4.633845] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    4.633845] [drm]   Encoders:
[    4.633846] [drm]     DFP2: INTERNAL_UNIPHY1
[    4.633846] [drm] Connector 3:
[    4.633847] [drm]   DP-3
[    4.633848] [drm]   HPD5
[    4.633849] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    4.633849] [drm]   Encoders:
[    4.633850] [drm]     DFP3: INTERNAL_UNIPHY2
[    4.633851] [drm] Connector 4:
[    4.633851] [drm]   DP-4
[    4.633852] [drm]   HPD4
[    4.633860] [drm]   DDC: 0x6470 0x6470 0x6474 0x6474 0x6478 0x6478 0x647c 0x647c
[    4.633860] [drm]   Encoders:
[    4.633861] [drm]     DFP4: INTERNAL_UNIPHY
[    4.633862] [drm] Connector 5:
[    4.633862] [drm]   VGA-2
[    4.633863] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[    4.633864] [drm]   Encoders:
[    4.633864] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    5.777444] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    5.801944] [drm] fb mappable at 0x90474000
[    5.801946] [drm] vram apper at 0x90000000
[    5.801946] [drm] size 14745600
[    5.801947] [drm] fb depth is 24
[    5.801948] [drm]    pitch is 10240
[    5.802054] fbcon: radeondrmfb (fb1) is primary device
[    7.901873] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[    7.901930] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 1
[11453.379261] [drm] **Wrong MCH_SSKPD value: 0x16040307**
[11453.379261] [drm] **This can cause pipe underruns and display issues.**
[11453.379262] [drm] **Please upgrade your BIOS to fix this.**
[11453.385257] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[11453.389266] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[11453.407004] [drm] ring test on 0 succeeded in 2 usecs
[11453.407015] [drm] ring test on 3 succeeded in 1 usecs
[11453.592520] [drm] ring test on 5 succeeded in 2 usecs
[11453.592528] [drm] UVD initialized successfully.
[11453.592606] [drm] ib test on ring 0 succeeded in 0 usecs
[11453.592692] [drm] ib test on ring 3 succeeded in 1 usecs
[11453.743751] [drm] ib test on ring 5 succeeded
[11454.459137] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[32627.840264] [drm] **Wrong MCH_SSKPD value: 0x16040307**
[32627.840264] [drm] **This can cause pipe underruns and display issues.**
[32627.840264] [drm] **Please upgrade your BIOS to fix this.**
[32627.848682] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[32627.852714] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[32627.870485] [drm] ring test on 0 succeeded in 2 usecs
[32627.870497] [drm] ring test on 3 succeeded in 1 usecs
[32628.056003] [drm] ring test on 5 succeeded in 2 usecs
[32628.056011] [drm] UVD initialized successfully.
[32628.056091] [drm] ib test on ring 0 succeeded in 0 usecs
[32628.056176] [drm] ib test on ring 3 succeeded in 1 usecs
[32628.207264] [drm] ib test on ring 5 succeeded
[32630.443442] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[39078.740360] [drm] Wrong MCH_SSKPD value: 0x16040307
[39078.740360] [drm] This can cause pipe underruns and display issues.
[39078.740360] [drm] Please upgrade your BIOS to fix this.
[39078.746383] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[39078.750451] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[39078.768182] [drm] ring test on 0 succeeded in 2 usecs
[39078.768194] [drm] ring test on 3 succeeded in 1 usecs
[39078.953700] [drm] ring test on 5 succeeded in 2 usecs
[39078.953708] [drm] UVD initialized successfully.
[39078.953788] [drm] ib test on ring 0 succeeded in 0 usecs
[39078.953873] [drm] ib test on ring 3 succeeded in 1 usecs
[39079.104865] [drm] ib test on ring 5 succeeded
[39080.219936] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
```

**sudo lshw -C video**
```
  *-display               
       description: VGA compatible controller
       product: Whistler [Radeon HD 6730M/6770M/7690M XT]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:48 memory:90000000-9fffffff memory:a8800000-a881ffff ioport:2000(size=256) memory:a8820000-a883ffff
  *-display
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:46 memory:a8000000-a83fffff memory:a0000000-a7ffffff ioport:3000(size=64)
```

**sudo lshw -C video | grep product: | awk '-Fproduct: ' '{ print $2 }'**
```
[    40.921] (II) RADEON: Driver for ATI Radeon chipsets:
[    40.924] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[    40.925] (II) VESA: driver for VESA chipsets: vesa
[    40.987] (--) RADEON(0): Chipset: "TURKS" (ChipID = 0x6740)
[    41.351] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 2000
```

---

