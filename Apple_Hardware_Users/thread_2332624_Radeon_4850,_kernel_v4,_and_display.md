---
title: "Radeon 4850, kernel v4, and display"
date: 2016-08-02
forum: Apple Hardware Users
---

### Post by DigiAngel on 2016-08-02
So I know this is a kernel issue already.  Kernel v3, no problems, but kernel v4 is when the issue started.  The tl'dr is:  How can I choose the display port on boot?  More info:

```
[   10.996745] radeon 0000:02:00.0: firmware: direct-loading firmware radeon/RV770_uvd.bin
[   10.996795] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   10.997981] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   11.001968] [drm] PCIE GART of 1024M enabled (table at 0x0000000000258000).
[   11.002004] radeon 0000:02:00.0: WB enabled
[   11.002009] radeon 0000:02:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff8802355a2c00
[   11.002015] radeon 0000:02:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff8802355a2c0c
[   11.002498] radeon 0000:02:00.0: fence driver on ring 5 use gpu addr 0x0000000000056230 and cpu addr 0xffffc90001016230
[   11.002505] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   11.002508] [drm] Driver supports precise vblank timestamp query.
[   11.002512] radeon 0000:02:00.0: radeon: MSI limited to 32-bit
[   11.002543] radeon 0000:02:00.0: radeon: using MSI.
[   11.002570] [drm] radeon: irq initialized.
[   11.048841] [drm] ring test on 0 succeeded in 1 usecs
[   11.048850] [drm] ring test on 3 succeeded in 2 usecs
[   11.099988] Adding 7812092k swap on /dev/sda3.  Priority:-1 extents:1 across:7812092k FS
[   11.223502] [drm] ring test on 5 succeeded in 1 usecs
[   11.223513] [drm] UVD initialized successfully.
[   11.223859] [drm] ib test on ring 0 succeeded in 0 usecs
[   11.223877] [drm] ib test on ring 3 succeeded in 0 usecs
[   11.430422] FAT-fs (sda1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   11.872125] [drm] ib test on ring 5 succeeded
[   11.872601] [drm] radeon atom DIG backlight initialized
[   11.872605] [drm] Radeon Display Connectors
[   11.872608] [drm] Connector 0:
[   11.872611] [drm]   DP-1
[   11.872614] [drm]   HPD2
[   11.872617] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[   11.872622] [drm]   Encoders:
[   11.872625] [drm]     DFP1: INTERNAL_UNIPHY
[   11.872628] [drm] Connector 1:
[   11.872631] [drm]   DP-2
[   11.872633] [drm]   HPD3
[   11.872636] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[   11.872641] [drm]   Encoders:
[   11.872644] [drm]     DFP2: INTERNAL_UNIPHY
[   11.872647] [drm] Connector 2:
[   11.872649] [drm]   LVDS-1
[   11.872652] [drm]   Encoders:
[   11.872655] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[   11.872658] [drm] Connector 3:
[   11.872661] [drm]   VGA-1
[   11.872664] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   11.872669] [drm]   Encoders:
[   11.872671] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   12.260545] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/sound/card0/input9
[   12.261317] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
[   12.261675] input: HDA NVidia Line as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
[   12.261911] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input12
[   12.561492] [drm] fb mappable at 0xC0459000
[   12.561499] [drm] vram apper at 0xC0000000
[   12.561502] [drm] size 5947392
[   12.561505] [drm] fb depth is 24
[   12.561508] [drm]    pitch is 5632
[   12.561595] fbcon: radeondrmfb (fb0) is primary device
[   12.640199] Console: switching to colour frame buffer device 175x65
[   12.643081] radeon 0000:02:00.0: fb0: radeondrmfb frame buffer device
[   12.660064] [drm] Initialized radeon 2.43.0 20080528 for 0000:02:00.0 on minor 0


02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770/M98L [Mobility Radeon HD 4850]

GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=1"

```

The modeset line gets me what I need..which is to poweroff the screen after a timeout.  The issue is that with that modeset the wrong display port is used...one that doesn't have a monitor attached so the main screen is completely blank.  With no modeset specified I get a normal screen, but no dpms.  I've looked high and low, but I've not found any kernel options to boot to change the display port.  It's not running X windows.  Thank you.

---

### Post by DigiAngel on 2016-08-03
Admins, might as well move this to Apple Hardware as well.

---

### Post by QDR06VV9 on 2016-08-03
Moved  @ OP's Request

---

