---
title: "Radeon driver: Can't run without &quot;nomodeset&quot;: MacPro6,1; two AMD R9 280X Tahiti cards"
date: 2016-10-29
forum: Apple Hardware Users
---

### Post by heigh on 2016-10-29
Hello, Ubuntu Gurus,

I have a rare configuration of 2016 MacPro6,1 with two
AMD Radeon R9 280X Tahiti video cards, and three 4-K monitors
connected via DisplayPort / Thunderbolt ports.

The system installs successfully, but both LiveCD (for installation) and installed system
require "nomodeset" option, otherwise boot process hangs with a black screen.

With "nomodeset" system detects and works only on one monitor, connected
via HDMI. All monitors connected via DisplayPorts remain blank.

I tried different versions of Ubuntu (14.04.4, 14.04.5, 15.10, 16.04, 16.04.1, 16.10),
all have this problem, and also several versions of Linux Mint, with same result.
I also tried newer upstream kernels (4.6, 4.7.3, 4.8) on Ubuntu 16.04.1,
all with the same result.

But I found one distro of Linux, called KaOS ([https://kaosx.us/](https://kaosx.us/)) that works OK on my
hardware. Soon after butting, it successfully detects and turns On all three monitors
connected via Display Ports, and then presents normal wide KDE desktop on all three monitors.

I compared journal entries from Ubuntu and KaOS boots, and it seems that
KaOS successfully detects and activates both AMD cards, and then continues to boot normally.
It uses open source "radeon" driver.

Ubuntu, on the other hand (all versions and kernels listed above), with the same "radeon" driver 
detects only the first card, and fails on the second card, which causes immediate shutdown of "radeon" driver,
and boot process hangs after that.

Here's the relevant messages from the journals. Full journal logs are
available in the Google Drive: [https://drive.google.com/open?id=0B-XqvPBgTkOSN1p2eVcwNkpmbWs](https://drive.google.com/open?id=0B-XqvPBgTkOSN1p2eVcwNkpmbWs)

KaOS:
=====

First card:
-------------
```
[drm] radeon kernel modesetting enabled.
[drm] initializing kernel modesetting (TAHITI 0x1002:0x6798 0x106B:0x0128 0x00).
[drm] register mmio base: 0xA0700000
[drm] register mmio size: 262144
[drm] ACPI VFCT contains a BIOS for 02:00.0 1002:6798, size 65536
[drm:radeon_get_bios] ATOMBIOS detected
ATOM BIOS: Tahiti
[drm] Loading tahiti Microcode
[drm] Initialized radeon 2.45.0 20080528 for 0000:02:00.0 on minor 0
fb: switching to radeondrmfb from EFI VGA
.....
```

Second card:
----------------
```
[drm] ACPI VFCT contains a BIOS for 02:00.0 1002:6798, size 65536
[drm] ACPI VFCT table is not for this card
radeon 0000:06:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
radeon 0000:06:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
[drm:radeon_get_bios] ATOMBIOS detected
ATOM BIOS: Tahiti
[drm] Loading tahiti Microcode
[drm] radeon: dpm initialized
[drm] Initialized radeon 2.45.0 20080528 for 0000:06:00.0 on minor 1
```


(Notice these "Invalid PCI ROM header signature" errors,
but the card initialized successfully despite them,
and KaOS developers confirmed, that these errors are normal for ATI cards,
and are harmless)


Ubuntu:
=======

First card:
-------------
```
[drm] radeon kernel modesetting enabled.
[drm] initializing kernel modesetting (TAHITI 0x1002:0x6798 0x106B:0x0128).
[drm] register mmio base: 0xA0700000
[drm] register mmio size: 262144
[drm] ACPI VFCT contains a BIOS for 02:00.0 1002:6798, size 65536
[drm:radeon_get_bios] ATOMBIOS detected
ATOM BIOS: Tahiti
[drm] Loading tahiti Microcode
[drm] radeon: dpm initialized
[drm] Initialized radeon 2.43.0 20080528 for 0000:02:00.0 on minor 0
fb: switching to radeondrmfb from EFI VGA
```

Second card:
-----------------
```
[drm] initializing kernel modesetting (TAHITI 0x1002:0x6798 0x106B:0x0127).
[drm] register mmio base: 0xA0600000
[drm] register mmio size: 262144
[drm] ACPI VFCT contains a BIOS for 02:00.0 1002:6798, size 65536
[drm] ACPI VFCT table is not for this card
radeon 0000:06:00.0: Invalid ROM contents
radeon 0000:06:00.0: Invalid ROM contents
[drm:radeon_get_bios [radeon]] *ERROR* Unable to locate a BIOS ROM
radeon 0000:06:00.0: Fatal error during GPU init
[drm] radeon: finishing device.
radeon: probe of 0000:06:00.0 failed with error -22
```

Notice same errors "Invalid ROM contents" (slightly different wording,
but I have checked in sources that they mean the same - unexpected ROM signature)
After these errors radeon/drm driver fails with *ERROR* Unable to locate a BIOS ROM,
and then "finishing device."

KaOS uses newer kernel 4.7.3-1, but I tried 4.6, 4.7.3, 4.8 on Ubuntu, without success.

Another thing I noticed from journals: on KaOS udev rules are loaded before kernel modesetting,
but on Ubuntu - after modesetting. Can this be a reason?


Graphics cards info:
---------------------------
```

lspci | grep VGA
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
```

Full "lspci -vvv" and "lshw" outputs are also included in the archive on Google Drive:
[https://drive.google.com/open?id=0B-XqvPBgTkOSN1p2eVcwNkpmbWs](https://drive.google.com/open?id=0B-XqvPBgTkOSN1p2eVcwNkpmbWs)

I really need to make this workstation work under Linux, don't want
to settle for MacOS.

If somebody competent could have a look at this and give some suggestions,
I'd appreciate it a lot.

Thanks,
Heigh

For convenience, journals_and_hardware_info.zip as an attachment

[ATTACH]271852[/ATTACH]

Thanks.

---

### Post by howefield on 2016-10-30
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by heigh on 2016-11-08
I have found a workaround or solution.

The system needs to be booted with systemd-boot bootloader (or perhaps any other supporting UEFI boot)

  When I boot Ubuntu on my MacPro with standard, installed during  installation grub2, radeon driver would't detect external displays  connected via Display Ports.

  But when I boot system using systemd-boot installed by Arch Linux (or KaOS), it detects displays normally, and works correctly, supporting all external displays as expected.

  I think this is related to some aspects of the hardware not being exposed in BIOS boot mode, and exposed in EFI/UEFI boot mode.

  Preferred solution would be working radeon driver in BIOS mode if possible, or, if that is not possible, some meaningful message  in the system journal explaining that certain features  (e.g. external monitors via Display Port) will not be supported  unless the system is booted in EFI/UEFI mode.

  I submitted a bug into radeon bugzilla: [URL="https://bugs.freedesktop.org/show_bug.cgi?id=98523"]https://bugs.freedesktop.org/show_bug.cgi?id=98523

[/URL]Hopefully, this will be fixed to work out of the box at some point.

  Thank you, Heigh

---

