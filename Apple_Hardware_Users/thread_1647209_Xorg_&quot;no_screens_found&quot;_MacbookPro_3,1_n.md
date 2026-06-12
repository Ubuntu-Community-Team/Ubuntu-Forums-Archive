---
title: "Xorg &quot;no screens found&quot; MacbookPro 3,1 nVidia 8600M GT"
date: 2010-12-17
forum: Apple Hardware Users
---

### Post by a.ross.cohen on 2010-12-17
Hello, this is my first post on this forum. I hope I'm not double posting something but I checked pretty well and couldn't find a solution.

I recently installed ubuntu 10.10 x86_64 on my Macbook Pro 3,1 which has an nVidia 8600M GT video card. The native screen resolution for my system is 1440x900.

Ubuntu is installed booting through Grub2 straight from my EFI firmware through rEFIt. I have to disable quiet boot and splash screen but I can boot into a shell.

From there I obviously tried startX, but much to my chagrin it did not start. I screwed around with drivers and the like for a bit and ended up reinstalling completely to try and rule things out one by one.

I started by blacklisting nouveau, which didn't load nouveau but also didn't work. I then tried installing the newest nVidia drivers, which also didn't work.

Everything I tried gave me the same error, "no screens found".

I below is the most resent Xorg.0.log dump with the attempt at running with the nVidia driver.

```

[  3242.793] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  3242.829] X Protocol Version 11, Revision 0
[  3242.841] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[  3242.853] Current Operating System: Linux MacBuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[  3242.867] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=cba2822c-7f25-48a4-a629-80bcda8f0cb7 video=efifb nomodeset
[  3242.881] Build Date: 16 September 2010  06:18:41PM
[  3242.895] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  3242.910] Current version of pixman: 0.18.4
[  3242.926] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  3242.957] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3243.008] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 15 06:14:16 2010
[  3243.025] (==) Using config file: "/etc/X11/xorg.conf"
[  3243.043] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3243.061] (==) ServerLayout "Layout0"
[  3243.061] (**) |-->Screen "Screen0" (0)
[  3243.061] (**) |   |-->Monitor "Monitor0"
[  3243.061] (**) |   |-->Device "Device0"
[  3243.061] (**) |-->Input Device "Keyboard0"
[  3243.061] (**) |-->Input Device "Mouse0"
[  3243.061] (==) Automatically adding devices
[  3243.061] (==) Automatically enabling devices
[  3243.061] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3243.061] 	Entry deleted from font path.
[  3243.061] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  3243.061] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3243.061] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  3243.061] (WW) Disabling Keyboard0
[  3243.061] (WW) Disabling Mouse0
[  3243.061] (II) Loader magic: 0x7d0200
[  3243.061] (II) Module ABI versions:
[  3243.061] 	X.Org ANSI C Emulation: 0.4
[  3243.061] 	X.Org Video Driver: 8.0
[  3243.061] 	X.Org XInput driver : 11.0
[  3243.061] 	X.Org Server Extension : 4.0
[  3243.062] (--) PCI:*(0:1:0:0) 10de:0407:106b:00a0 rev 161, Mem @ 0x92000000/16777216, 0x80000000/268435456, 0x90000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/131072
[  3243.062] (II) Open ACPI successful (/var/run/acpid.socket)
[  3243.062] (II) LoadModule: "extmod"
[  3243.062] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  3243.063] (II) Module extmod: vendor="X.Org Foundation"
[  3243.063] 	compiled for 1.9.0, module version = 1.0.0
[  3243.063] 	Module class: X.Org Server Extension
[  3243.063] 	ABI class: X.Org Server Extension, version 4.0
[  3243.063] (II) Loading extension MIT-SCREEN-SAVER
[  3243.063] (II) Loading extension XFree86-VidModeExtension
[  3243.063] (II) Loading extension XFree86-DGA
[  3243.063] (II) Loading extension DPMS
[  3243.063] (II) Loading extension XVideo
[  3243.063] (II) Loading extension XVideo-MotionCompensation
[  3243.063] (II) Loading extension X-Resource
[  3243.063] (II) LoadModule: "dbe"
[  3243.063] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  3243.063] (II) Module dbe: vendor="X.Org Foundation"
[  3243.063] 	compiled for 1.9.0, module version = 1.0.0
[  3243.063] 	Module class: X.Org Server Extension
[  3243.063] 	ABI class: X.Org Server Extension, version 4.0
[  3243.063] (II) Loading extension DOUBLE-BUFFER
[  3243.063] (II) LoadModule: "glx"
[  3243.063] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3243.073] (II) Module glx: vendor="NVIDIA Corporation"
[  3243.073] 	compiled for 4.0.2, module version = 1.0.0
[  3243.073] 	Module class: X.Org Server Extension
[  3243.073] (II) NVIDIA GLX Module  260.19.29  Wed Dec  8 12:24:30 PST 2010
[  3243.073] (II) Loading extension GLX
[  3243.073] (II) LoadModule: "record"
[  3243.073] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  3243.073] (II) Module record: vendor="X.Org Foundation"
[  3243.073] 	compiled for 1.9.0, module version = 1.13.0
[  3243.073] 	Module class: X.Org Server Extension
[  3243.074] 	ABI class: X.Org Server Extension, version 4.0
[  3243.074] (II) Loading extension RECORD
[  3243.074] (II) LoadModule: "dri"
[  3243.074] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  3243.074] (II) Module dri: vendor="X.Org Foundation"
[  3243.074] 	compiled for 1.9.0, module version = 1.0.0
[  3243.074] 	ABI class: X.Org Server Extension, version 4.0
[  3243.074] (II) Loading extension XFree86-DRI
[  3243.074] (II) LoadModule: "dri2"
[  3243.074] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  3243.074] (II) Module dri2: vendor="X.Org Foundation"
[  3243.074] 	compiled for 1.9.0, module version = 1.2.0
[  3243.074] 	ABI class: X.Org Server Extension, version 4.0
[  3243.074] (II) Loading extension DRI2
[  3243.074] (II) LoadModule: "nvidia"
[  3243.074] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  3243.075] (II) Module nvidia: vendor="NVIDIA Corporation"
[  3243.075] 	compiled for 4.0.2, module version = 1.0.0
[  3243.075] 	Module class: X.Org Video Driver
[  3243.075] (II) NVIDIA dlloader X Driver  260.19.29  Wed Dec  8 12:10:14 PST 2010
[  3243.075] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  3243.075] (--) using VT number 8

[  3243.154] (II) Loading sub module "fb"
[  3243.154] (II) LoadModule: "fb"
[  3243.154] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3243.154] (II) Module fb: vendor="X.Org Foundation"
[  3243.154] 	compiled for 1.9.0, module version = 1.0.0
[  3243.154] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3243.154] (II) Loading sub module "wfb"
[  3243.154] (II) LoadModule: "wfb"
[  3243.154] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  3243.154] (II) Module wfb: vendor="X.Org Foundation"
[  3243.154] 	compiled for 1.9.0, module version = 1.0.0
[  3243.154] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3243.154] (II) Loading sub module "ramdac"
[  3243.154] (II) LoadModule: "ramdac"
[  3243.155] (II) Module "ramdac" already built-in
[  3243.155] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  3243.155] (==) NVIDIA(0): RGB weight 888
[  3243.155] (==) NVIDIA(0): Default visual is TrueColor
[  3243.155] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  3243.155] (**) NVIDIA(0): Enabling RENDER acceleration
[  3243.155] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  3243.155] (II) NVIDIA(0):     enabled.
[  3243.166] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[  3243.166] (EE) NVIDIA(0):     check your system's kernel log for additional error
[  3243.166] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[  3243.166] (EE) NVIDIA(0):     README for additional information.
[  3243.166] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[  3243.166] (II) UnloadModule: "nvidia"
[  3243.166] (II) UnloadModule: "wfb"
[  3243.166] (II) UnloadModule: "fb"
[  3243.166] (EE) Screen(s) found, but none have a usable configuration.
[  3243.166] 
Fatal server error:
[  3243.166] no screens found
[  3243.166] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  3243.166] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3243.166] 
[  3243.393]  ddxSigGiveUp: Closing log

```

I am a computer science student so I am not completely inept, however I just cannot seem to figure out whats wrong with this thing.
Any help is much appreciated in advance.

--> I tacked on my xorg.conf file just in case.

---

### Post by metatechbe on 2010-12-17
Hello,

Please attach your /var/log/kern.log, normally the "real" error message is there.
Thanks.

metatech

---

### Post by yugnip on 2010-12-18
Hi. I can't believe we have the same machine after glancing at your xorg. Check mine out (attached). Try it out and see.

---

### Post by a.ross.cohen on 2010-12-21
Here is my kern.log. Sorry it took me so long to get it up here but I've been moving.
By the way I tried that other xorg.conf configuration and it didn't fix the problem.

```

Dec 21 00:38:18 MacBuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=cba2822c-7f25-48a4-a629-80bcda8f0cb7 ro
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000000008f000 - 0000000000090000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 0000000000090000 - 00000000000a0000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 00000000000a0000 - 00000000000c0000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007eef1000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007eef1000 - 000000007f0f2000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007f0f2000 - 000000007fe53000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007fe53000 - 000000007fe79000 (unusable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007fe79000 - 000000007fe89000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007fe89000 - 000000007feb3000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007feb3000 - 000000007feb9000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007feb9000 - 000000007febf000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007febf000 - 000000007fed2000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007fed2000 - 000000007fed4000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007fed4000 - 000000007fed7000 (ACPI data)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007fed7000 - 000000007feda000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007feda000 - 000000007fedb000 (ACPI data)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007fedb000 - 000000007feef000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007feef000 - 000000007feff000 (ACPI data)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 000000007feff000 - 0000000080000000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 00000000f00f8000 - 00000000f00f9000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  BIOS-e820: 00000000fffa0000 - 00000000fffd0000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI v1.10 by Apple
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  ACPI=0x7fefe000  ACPI 2.0=0x7fefe014  SMBIOS=0x7fed3000 
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x000000000008b000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem01: type=2, attr=0xf, range=[0x000000000008b000-0x000000000008f000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem02: type=10, attr=0xf, range=[0x000000000008f000-0x0000000000090000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem03: type=7, attr=0xf, range=[0x0000000000090000-0x00000000000a0000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x0000000000521000) (4MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x0000000000521000-0x000000005cfc7000) (1482MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x000000005cfc7000-0x000000007ce2e000) (510MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x000000007ce2e000-0x000000007ce34000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem08: type=1, attr=0xf, range=[0x000000007ce34000-0x000000007ce53000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem09: type=2, attr=0xf, range=[0x000000007ce53000-0x000000007ceac000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem10: type=7, attr=0xf, range=[0x000000007ceac000-0x000000007cead000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem11: type=2, attr=0xf, range=[0x000000007cead000-0x000000007cec7000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem12: type=7, attr=0xf, range=[0x000000007cec7000-0x000000007cec8000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem13: type=2, attr=0xf, range=[0x000000007cec8000-0x000000007ceee000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem14: type=1, attr=0xf, range=[0x000000007ceee000-0x000000007cf0b000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x000000007cf0b000-0x000000007d178000) (2MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem16: type=2, attr=0xf, range=[0x000000007d178000-0x000000007d17f000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem17: type=7, attr=0xf, range=[0x000000007d17f000-0x000000007d28d000) (1MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem18: type=4, attr=0xf, range=[0x000000007d28d000-0x000000007ea41000) (23MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem19: type=7, attr=0xf, range=[0x000000007ea41000-0x000000007ea50000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem20: type=4, attr=0xf, range=[0x000000007ea50000-0x000000007ea79000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem21: type=7, attr=0xf, range=[0x000000007ea79000-0x000000007ea7a000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem22: type=4, attr=0xf, range=[0x000000007ea7a000-0x000000007eb0e000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem23: type=7, attr=0xf, range=[0x000000007eb0e000-0x000000007ebf5000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem24: type=4, attr=0xf, range=[0x000000007ebf5000-0x000000007eef1000) (2MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem25: type=10, attr=0xf, range=[0x000000007eef1000-0x000000007f0f2000) (2MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem26: type=4, attr=0xf, range=[0x000000007f0f2000-0x000000007f1cd000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem27: type=7, attr=0xf, range=[0x000000007f1cd000-0x000000007f1ce000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem28: type=4, attr=0xf, range=[0x000000007f1ce000-0x000000007fc73000) (10MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem29: type=7, attr=0xf, range=[0x000000007fc73000-0x000000007fca2000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem30: type=3, attr=0xf, range=[0x000000007fca2000-0x000000007fe3f000) (1MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem31: type=7, attr=0xf, range=[0x000000007fe3f000-0x000000007fe53000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem32: type=5, attr=0x800000000000000f, range=[0x000000007fe53000-0x000000007fe79000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem33: type=7, attr=0xf, range=[0x000000007fe79000-0x000000007fe89000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem34: type=6, attr=0x800000000000000f, range=[0x000000007fe89000-0x000000007feb3000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem35: type=7, attr=0xf, range=[0x000000007feb3000-0x000000007feb9000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem36: type=0, attr=0xf, range=[0x000000007feb9000-0x000000007febf000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem37: type=7, attr=0xf, range=[0x000000007febf000-0x000000007fed2000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem38: type=10, attr=0xf, range=[0x000000007fed2000-0x000000007fed4000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem39: type=9, attr=0xf, range=[0x000000007fed4000-0x000000007fed7000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem40: type=10, attr=0xf, range=[0x000000007fed7000-0x000000007feda000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem41: type=9, attr=0xf, range=[0x000000007feda000-0x000000007fedb000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem42: type=10, attr=0xf, range=[0x000000007fedb000-0x000000007feef000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem43: type=9, attr=0xf, range=[0x000000007feef000-0x000000007feff000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem44: type=6, attr=0x800000000000000f, range=[0x000000007feff000-0x000000007ff00000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem45: type=0, attr=0x8000000000000000, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem46: type=0, attr=0x8000000000000000, range=[0x000000007ff00000-0x0000000080000000) (1MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem47: type=11, attr=0x8000000000000000, range=[0x00000000f00f8000-0x00000000f00f9000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem48: type=11, attr=0x8000000000000000, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] EFI: mem49: type=11, attr=0x8000000000000000, range=[0x00000000fffa0000-0x00000000fffd0000) (0MB)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] DMI 2.4 present.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] No AGP bridge found
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] last_pfn = 0x7fed2 max_arch_pfn = 0x400000000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] MTRR default type: uncachable
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   00000-9FFFF write-back
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   C0000-CFFFF write-protect
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   D0000-DFFFF uncachable
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   E0000-FFFFF write-protect
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] MTRR variable ranges enabled:
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   2 base 07FF00000 mask FFFF00000 uncachable
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   3 disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   4 disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   5 disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   6 disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   7 disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] modified physical RAM map:
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000008f000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000000008f000 - 0000000000090000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 0000000000090000 - 00000000000a0000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 00000000000a0000 - 00000000000c0000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000007eef1000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007eef1000 - 000000007f0f2000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007f0f2000 - 000000007fe53000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007fe53000 - 000000007fe79000 (unusable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007fe79000 - 000000007fe89000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007fe89000 - 000000007feb3000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007feb3000 - 000000007feb9000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007feb9000 - 000000007febf000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007febf000 - 000000007fed2000 (usable)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007fed2000 - 000000007fed4000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007fed4000 - 000000007fed7000 (ACPI data)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007fed7000 - 000000007feda000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007feda000 - 000000007fedb000 (ACPI data)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007fedb000 - 000000007feef000 (ACPI NVS)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007feef000 - 000000007feff000 (ACPI data)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 000000007feff000 - 0000000080000000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 00000000f00f8000 - 00000000f00f9000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  modified: 00000000fffa0000 - 00000000fffd0000 (reserved)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007fed2000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  0000000000 - 007fe00000 page 2M
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  007fe00000 - 007fed2000 page 4k
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] kernel direct mapping tables up to 7fed2000 @ 16000-1a000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] RAMDISK: 5cfc7000 - 5da46000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: RSDP 000000007fefe014 00024 (v02 APPLE )
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: XSDT 000000007fefe1c0 0007C (v01 APPLE   Apple00 00000070      01000013)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: FACP 000000007fefc000 000F4 (v03 APPLE   Apple00 00000070 Loki 0000005F)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: DSDT 000000007fef1000 048A8 (v01 APPLE  MacBookP 00030001 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: FACS 000000007fedb000 00040
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: HPET 000000007fefb000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: APIC 000000007fefa000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: MCFG 000000007fef9000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: ASF! 000000007fef8000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: SBST 000000007fef7000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: ECDT 000000007fef6000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: SSDT 000000007feda000 00137 (v01 APPLE  SataAhci 00001000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: SSDT 000000007fed6000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: SSDT 000000007fed5000 0025F (v01  APPLE  Cpu0Tst 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: SSDT 000000007fed4000 000A6 (v01  APPLE  Cpu1Tst 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] No NUMA configuration found
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007fed2000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000007fed2000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   NODE_DATA [0000000001d18240 - 0000000001d1d23f]
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880002600000-ffff8800041fffff] on node 0
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Zone PFN ranges:
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   Normal   empty
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Movable zone start PFN for each node
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] early_node_map[7] active PFN ranges
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000008f
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]     0: 0x00000090 -> 0x000000a0
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007eef1
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]     0: 0x0007f0f2 -> 0x0007fe53
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]     0: 0x0007fe79 -> 0x0007fe89
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]     0: 0x0007feb3 -> 0x0007feb9
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]     0: 0x0007febf -> 0x0007fed2
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] On node 0 totalpages: 523274
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   DMA zone: 3927 pages, LIFO batch:0
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   DMA32 zone: 7108 pages used for memmap
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   DMA32 zone: 512183 pages, LIFO batch:31
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] nr_irqs_gsi: 40
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] early_res array is doubled to 64 at [18000 - 187ff]
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000008f000 - 0000000000090000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000c0000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007eef1000 - 000000007f0f2000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007fe53000 - 000000007fe79000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007fe89000 - 000000007feb3000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007feb9000 - 000000007febf000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:700f8000)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u1048576
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] early_res array is doubled to 128 at [18800 - 197ff]
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u1048576 alloc=1*2097152
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516110
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Policy zone: DMA32
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=cba2822c-7f25-48a4-a629-80bcda8f0cb7 ro
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Checking aperture...
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] No AGP bridge found
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Subtract (62 early reservations)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #2 [005cfc7000 - 005da46000]         RAMDISK
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #3 [000009f000 - 0000100000]   BIOS reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #4 [000008d000 - 000008d960]      EFI memmap
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #5 [0001d18000 - 0001d18221]             BRK
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #6 [0000010000 - 0000012000]      TRAMPOLINE
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #7 [0000012000 - 0000016000]     ACPI WAKEUP
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #8 [0000016000 - 0000018000]         PGTABLE
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #9 [0001d18240 - 0001d1d240]       NODE_DATA
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #10 [0001d1d240 - 0001d1e240]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #11 [0001d17140 - 0001d172c0]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #12 [000251f000 - 0002520000]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #13 [0002520000 - 0002521000]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #14 [0002600000 - 0004200000]        MEMMAP 0
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #15 [0001d172c0 - 0001d17440]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #16 [0001d1e240 - 0001d2a240]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #17 [0001d2b000 - 0001d2c000]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #18 [0001d17440 - 0001d17481]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #19 [0001d174c0 - 0001d17503]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #20 [0001d17540 - 0001d17a80]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #21 [0001d17a80 - 0001d17ae8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #22 [0001d17b00 - 0001d17b68]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #23 [0001d17b80 - 0001d17be8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #24 [0001d17c00 - 0001d17c68]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #25 [0001d17c80 - 0001d17ce8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #26 [0001d17d00 - 0001d17d68]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #27 [0001d17d80 - 0001d17de8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #28 [0001d17e00 - 0001d17e68]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #29 [0001d17e80 - 0001d17ee8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #30 [0001d17f00 - 0001d17f68]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #31 [0001d17f80 - 0001d17fe8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #32 [0001d2a240 - 0001d2a2a8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #33 [0001d2a2c0 - 0001d2a328]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #34 [0001d2a340 - 0001d2a3a8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #35 [0001d2a3c0 - 0001d2a428]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #36 [0001d2a440 - 0001d2a4a8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #37 [0001d2a4c0 - 0001d2a528]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #38 [0001d2a540 - 0001d2a5a8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #39 [0001d2a5c0 - 0001d2a628]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #40 [0001d2a640 - 0001d2a6a8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #41 [0001d2a6c0 - 0001d2a728]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #42 [0001d2a740 - 0001d2a7a8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #43 [0001d2a7c0 - 0001d2a828]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #44 [0001d2a840 - 0001d2a860]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #45 [0001d2a880 - 0001d2a8a0]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #46 [0001d2a8c0 - 0001d2a8e0]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #47 [0001d2a900 - 0001d2a920]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #48 [0001d2a940 - 0001d2a960]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #49 [0001d2a980 - 0001d2a9a0]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #50 [0001d2a9c0 - 0001d2aa1d]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #51 [0001d2aa40 - 0001d2aa9d]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #52 [0001e00000 - 0001e1e000]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #53 [0001f00000 - 0001f1e000]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #54 [0001d2aac0 - 0001d2aac8]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #55 [0001d2ab00 - 0001d2ab08]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #56 [0001d2ab40 - 0001d2ab48]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #57 [0001d2ab80 - 0001d2ab90]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #58 [0001d2abc0 - 0001d2ad00]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #59 [0001d2ad00 - 0001d2ad60]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #60 [0001d2ad80 - 0001d2ade0]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000]   #61 [0001d2c000 - 0001d34000]         BOOTMEM
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Memory: 2039868k/2095944k available (5708k kernel code, 2848k absent, 53228k reserved, 5382k data, 908k init)
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Hierarchical RCU implementation.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:512
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Extended CMOS year: 2000
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Console: colour dummy device 80x25
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] console [tty0] enabled
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] allocated 20971520 bytes of page_cgroup
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] hpet clockevent registered
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Fast TSC calibration using PIT
Dec 21 00:38:18 MacBuntu kernel: [    0.000000] Detected 2593.499 MHz processor.
Dec 21 00:38:18 MacBuntu kernel: [    0.010010] Calibrating delay loop (skipped), value calculated using timer frequency.. 5186.99 BogoMIPS (lpj=25934990)
Dec 21 00:38:18 MacBuntu kernel: [    0.010018] pid_max: default: 32768 minimum: 301
Dec 21 00:38:18 MacBuntu kernel: [    0.010033] init_memory_mapping: 000000007feff000-000000007ff00000
Dec 21 00:38:18 MacBuntu kernel: [    0.010038]  007feff000 - 007ff00000 page 4k
Dec 21 00:38:18 MacBuntu kernel: [    0.010157] init_memory_mapping: 000000007ff00000-0000000080000000
Dec 21 00:38:18 MacBuntu kernel: [    0.010160]  007ff00000 - 0080000000 page 4k
Dec 21 00:38:18 MacBuntu kernel: [    0.010964] Security Framework initialized
Dec 21 00:38:18 MacBuntu kernel: [    0.010986] AppArmor: AppArmor initialized
Dec 21 00:38:18 MacBuntu kernel: [    0.010988] Yama: becoming mindful.
Dec 21 00:38:18 MacBuntu kernel: [    0.011206] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.012320] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.012845] Mount-cache hash table entries: 256
Dec 21 00:38:18 MacBuntu kernel: [    0.012977] Initializing cgroup subsys ns
Dec 21 00:38:18 MacBuntu kernel: [    0.012985] Initializing cgroup subsys cpuacct
Dec 21 00:38:18 MacBuntu kernel: [    0.012989] Initializing cgroup subsys memory
Dec 21 00:38:18 MacBuntu kernel: [    0.013000] Initializing cgroup subsys devices
Dec 21 00:38:18 MacBuntu kernel: [    0.013003] Initializing cgroup subsys freezer
Dec 21 00:38:18 MacBuntu kernel: [    0.013007] Initializing cgroup subsys net_cls
Dec 21 00:38:18 MacBuntu kernel: [    0.013036] CPU: Physical Processor ID: 0
Dec 21 00:38:18 MacBuntu kernel: [    0.013039] CPU: Processor Core ID: 0
Dec 21 00:38:18 MacBuntu kernel: [    0.013043] mce: CPU supports 6 MCE banks
Dec 21 00:38:18 MacBuntu kernel: [    0.013052] CPU0: Thermal monitoring enabled (TM2)
Dec 21 00:38:18 MacBuntu kernel: [    0.013057] using mwait in idle threads.
Dec 21 00:38:18 MacBuntu kernel: [    0.013060] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Dec 21 00:38:18 MacBuntu kernel: [    0.013068] PEBS disabled due to CPU errata.
Dec 21 00:38:18 MacBuntu kernel: [    0.013073] ... version:                2
Dec 21 00:38:18 MacBuntu kernel: [    0.013076] ... bit width:              40
Dec 21 00:38:18 MacBuntu kernel: [    0.013078] ... generic registers:      2
Dec 21 00:38:18 MacBuntu kernel: [    0.013081] ... value mask:             000000ffffffffff
Dec 21 00:38:18 MacBuntu kernel: [    0.013084] ... max period:             000000007fffffff
Dec 21 00:38:18 MacBuntu kernel: [    0.013087] ... fixed-purpose events:   3
Dec 21 00:38:18 MacBuntu kernel: [    0.013090] ... event mask:             0000000700000003
Dec 21 00:38:18 MacBuntu kernel: [    0.015246] ACPI: Core revision 20100428
Dec 21 00:38:18 MacBuntu kernel: [    0.025528] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec 21 00:38:18 MacBuntu kernel: [    0.025535] ftrace: allocating 22680 entries in 89 pages
Dec 21 00:38:18 MacBuntu kernel: [    0.030052] Setting APIC routing to flat
Dec 21 00:38:18 MacBuntu kernel: [    0.030406] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 21 00:38:18 MacBuntu kernel: [    0.134143] CPU0: Intel(R) Core(TM)2 Duo CPU     T7800  @ 2.60GHz stepping 0b
Dec 21 00:38:18 MacBuntu kernel: [    0.140000] Booting Node   0, Processors  #1 Ok.
Dec 21 00:38:18 MacBuntu kernel: [    0.300017] Brought up 2 CPUs
Dec 21 00:38:18 MacBuntu kernel: [    0.300023] Total of 2 processors activated (10373.98 BogoMIPS).
Dec 21 00:38:18 MacBuntu kernel: [    0.300596] devtmpfs: initialized
Dec 21 00:38:18 MacBuntu kernel: [    0.300596] regulator: core version 0.5
Dec 21 00:38:18 MacBuntu kernel: [    0.300622] Time:  5:38:08  Date: 12/21/10
Dec 21 00:38:18 MacBuntu kernel: [    0.300655] NET: Registered protocol family 16
Dec 21 00:38:18 MacBuntu kernel: [    0.300676] Trying to unpack rootfs image as initramfs...
Dec 21 00:38:18 MacBuntu kernel: [    0.300769] ACPI: bus type pci registered
Dec 21 00:38:18 MacBuntu kernel: [    0.300833] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
Dec 21 00:38:18 MacBuntu kernel: [    0.300839] PCI: not using MMCONFIG
Dec 21 00:38:18 MacBuntu kernel: [    0.300841] PCI: Using configuration type 1 for base access
Dec 21 00:38:18 MacBuntu kernel: [    0.310154] bio: create slab <bio-0> at 0
Dec 21 00:38:18 MacBuntu kernel: [    0.311116] ACPI: EC: EC description table is found, configuring boot EC
Dec 21 00:38:18 MacBuntu kernel: [    0.312018] ACPI: BIOS _OSI(Linux) query ignored
Dec 21 00:38:18 MacBuntu kernel: [    0.312451] ACPI: SSDT 000000007fed9c18 00382 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.312714] ACPI: Dynamic OEM Table Load:
Dec 21 00:38:18 MacBuntu kernel: [    0.312719] ACPI: SSDT (null) 00382 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.312889] ACPI: SSDT 000000007fed7c18 002A0 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.313136] ACPI: Dynamic OEM Table Load:
Dec 21 00:38:18 MacBuntu kernel: [    0.313140] ACPI: SSDT (null) 002A0 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.313464] ACPI: SSDT 000000007fed8f18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.313720] ACPI: Dynamic OEM Table Load:
Dec 21 00:38:18 MacBuntu kernel: [    0.313724] ACPI: SSDT (null) 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.313840] ACPI: SSDT 000000007fed7f18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.314090] ACPI: Dynamic OEM Table Load:
Dec 21 00:38:18 MacBuntu kernel: [    0.314094] ACPI: SSDT (null) 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
Dec 21 00:38:18 MacBuntu kernel: [    0.314150] ACPI: Interpreter enabled
Dec 21 00:38:18 MacBuntu kernel: [    0.314153] ACPI: (supports S0 S3 S4 S5)
Dec 21 00:38:18 MacBuntu kernel: [    0.314173] ACPI: Using IOAPIC for interrupt routing
Dec 21 00:38:18 MacBuntu kernel: [    0.314210] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
Dec 21 00:38:18 MacBuntu kernel: [    0.315962] PCI: MMCONFIG at [mem 0xf0000000-0xffffffff] reserved in ACPI motherboard resources
Dec 21 00:38:18 MacBuntu kernel: [    0.315969] PCI: MMCONFIG for 0000 [bus00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) (size reduced!)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] ACPI: No dock devices found.
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:01.0: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1a.0: reg 20: [io  0x60c0-0x60df]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1a.1: reg 20: [io  0x60a0-0x60bf]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1a.7: reg 10: [mem 0x9b504c00-0x9b504fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1a.7: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1b.0: reg 10: [mem 0x9b500000-0x9b503fff 64bit]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1b.0: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.0: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.2: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.4: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.5: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1d.0: reg 20: [io  0x6080-0x609f]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1d.1: reg 20: [io  0x6060-0x607f]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1d.2: reg 20: [io  0x6040-0x605f]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1d.7: reg 10: [mem 0x9b504800-0x9b504bff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1d.7: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH6 ACPI/GPIO/TCO
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 000f)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0300 (mask 001f)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.1: reg 10: [io  0x6108-0x610f]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.1: reg 14: [io  0x611c-0x611f]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.1: reg 18: [io  0x6100-0x6107]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.1: reg 1c: [io  0x6118-0x611b]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.1: reg 20: [io  0x60e0-0x60ef]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: reg 10: [io  0x60f8-0x60ff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: reg 14: [io  0x6114-0x6117]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: reg 18: [io  0x60f0-0x60f7]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: reg 1c: [io  0x6110-0x6113]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: reg 20: [io  0x6020-0x603f]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: reg 24: [mem 0x9b504000-0x9b5047ff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: PME# supported from D3hot
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.2: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.3: reg 10: [mem 0x9b505000-0x9b5050ff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:01:00.0: reg 10: [mem 0x92000000-0x92ffffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:01:00.0: reg 14: [mem 0x80000000-0x8fffffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:01:00.0: reg 1c: [mem 0x90000000-0x91ffffff 64bit]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:01:00.0: reg 24: [io  0x5000-0x507f]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:01:00.0: reg 30: [mem 0x93000000-0x9301ffff pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x930fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.0:   bridge window [mem 0x9b400000-0x9b4fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.2:   bridge window [mem 0x97400000-0x9b3fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.2:   bridge window [mem 0x93100000-0x970fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0b:00.0: reg 10: [mem 0x97300000-0x9730ffff 64bit]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0b:00.0: supports D1
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0b:00.0: PME# supported from D0 D1 D3hot
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0b:00.0: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0b:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.4: PCI bridge to [bus 0b-0b]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.4:   bridge window [mem 0x97300000-0x973fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0c:00.0: reg 10: [mem 0x97200000-0x97203fff 64bit]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0c:00.0: reg 18: [io  0x3000-0x30ff]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0c:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0c:00.0: supports D1 D2
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0c:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:0c:00.0: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.5: PCI bridge to [bus 0c-0c]
Dec 21 00:38:18 MacBuntu kernel: [    0.345070] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.350004] pci 0000:00:1c.5:   bridge window [mem 0x97200000-0x972fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.350011] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.350085] pci 0000:0d:03.0: reg 10: [mem 0x97104000-0x971047ff]
Dec 21 00:38:18 MacBuntu kernel: [    0.350094] pci 0000:0d:03.0: reg 14: [mem 0x97100000-0x97103fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.350159] pci 0000:0d:03.0: supports D1 D2
Dec 21 00:38:18 MacBuntu kernel: [    0.350160] pci 0000:0d:03.0: PME# supported from D0 D1 D2 D3hot
Dec 21 00:38:18 MacBuntu kernel: [    0.350165] pci 0000:0d:03.0: PME# disabled
Dec 21 00:38:18 MacBuntu kernel: [    0.350226] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350233] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.350238] pci 0000:00:1e.0:   bridge window [mem 0x97100000-0x971fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.350246] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.350248] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350250] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350252] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350254] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350256] pci 0000:00:1e.0:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350259] pci 0000:00:1e.0:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350261] pci 0000:00:1e.0:   bridge window [mem 0x000cc000-0x000cffff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350263] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350265] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350267] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350269] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350271] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350273] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350275] pci 0000:00:1e.0:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350277] pci 0000:00:1e.0:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350279] pci 0000:00:1e.0:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350281] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
Dec 21 00:38:18 MacBuntu kernel: [    0.350322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 21 00:38:18 MacBuntu kernel: [    0.350484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
Dec 21 00:38:18 MacBuntu kernel: [    0.350555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Dec 21 00:38:18 MacBuntu kernel: [    0.350613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Dec 21 00:38:18 MacBuntu kernel: [    0.350671] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Dec 21 00:38:18 MacBuntu kernel: [    0.350754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Dec 21 00:38:18 MacBuntu kernel: [    0.358528] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.358619] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.358703] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.358790] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.358878] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.358961] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.359047] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.359131] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 21 00:38:18 MacBuntu kernel: [    0.359172] HEST: Table is not found!
Dec 21 00:38:18 MacBuntu kernel: [    0.359262] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
Dec 21 00:38:18 MacBuntu kernel: [    0.359268] vgaarb: loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.359399] SCSI subsystem initialized
Dec 21 00:38:18 MacBuntu kernel: [    0.370047] libata version 3.00 loaded.
Dec 21 00:38:18 MacBuntu kernel: [    0.370112] usbcore: registered new interface driver usbfs
Dec 21 00:38:18 MacBuntu kernel: [    0.370129] usbcore: registered new interface driver hub
Dec 21 00:38:18 MacBuntu kernel: [    0.370155] usbcore: registered new device driver usb
Dec 21 00:38:18 MacBuntu kernel: [    0.370303] ACPI: WMI: Mapper loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.370307] PCI: Using ACPI for IRQ routing
Dec 21 00:38:18 MacBuntu kernel: [    0.370311] PCI: pci_cache_line_size set to 64 bytes
Dec 21 00:38:18 MacBuntu kernel: [    0.370468] reserve RAM buffer: 000000000008f000 - 000000000008ffff 
Dec 21 00:38:18 MacBuntu kernel: [    0.370471] reserve RAM buffer: 000000007eef1000 - 000000007fffffff 
Dec 21 00:38:18 MacBuntu kernel: [    0.370475] reserve RAM buffer: 000000007fe53000 - 000000007fffffff 
Dec 21 00:38:18 MacBuntu kernel: [    0.370478] reserve RAM buffer: 000000007fe89000 - 000000007fffffff 
Dec 21 00:38:18 MacBuntu kernel: [    0.370482] reserve RAM buffer: 000000007feb9000 - 000000007fffffff 
Dec 21 00:38:18 MacBuntu kernel: [    0.370485] reserve RAM buffer: 000000007fed2000 - 000000007fffffff 
Dec 21 00:38:18 MacBuntu kernel: [    0.370577] NetLabel: Initializing
Dec 21 00:38:18 MacBuntu kernel: [    0.370580] NetLabel:  domain hash size = 128
Dec 21 00:38:18 MacBuntu kernel: [    0.370582] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 21 00:38:18 MacBuntu kernel: [    0.370597] NetLabel:  unlabeled traffic allowed by default
Dec 21 00:38:18 MacBuntu kernel: [    0.370634] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Dec 21 00:38:18 MacBuntu kernel: [    0.370642] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 21 00:38:18 MacBuntu kernel: [    0.370647] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Dec 21 00:38:18 MacBuntu kernel: [    0.390037] Switching to clocksource tsc
Dec 21 00:38:18 MacBuntu kernel: [    0.398591] AppArmor: AppArmor Filesystem Enabled
Dec 21 00:38:18 MacBuntu kernel: [    0.398619] pnp: PnP ACPI init
Dec 21 00:38:18 MacBuntu kernel: [    0.398646] ACPI: bus type pnp registered
Dec 21 00:38:18 MacBuntu kernel: [    0.404158] pnp: PnP ACPI: found 9 devices
Dec 21 00:38:18 MacBuntu kernel: [    0.404163] ACPI: ACPI bus type pnp unregistered
Dec 21 00:38:18 MacBuntu kernel: [    0.404179] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404183] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404187] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404191] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404196] system 00:01: [mem 0xf0000000-0xf3ffffff] could not be reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404200] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404204] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404212] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404219] system 00:07: [io  0x0680-0x069f] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404223] system 00:07: [io  0x0800-0x080f] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404227] system 00:07: [io  0x0810-0x0817] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404231] system 00:07: [io  0x0400-0x047f] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404234] system 00:07: [io  0x0500-0x053f] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.404238] system 00:07: [io  0x1640-0x164f] has been reserved
Dec 21 00:38:18 MacBuntu kernel: [    0.410007] pci 0000:0c:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410083] pci 0000:00:1c.0: BAR 15: assigned [mem 0x9b600000-0x9b7fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410090] pci 0000:00:1c.4: BAR 15: assigned [mem 0x9b800000-0x9b9fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410097] pci 0000:00:1c.5: BAR 15: assigned [mem 0x9ba00000-0x9bbfffff pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410102] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410106] pci 0000:00:1c.4: BAR 13: assigned [io  0x7000-0x7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410110] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 21 00:38:18 MacBuntu kernel: [    0.410114] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410120] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x930fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410124] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410131] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 21 00:38:18 MacBuntu kernel: [    0.410135] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410143] pci 0000:00:1c.0:   bridge window [mem 0x9b400000-0x9b4fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410149] pci 0000:00:1c.0:   bridge window [mem 0x9b600000-0x9b7fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410159] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
Dec 21 00:38:18 MacBuntu kernel: [    0.410163] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410171] pci 0000:00:1c.2:   bridge window [mem 0x97400000-0x9b3fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410177] pci 0000:00:1c.2:   bridge window [mem 0x93100000-0x970fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410187] pci 0000:00:1c.4: PCI bridge to [bus 0b-0b]
Dec 21 00:38:18 MacBuntu kernel: [    0.410191] pci 0000:00:1c.4:   bridge window [io  0x7000-0x7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410199] pci 0000:00:1c.4:   bridge window [mem 0x97300000-0x973fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410205] pci 0000:00:1c.4:   bridge window [mem 0x9b800000-0x9b9fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410216] pci 0000:0c:00.0: BAR 6: assigned [mem 0x9ba00000-0x9ba1ffff pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410220] pci 0000:00:1c.5: PCI bridge to [bus 0c-0c]
Dec 21 00:38:18 MacBuntu kernel: [    0.410224] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410232] pci 0000:00:1c.5:   bridge window [mem 0x97200000-0x972fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410238] pci 0000:00:1c.5:   bridge window [mem 0x9ba00000-0x9bbfffff pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410248] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d]
Dec 21 00:38:18 MacBuntu kernel: [    0.410250] pci 0000:00:1e.0:   bridge window [io  disabled]
Dec 21 00:38:18 MacBuntu kernel: [    0.410258] pci 0000:00:1e.0:   bridge window [mem 0x97100000-0x971fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410264] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Dec 21 00:38:18 MacBuntu kernel: [    0.410282]   alloc irq_desc for 16 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.410284]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.410291] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 00:38:18 MacBuntu kernel: [    0.410296] pci 0000:00:01.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.410305] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Dec 21 00:38:18 MacBuntu kernel: [    0.410310] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 00:38:18 MacBuntu kernel: [    0.410318] pci 0000:00:1c.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.410328] pci 0000:00:1c.2: enabling device (0000 -> 0003)
Dec 21 00:38:18 MacBuntu kernel: [    0.410332]   alloc irq_desc for 18 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.410334]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.410337] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 21 00:38:18 MacBuntu kernel: [    0.410345] pci 0000:00:1c.2: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.410355] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 00:38:18 MacBuntu kernel: [    0.410361] pci 0000:00:1c.4: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.410371]   alloc irq_desc for 17 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.410372]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.410375] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 21 00:38:18 MacBuntu kernel: [    0.410382] pci 0000:00:1c.5: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.410465] pci 0000:00:1e.0: power state changed by ACPI to D0
Dec 21 00:38:18 MacBuntu kernel: [    0.410510] pci 0000:00:1e.0: power state changed by ACPI to D0
Dec 21 00:38:18 MacBuntu kernel: [    0.410518] pci 0000:00:1e.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.410523] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 21 00:38:18 MacBuntu kernel: [    0.410525] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410527] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410528] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410530] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410532] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410534] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410536] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410537] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410539] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410541] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410543] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410545] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410546] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410548] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410550] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410552] pci_bus 0000:00: resource 20 [mem 0x80000000-0xfebfffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410554] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410556] pci_bus 0000:01: resource 1 [mem 0x90000000-0x930fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410558] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410560] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410562] pci_bus 0000:02: resource 1 [mem 0x9b400000-0x9b4fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410564] pci_bus 0000:02: resource 2 [mem 0x9b600000-0x9b7fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410565] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410567] pci_bus 0000:03: resource 1 [mem 0x97400000-0x9b3fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410569] pci_bus 0000:03: resource 2 [mem 0x93100000-0x970fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410571] pci_bus 0000:0b: resource 0 [io  0x7000-0x7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410573] pci_bus 0000:0b: resource 1 [mem 0x97300000-0x973fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410575] pci_bus 0000:0b: resource 2 [mem 0x9b800000-0x9b9fffff 64bit pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410577] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410578] pci_bus 0000:0c: resource 1 [mem 0x97200000-0x972fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410580] pci_bus 0000:0c: resource 2 [mem 0x9ba00000-0x9bbfffff pref]
Dec 21 00:38:18 MacBuntu kernel: [    0.410582] pci_bus 0000:0d: resource 1 [mem 0x97100000-0x971fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410584] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
Dec 21 00:38:18 MacBuntu kernel: [    0.410586] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410587] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410589] pci_bus 0000:0d: resource 7 [mem 0x000c0000-0x000c3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410591] pci_bus 0000:0d: resource 8 [mem 0x000c4000-0x000c7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410593] pci_bus 0000:0d: resource 9 [mem 0x000c8000-0x000cbfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410594] pci_bus 0000:0d: resource 10 [mem 0x000cc000-0x000cffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410596] pci_bus 0000:0d: resource 11 [mem 0x000d0000-0x000d3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410598] pci_bus 0000:0d: resource 12 [mem 0x000d4000-0x000d7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410600] pci_bus 0000:0d: resource 13 [mem 0x000d8000-0x000dbfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410602] pci_bus 0000:0d: resource 14 [mem 0x000dc000-0x000dffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410603] pci_bus 0000:0d: resource 15 [mem 0x000e0000-0x000e3fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410605] pci_bus 0000:0d: resource 16 [mem 0x000e4000-0x000e7fff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410607] pci_bus 0000:0d: resource 17 [mem 0x000e8000-0x000ebfff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410609] pci_bus 0000:0d: resource 18 [mem 0x000ec000-0x000effff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410610] pci_bus 0000:0d: resource 19 [mem 0x000f0000-0x000fffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410612] pci_bus 0000:0d: resource 20 [mem 0x80000000-0xfebfffff]
Dec 21 00:38:18 MacBuntu kernel: [    0.410651] NET: Registered protocol family 2
Dec 21 00:38:18 MacBuntu kernel: [    0.410756] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.411415] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.413469] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.414073] TCP: Hash tables configured (established 262144 bind 65536)
Dec 21 00:38:18 MacBuntu kernel: [    0.414078] TCP reno registered
Dec 21 00:38:18 MacBuntu kernel: [    0.414089] UDP hash table entries: 1024 (order: 3, 32768 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.414113] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.414248] NET: Registered protocol family 1
Dec 21 00:38:18 MacBuntu kernel: [    0.414451] PCI: CLS mismatch (256 != 64), using 64 bytes
Dec 21 00:38:18 MacBuntu kernel: [    0.414675] Scanning for low memory corruption every 60 seconds
Dec 21 00:38:18 MacBuntu kernel: [    0.414860] audit: initializing netlink socket (disabled)
Dec 21 00:38:18 MacBuntu kernel: [    0.414872] type=2000 audit(1292909888.400:1): initialized
Dec 21 00:38:18 MacBuntu kernel: [    0.440043] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 21 00:38:18 MacBuntu kernel: [    0.441267] VFS: Disk quotas dquot_6.5.2
Dec 21 00:38:18 MacBuntu kernel: [    0.441321] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 21 00:38:18 MacBuntu kernel: [    0.441817] fuse init (API version 7.14)
Dec 21 00:38:18 MacBuntu kernel: [    0.441886] msgmni has been set to 3984
Dec 21 00:38:18 MacBuntu kernel: [    0.442127] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 21 00:38:18 MacBuntu kernel: [    0.442133] io scheduler noop registered
Dec 21 00:38:18 MacBuntu kernel: [    0.442135] io scheduler deadline registered
Dec 21 00:38:18 MacBuntu kernel: [    0.442168] io scheduler cfq registered (default)
Dec 21 00:38:18 MacBuntu kernel: [    0.442268] pcieport 0000:00:01.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.442293]   alloc irq_desc for 40 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442295]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442304] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Dec 21 00:38:18 MacBuntu kernel: [    0.442371] pcieport 0000:00:1c.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.442416]   alloc irq_desc for 41 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442417]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442426] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Dec 21 00:38:18 MacBuntu kernel: [    0.442521] pcieport 0000:00:1c.2: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.442566]   alloc irq_desc for 42 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442568]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442576] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Dec 21 00:38:18 MacBuntu kernel: [    0.442669] pcieport 0000:00:1c.4: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.442716]   alloc irq_desc for 43 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442717]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442726] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
Dec 21 00:38:18 MacBuntu kernel: [    0.442820] pcieport 0000:00:1c.5: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.442867]   alloc irq_desc for 44 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442868]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.442877] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
Dec 21 00:38:18 MacBuntu kernel: [    0.442980] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 21 00:38:18 MacBuntu kernel: [    0.443476] pciehp 0000:00:01.0:pcie04: HPC vendor_id 8086 device_id 2a01 ss_vid 8086 ss_did 0
Dec 21 00:38:18 MacBuntu kernel: [    0.443511] pciehp 0000:00:01.0:pcie04: service driver pciehp loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.443526] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 283f ss_vid 0 ss_did 0
Dec 21 00:38:18 MacBuntu kernel: [    0.443559] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.443574] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 2843 ss_vid 0 ss_did 0
Dec 21 00:38:18 MacBuntu kernel: [    0.443607] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.443621] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 2847 ss_vid 0 ss_did 0
Dec 21 00:38:18 MacBuntu kernel: [    0.443655] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.443670] pciehp 0000:00:1c.5:pcie04: HPC vendor_id 8086 device_id 2849 ss_vid 0 ss_did 0
Dec 21 00:38:18 MacBuntu kernel: [    0.443705] pciehp 0000:00:1c.5:pcie04: service driver pciehp loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.443711] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 21 00:38:18 MacBuntu kernel: [    0.443779] efifb: dmi detected MacBookPro3,1 - framebuffer at 0000000080030000 (1440x900, stride 8192)
Dec 21 00:38:18 MacBuntu kernel: [    0.443799] efifb: probing for efifb
Dec 21 00:38:18 MacBuntu kernel: [    0.446157] efifb: framebuffer at 0x80030000, mapped to 0xffffc90004a00000, using 7232k, total 7232k
Dec 21 00:38:18 MacBuntu kernel: [    0.446162] efifb: mode is 1440x900x32, linelength=8192, pages=1
Dec 21 00:38:18 MacBuntu kernel: [    0.446165] efifb: scrolling: redraw
Dec 21 00:38:18 MacBuntu kernel: [    0.446168] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Dec 21 00:38:18 MacBuntu kernel: [    0.509649] Freeing initrd memory: 10748k freed
Dec 21 00:38:18 MacBuntu kernel: [    0.527946] Console: switching to colour frame buffer device 180x56
Dec 21 00:38:18 MacBuntu kernel: [    0.606949] fb0: EFI VGA frame buffer device
Dec 21 00:38:18 MacBuntu kernel: [    0.607338] intel_idle: MWAIT substates: 0x22220
Dec 21 00:38:18 MacBuntu kernel: [    0.607340] intel_idle: does not run on family 6 model 15
Dec 21 00:38:18 MacBuntu kernel: [    0.607510] ACPI: AC Adapter [ADP1] (on-line)
Dec 21 00:38:18 MacBuntu kernel: [    0.607998] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Dec 21 00:38:18 MacBuntu kernel: [    0.608757] ACPI: Lid Switch [LID0]
Dec 21 00:38:18 MacBuntu kernel: [    0.609103] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Dec 21 00:38:18 MacBuntu kernel: [    0.609849] ACPI: Power Button [PWRB]
Dec 21 00:38:18 MacBuntu kernel: [    0.610259] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Dec 21 00:38:18 MacBuntu kernel: [    0.611004] ACPI: Sleep Button [SLPB]
Dec 21 00:38:18 MacBuntu kernel: [    0.611372] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Dec 21 00:38:18 MacBuntu kernel: [    0.612032] ACPI: Power Button [PWRF]
Dec 21 00:38:18 MacBuntu kernel: [    0.612552] ACPI: acpi_idle registered with cpuidle
Dec 21 00:38:18 MacBuntu kernel: [    0.614247] Monitor-Mwait will be used to enter C-1 state
Dec 21 00:38:18 MacBuntu kernel: [    0.614274] Monitor-Mwait will be used to enter C-2 state
Dec 21 00:38:18 MacBuntu kernel: [    0.614292] Monitor-Mwait will be used to enter C-3 state
Dec 21 00:38:18 MacBuntu kernel: [    0.614297] Marking TSC unstable due to TSC halts in idle
Dec 21 00:38:18 MacBuntu kernel: [    0.614845] Switching to clocksource hpet
Dec 21 00:38:18 MacBuntu kernel: [    0.619329] ERST: Table is not found!
Dec 21 00:38:18 MacBuntu kernel: [    0.620219] Linux agpgart interface v0.103
Dec 21 00:38:18 MacBuntu kernel: [    0.620636] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 21 00:38:18 MacBuntu kernel: [    0.622646] brd: module loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.623431] loop: module loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.623921] ata_piix 0000:00:1f.1: version 2.13
Dec 21 00:38:18 MacBuntu kernel: [    0.623958] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
Dec 21 00:38:18 MacBuntu kernel: [    0.624577] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
Dec 21 00:38:18 MacBuntu kernel: [    0.625259]   alloc irq_desc for 21 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.625261]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.625268] ata_piix 0000:00:1f.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 21 00:38:18 MacBuntu kernel: [    0.625975] ata_piix 0000:00:1f.1: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.626050] scsi0 : ata_piix
Dec 21 00:38:18 MacBuntu kernel: [    0.626378] scsi1 : ata_piix
Dec 21 00:38:18 MacBuntu kernel: [    0.627163] ata1: PATA max UDMA/100 cmd 0x6108 ctl 0x611c bmdma 0x60e0 irq 21
Dec 21 00:38:18 MacBuntu kernel: [    0.627828] ata2: PATA max UDMA/100 cmd 0x6100 ctl 0x6118 bmdma 0x60e8 irq 21
Dec 21 00:38:18 MacBuntu kernel: [    0.628756] Fixed MDIO Bus: probed
Dec 21 00:38:18 MacBuntu kernel: [    0.629109] PPP generic driver version 2.4.2
Dec 21 00:38:18 MacBuntu kernel: [    0.629548] tun: Universal TUN/TAP device driver, 1.6
Dec 21 00:38:18 MacBuntu kernel: [    0.630043] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 21 00:38:18 MacBuntu kernel: [    0.630704] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 21 00:38:18 MacBuntu kernel: [    0.631333] ehci_hcd 0000:00:1a.7: enabling device (0000 -> 0002)
Dec 21 00:38:18 MacBuntu kernel: [    0.645163] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Dec 21 00:38:18 MacBuntu kernel: [    0.659418] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.659422] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 21 00:38:18 MacBuntu kernel: [    0.673838] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Dec 21 00:38:18 MacBuntu kernel: [    0.688830] ehci_hcd 0000:00:1a.7: debug port 1
Dec 21 00:38:18 MacBuntu kernel: [    0.707680] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Dec 21 00:38:18 MacBuntu kernel: [    0.707700] ehci_hcd 0000:00:1a.7: irq 21, io mem 0x9b504c00
Dec 21 00:38:18 MacBuntu kernel: [    0.727627] ACPI: EC: GPE storm detected, transactions will use polling mode
Dec 21 00:38:18 MacBuntu kernel: [    0.742515] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Dec 21 00:38:18 MacBuntu kernel: [    0.742623] hub 1-0:1.0: USB hub found
Dec 21 00:38:18 MacBuntu kernel: [    0.742628] hub 1-0:1.0: 4 ports detected
Dec 21 00:38:18 MacBuntu kernel: [    0.742690] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
Dec 21 00:38:18 MacBuntu kernel: [    0.742694]   alloc irq_desc for 20 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.742695]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    0.742699] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
Dec 21 00:38:18 MacBuntu kernel: [    0.742712] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.742715] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 21 00:38:18 MacBuntu kernel: [    0.742742] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Dec 21 00:38:18 MacBuntu kernel: [    0.742773] ehci_hcd 0000:00:1d.7: debug port 1
Dec 21 00:38:18 MacBuntu kernel: [    0.746648] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Dec 21 00:38:18 MacBuntu kernel: [    0.746661] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x9b504800
Dec 21 00:38:18 MacBuntu kernel: [    0.762515] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 21 00:38:18 MacBuntu kernel: [    0.762588] hub 2-0:1.0: USB hub found
Dec 21 00:38:18 MacBuntu kernel: [    0.762591] hub 2-0:1.0: 6 ports detected
Dec 21 00:38:18 MacBuntu kernel: [    0.762651] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 21 00:38:18 MacBuntu kernel: [    0.762661] uhci_hcd: USB Universal Host Controller Interface driver
Dec 21 00:38:18 MacBuntu kernel: [    0.762708] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 21 00:38:18 MacBuntu kernel: [    0.762714] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.762717] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 21 00:38:18 MacBuntu kernel: [    0.762742] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Dec 21 00:38:18 MacBuntu kernel: [    0.762771] uhci_hcd 0000:00:1a.0: irq 20, io base 0x000060c0
Dec 21 00:38:18 MacBuntu kernel: [    0.762873] hub 3-0:1.0: USB hub found
Dec 21 00:38:18 MacBuntu kernel: [    0.762877] hub 3-0:1.0: 2 ports detected
Dec 21 00:38:18 MacBuntu kernel: [    0.762926] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec 21 00:38:18 MacBuntu kernel: [    0.762931] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.762934] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 21 00:38:18 MacBuntu kernel: [    0.762967] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Dec 21 00:38:18 MacBuntu kernel: [    0.763005] uhci_hcd 0000:00:1a.1: irq 16, io base 0x000060a0
Dec 21 00:38:18 MacBuntu kernel: [    0.763108] hub 4-0:1.0: USB hub found
Dec 21 00:38:18 MacBuntu kernel: [    0.763111] hub 4-0:1.0: 2 ports detected
Dec 21 00:38:18 MacBuntu kernel: [    0.763168] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 00:38:18 MacBuntu kernel: [    0.763176] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.763179] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 21 00:38:18 MacBuntu kernel: [    0.763204] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Dec 21 00:38:18 MacBuntu kernel: [    0.763231] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
Dec 21 00:38:18 MacBuntu kernel: [    0.763324] hub 5-0:1.0: USB hub found
Dec 21 00:38:18 MacBuntu kernel: [    0.763327] hub 5-0:1.0: 2 ports detected
Dec 21 00:38:18 MacBuntu kernel: [    0.763379] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Dec 21 00:38:18 MacBuntu kernel: [    0.763384] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.763387] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 21 00:38:18 MacBuntu kernel: [    0.763415] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Dec 21 00:38:18 MacBuntu kernel: [    0.763450] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00006060
Dec 21 00:38:18 MacBuntu kernel: [    0.763547] hub 6-0:1.0: USB hub found
Dec 21 00:38:18 MacBuntu kernel: [    0.763550] hub 6-0:1.0: 2 ports detected
Dec 21 00:38:18 MacBuntu kernel: [    0.763603] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Dec 21 00:38:18 MacBuntu kernel: [    0.763609] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    0.763612] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 21 00:38:18 MacBuntu kernel: [    0.763638] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Dec 21 00:38:18 MacBuntu kernel: [    0.763665] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006040
Dec 21 00:38:18 MacBuntu kernel: [    0.763771] hub 7-0:1.0: USB hub found
Dec 21 00:38:18 MacBuntu kernel: [    0.763774] hub 7-0:1.0: 2 ports detected
Dec 21 00:38:18 MacBuntu kernel: [    0.763863] PNP: No PS/2 controller found. Probing ports directly.
Dec 21 00:38:18 MacBuntu kernel: [    0.764722] i8042.c: No controller found.
Dec 21 00:38:18 MacBuntu kernel: [    0.764765] mice: PS/2 mouse device common for all mice
Dec 21 00:38:18 MacBuntu kernel: [    0.764891] rtc_cmos 00:08: RTC can wake from S4
Dec 21 00:38:18 MacBuntu kernel: [    0.764922] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Dec 21 00:38:18 MacBuntu kernel: [    0.764954] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Dec 21 00:38:18 MacBuntu kernel: [    0.765024] device-mapper: uevent: version 1.0.3
Dec 21 00:38:18 MacBuntu kernel: [    0.765099] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Dec 21 00:38:18 MacBuntu kernel: [    0.765157] device-mapper: multipath: version 1.1.1 loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.765160] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 21 00:38:18 MacBuntu kernel: [    0.765335] cpuidle: using governor ladder
Dec 21 00:38:18 MacBuntu kernel: [    1.791208] cpuidle: using governor menu
Dec 21 00:38:18 MacBuntu kernel: [    1.810351] EFI Variables Facility v0.08 2004-May-17
Dec 21 00:38:18 MacBuntu kernel: [    1.810379] ata1.00: ATAPI: HL-DT-ST DVDRW  GSA-S10N, AP09, max UDMA/33
Dec 21 00:38:18 MacBuntu kernel: [    1.871257] ata1.00: configured for UDMA/33
Dec 21 00:38:18 MacBuntu kernel: [    1.895335] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRW  GSA-S10N  AP09 PQ: 0 ANSI: 5
Dec 21 00:38:18 MacBuntu kernel: [    1.924678] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
Dec 21 00:38:18 MacBuntu kernel: [    1.937573] TCP cubic registered
Dec 21 00:38:18 MacBuntu kernel: [    1.937672] NET: Registered protocol family 10
Dec 21 00:38:18 MacBuntu kernel: [    1.937959] lo: Disabled Privacy Extensions
Dec 21 00:38:18 MacBuntu kernel: [    1.938116] NET: Registered protocol family 17
Dec 21 00:38:18 MacBuntu kernel: [    2.023266] Uniform CD-ROM driver Revision: 3.20
Dec 21 00:38:18 MacBuntu kernel: [    2.043292] sr 0:0:0:0: Attached scsi CD-ROM sr0
Dec 21 00:38:18 MacBuntu kernel: [    2.043340] sr 0:0:0:0: Attached scsi generic sg0 type 5
Dec 21 00:38:18 MacBuntu kernel: [    2.043389] PM: Resume from disk failed.
Dec 21 00:38:18 MacBuntu kernel: [    2.043400] registered taskstats version 1
Dec 21 00:38:18 MacBuntu kernel: [    2.043862]   Magic number: 6:723:618
Dec 21 00:38:18 MacBuntu kernel: [    2.102902] rtc_cmos 00:08: setting system clock to 2010-12-21 05:38:10 UTC (1292909890)
Dec 21 00:38:18 MacBuntu kernel: [    2.123133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 21 00:38:18 MacBuntu kernel: [    2.143455] EDD information not available.
Dec 21 00:38:18 MacBuntu kernel: [    2.163969] Freeing unused kernel memory: 908k freed
Dec 21 00:38:18 MacBuntu kernel: [    2.184586] Write protecting the kernel read-only data: 10240k
Dec 21 00:38:18 MacBuntu kernel: [    2.205206] Freeing unused kernel memory: 416k freed
Dec 21 00:38:18 MacBuntu kernel: [    2.225867] usb 2-4: new high speed USB device using ehci_hcd and address 2
Dec 21 00:38:18 MacBuntu kernel: [    2.246829] Freeing unused kernel memory: 1644k freed
Dec 21 00:38:18 MacBuntu kernel: [    2.302491] udev[86]: starting version 163
Dec 21 00:38:18 MacBuntu kernel: [    2.389970] ahci 0000:00:1f.2: version 3.0
Dec 21 00:38:18 MacBuntu kernel: [    2.389990] ahci 0000:00:1f.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Dec 21 00:38:18 MacBuntu kernel: [    2.390037]   alloc irq_desc for 45 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    2.390038]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    2.390052] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
Dec 21 00:38:18 MacBuntu kernel: [    2.390108] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
Dec 21 00:38:18 MacBuntu kernel: [    2.390111] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
Dec 21 00:38:18 MacBuntu kernel: [    2.390116] ahci 0000:00:1f.2: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    2.410153] sky2: driver version 1.28
Dec 21 00:38:18 MacBuntu kernel: [    2.410257] sky2 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 21 00:38:18 MacBuntu kernel: [    2.410304] sky2 0000:0c:00.0: setting latency timer to 64
Dec 21 00:38:18 MacBuntu kernel: [    2.410403] sky2 0000:0c:00.0: Yukon-2 EC Ultra chip revision 3
Dec 21 00:38:18 MacBuntu kernel: [    2.410951]   alloc irq_desc for 46 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    2.410953]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    2.411026] sky2 0000:0c:00.0: irq 46 for MSI/MSI-X
Dec 21 00:38:18 MacBuntu kernel: [    2.437039]   alloc irq_desc for 19 on node -1
Dec 21 00:38:18 MacBuntu kernel: [    2.437041]   alloc kstat_irqs on node -1
Dec 21 00:38:18 MacBuntu kernel: [    2.437049] firewire_ohci 0000:0d:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 21 00:38:18 MacBuntu kernel: [    2.459498] scsi2 : ahci
Dec 21 00:38:18 MacBuntu kernel: [    2.459631] scsi3 : ahci
Dec 21 00:38:18 MacBuntu kernel: [    2.459720] scsi4 : ahci
Dec 21 00:38:18 MacBuntu kernel: [    2.459796] ata3: SATA max UDMA/133 abar m2048@0x9b504000 port 0x9b504100 irq 45
Dec 21 00:38:18 MacBuntu kernel: [    2.459798] ata4: DUMMY
Dec 21 00:38:18 MacBuntu kernel: [    2.459800] ata5: DUMMY
Dec 21 00:38:18 MacBuntu kernel: [    2.469562] sky2 0000:0c:00.0: eth0: addr 00:1b:63:b8:63:f0
Dec 21 00:38:18 MacBuntu kernel: [    2.802583] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 21 00:38:18 MacBuntu kernel: [    2.824957] firewire_ohci: Added fw-ohci device 0000:0d:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Dec 21 00:38:18 MacBuntu kernel: [    2.930212] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Dec 21 00:38:18 MacBuntu kernel: [    2.953710] ata3.00: ATA-8: WDC WD3200BEKT-00F3T0, 11.01A11, max UDMA/133
Dec 21 00:38:18 MacBuntu kernel: [    2.977083] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Dec 21 00:38:18 MacBuntu kernel: [    3.140277] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Dec 21 00:38:18 MacBuntu kernel: [    3.164009] ata3.00: configured for UDMA/133
Dec 21 00:38:18 MacBuntu kernel: [    3.187482] usb 3-1: new full speed USB device using uhci_hcd and address 2
Dec 21 00:38:18 MacBuntu kernel: [    3.211444] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-0 11.0 PQ: 0 ANSI: 5
Dec 21 00:38:18 MacBuntu kernel: [    3.235636] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Dec 21 00:38:18 MacBuntu kernel: [    3.235674] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec 21 00:38:18 MacBuntu kernel: [    3.283522] sd 2:0:0:0: [sda] Write Protect is off
Dec 21 00:38:18 MacBuntu kernel: [    3.307038] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 21 00:38:18 MacBuntu kernel: [    3.307057] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 21 00:38:18 MacBuntu kernel: [    3.331219] firewire_core: created device fw0: GUID 001e52fffe4594f8, S800
Dec 21 00:38:18 MacBuntu kernel: [    3.331258]  sda: sda1 sda2 sda3 sda4 sda5
Dec 21 00:38:18 MacBuntu kernel: [    3.421118] sd 2:0:0:0: [sda] Attached SCSI disk
Dec 21 00:38:18 MacBuntu kernel: [    3.466478] usbcore: registered new interface driver hiddev
Dec 21 00:38:18 MacBuntu kernel: [    3.508162] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input4
Dec 21 00:38:18 MacBuntu kernel: [    3.533174] generic-usb 0003:05AC:1000.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0000:00:1a.0-1/input0
Dec 21 00:38:18 MacBuntu kernel: [    3.573239] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input5
Dec 21 00:38:18 MacBuntu kernel: [    3.598961] generic-usb 0003:05AC:1000.0002: input,hidraw1: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0000:00:1a.0-1/input1
Dec 21 00:38:18 MacBuntu kernel: [    3.625162] usbcore: registered new interface driver usbhid
Dec 21 00:38:18 MacBuntu kernel: [    3.651429] usbhid: USB HID core driver
Dec 21 00:38:18 MacBuntu kernel: [    3.772556] usb 7-1: new low speed USB device using uhci_hcd and address 2
Dec 21 00:38:18 MacBuntu kernel: [    4.028869] apple 0003:05AC:8242.0003: hiddev96,hidraw2: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-1/input0
Dec 21 00:38:18 MacBuntu kernel: [    4.085928] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
Dec 21 00:38:18 MacBuntu kernel: [    4.320057] usb 7-2: new full speed USB device using uhci_hcd and address 3
Dec 21 00:38:18 MacBuntu kernel: [    4.546089] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input6
Dec 21 00:38:18 MacBuntu kernel: [    4.575483] apple 0003:05AC:021A.0004: input,hidraw3: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Dec 21 00:38:18 MacBuntu kernel: [    4.613806] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input7
Dec 21 00:38:18 MacBuntu kernel: [    4.644721] apple 0003:05AC:021A.0005: input,hidraw4: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input2
Dec 21 00:38:18 MacBuntu kernel: [    9.291457] udev[387]: starting version 163
Dec 21 00:38:18 MacBuntu kernel: [    9.327632] lp: driver loaded but no devices found
Dec 21 00:38:18 MacBuntu kernel: [    9.338952] Adding 2142204k swap on /dev/sda5.  Priority:-1 extents:1 across:2142204k 
Dec 21 00:38:18 MacBuntu kernel: [    9.383418] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input8
Dec 21 00:38:18 MacBuntu kernel: [    9.383515] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 21 00:38:18 MacBuntu kernel: [    9.707599] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
Dec 21 00:38:18 MacBuntu kernel: [    9.909624] type=1400 audit(1292909898.356:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=630 comm="apparmor_parser"
Dec 21 00:38:18 MacBuntu kernel: [    9.910359] type=1400 audit(1292909898.356:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
Dec 21 00:38:18 MacBuntu kernel: [    9.910665] type=1400 audit(1292909898.356:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=630 comm="apparmor_parser"
Dec 21 00:38:18 MacBuntu kernel: [    9.999330] sky2 0000:0c:00.0: eth0: enabling interface
Dec 21 00:38:18 MacBuntu kernel: [    9.999578] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 21 00:38:19 MacBuntu kernel: [   10.610342] ACPI: Battery Slot [BAT0] (battery present)
Dec 21 00:38:20 MacBuntu kernel: [   11.681874] sky2 0000:0c:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
Dec 21 00:38:20 MacBuntu kernel: [   11.682087] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 21 00:38:21 MacBuntu kernel: [   12.606456] mbp_nvidia_bl: MacBookPro 3,1 detected
Dec 21 00:38:21 MacBuntu kernel: [   12.612698] applesmc: Apple MacBook Pro 3 detected:
Dec 21 00:38:21 MacBuntu kernel: [   12.612700] applesmc:  - Model with accelerometer
Dec 21 00:38:21 MacBuntu kernel: [   12.612701] applesmc:  - Model with light sensors and backlight
Dec 21 00:38:21 MacBuntu kernel: [   12.612703] applesmc:  - Model with 13 temperature sensors
Dec 21 00:38:21 MacBuntu kernel: [   12.697631] applesmc: device successfully initialized (0xe0, 0x00).
Dec 21 00:38:21 MacBuntu kernel: [   12.697634] applesmc: device successfully initialized.
Dec 21 00:38:21 MacBuntu kernel: [   12.698183] applesmc: 2 fans found.
Dec 21 00:38:21 MacBuntu kernel: [   12.698331] appletouch: Geyser mode initialized.
Dec 21 00:38:21 MacBuntu kernel: [   12.801308] cfg80211: Calling CRDA to update world regulatory domain
Dec 21 00:38:21 MacBuntu kernel: [   12.803353] input: appletouch as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input9
Dec 21 00:38:21 MacBuntu kernel: [   12.803475] usbcore: registered new interface driver appletouch
Dec 21 00:38:21 MacBuntu kernel: [   12.803903] Linux video capture interface: v2.00
Dec 21 00:38:21 MacBuntu kernel: [   12.806317] input: applesmc as /devices/platform/applesmc.768/input/input10
Dec 21 00:38:21 MacBuntu kernel: [   12.815434] Registered led device: smc::kbd_backlight
Dec 21 00:38:21 MacBuntu kernel: [   12.815453] applesmc: driver successfully loaded.
Dec 21 00:38:21 MacBuntu kernel: [   12.819285] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8502)
Dec 21 00:38:21 MacBuntu kernel: [   12.823643] input: Built-in iSight as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input11
Dec 21 00:38:21 MacBuntu kernel: [   12.823949] usbcore: registered new interface driver uvcvideo
Dec 21 00:38:21 MacBuntu kernel: [   12.823951] USB Video Class driver (v0.1.0)
Dec 21 00:38:21 MacBuntu kernel: [   12.833460] cfg80211: World regulatory domain updated:
Dec 21 00:38:21 MacBuntu kernel: [   12.833463]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 21 00:38:21 MacBuntu kernel: [   12.833465]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 21 00:38:21 MacBuntu kernel: [   12.833468]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 21 00:38:21 MacBuntu kernel: [   12.833470]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 21 00:38:21 MacBuntu kernel: [   12.833472]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 21 00:38:21 MacBuntu kernel: [   12.833475]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 21 00:38:21 MacBuntu kernel: [   12.863556] ath9k 0000:0b:00.0: enabling device (0000 -> 0002)
Dec 21 00:38:21 MacBuntu kernel: [   12.863565] ath9k 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 00:38:21 MacBuntu kernel: [   12.863579] ath9k 0000:0b:00.0: setting latency timer to 64
Dec 21 00:38:21 MacBuntu kernel: [   12.989510] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
Dec 21 00:38:21 MacBuntu kernel: [   12.989518] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 21 00:38:21 MacBuntu kernel: [   12.989580]   alloc irq_desc for 47 on node -1
Dec 21 00:38:21 MacBuntu kernel: [   12.989582]   alloc kstat_irqs on node -1
Dec 21 00:38:21 MacBuntu kernel: [   12.989596] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Dec 21 00:38:21 MacBuntu kernel: [   12.989633] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 21 00:38:21 MacBuntu kernel: [   13.000160] ath: EEPROM regdomain: 0x64
Dec 21 00:38:21 MacBuntu kernel: [   13.000162] ath: EEPROM indicates we should expect a direct regpair map
Dec 21 00:38:21 MacBuntu kernel: [   13.000166] ath: Country alpha2 being used: 00
Dec 21 00:38:21 MacBuntu kernel: [   13.000167] ath: Regpair used: 0x64
Dec 21 00:38:21 MacBuntu kernel: [   13.006853] phy0: Selected rate control algorithm 'ath9k_rate_control'
Dec 21 00:38:21 MacBuntu kernel: [   13.007338] Registered led device: ath9k-phy0::radio
Dec 21 00:38:21 MacBuntu kernel: [   13.007355] Registered led device: ath9k-phy0::assoc
Dec 21 00:38:21 MacBuntu kernel: [   13.007369] Registered led device: ath9k-phy0::tx
Dec 21 00:38:21 MacBuntu kernel: [   13.007383] Registered led device: ath9k-phy0::rx
Dec 21 00:38:21 MacBuntu kernel: [   13.007387] phy0: Atheros AR5418 MAC/BB Rev:2 AR5133 RF Rev:81 mem=0xffffc90005f80000, irq=16
Dec 21 00:38:21 MacBuntu kernel: [   13.035959] type=1400 audit(1292909901.486:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=902 comm="apparmor_parser"
Dec 21 00:38:21 MacBuntu kernel: [   13.036566] type=1400 audit(1292909901.486:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=902 comm="apparmor_parser"
Dec 21 00:38:21 MacBuntu kernel: [   13.036898] type=1400 audit(1292909901.486:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=902 comm="apparmor_parser"
Dec 21 00:38:21 MacBuntu kernel: [   13.038177] nvidia: module license 'NVIDIA' taints kernel.
Dec 21 00:38:21 MacBuntu kernel: [   13.038180] Disabling lock debugging due to kernel taint
Dec 21 00:38:21 MacBuntu kernel: [   13.091096] hda_codec: ALC889A: SKU not ready 0x400000f0
Dec 21 00:38:21 MacBuntu kernel: [   13.152820] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -84
Dec 21 00:38:21 MacBuntu kernel: [   13.498203] type=1400 audit(1292909901.946:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=901 comm="apparmor_parser"
Dec 21 00:38:21 MacBuntu kernel: [   13.503128] usb 3-1: USB disconnect, address 2
Dec 21 00:38:21 MacBuntu kernel: [   13.531896] type=1400 audit(1292909901.976:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=927 comm="apparmor_parser"
Dec 21 00:38:21 MacBuntu kernel: [   13.532672] type=1400 audit(1292909901.986:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=927 comm="apparmor_parser"
Dec 21 00:38:22 MacBuntu kernel: [   13.579890] type=1400 audit(1292909902.026:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=928 comm="apparmor_parser"
Dec 21 00:38:22 MacBuntu kernel: [   13.689901] applesmc: wait status failed: 5 != 0
Dec 21 00:38:22 MacBuntu kernel: [   13.753903] nvidia 0000:01:00.0: enabling device (0002 -> 0003)
Dec 21 00:38:22 MacBuntu kernel: [   13.753912] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 00:38:22 MacBuntu kernel: [   13.753923] nvidia 0000:01:00.0: setting latency timer to 64
Dec 21 00:38:22 MacBuntu kernel: [   13.753928] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Dec 21 00:38:22 MacBuntu kernel: [   13.755199] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.29  Wed Dec  8 12:08:56 PST 2010
Dec 21 00:38:22 MacBuntu kernel: [   14.132552] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec 21 00:38:22 MacBuntu kernel: [   14.340881] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 21 00:38:22 MacBuntu kernel: [   14.347984] Bluetooth: Core ver 2.15
Dec 21 00:38:22 MacBuntu kernel: [   14.348008] NET: Registered protocol family 31
Dec 21 00:38:22 MacBuntu kernel: [   14.348009] Bluetooth: HCI device and connection manager initialized
Dec 21 00:38:22 MacBuntu kernel: [   14.348011] Bluetooth: HCI socket layer initialized
Dec 21 00:38:22 MacBuntu kernel: [   14.351533] Bluetooth: Generic Bluetooth USB driver ver 0.6
Dec 21 00:38:22 MacBuntu kernel: [   14.352168] usbcore: registered new interface driver btusb
Dec 21 00:38:22 MacBuntu kernel: [   14.376297] ppdev: user-space parallel port driver
Dec 21 00:38:22 MacBuntu kernel: [   14.401593] Bluetooth: L2CAP ver 2.14
Dec 21 00:38:22 MacBuntu kernel: [   14.401596] Bluetooth: L2CAP socket layer initialized
Dec 21 00:38:22 MacBuntu kernel: [   14.408085] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 21 00:38:22 MacBuntu kernel: [   14.408088] Bluetooth: BNEP filters: protocol multicast
Dec 21 00:38:22 MacBuntu kernel: [   14.411460] Bluetooth: SCO (Voice Link) ver 0.6
Dec 21 00:38:22 MacBuntu kernel: [   14.411462] Bluetooth: SCO socket layer initialized
Dec 21 00:38:23 MacBuntu kernel: [   14.678525] Bluetooth: RFCOMM TTY layer initialized
Dec 21 00:38:23 MacBuntu kernel: [   14.678530] Bluetooth: RFCOMM socket layer initialized
Dec 21 00:38:23 MacBuntu kernel: [   14.678531] Bluetooth: RFCOMM ver 1.11
Dec 21 00:38:25 MacBuntu kernel: [   16.460810] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
Dec 21 00:38:26 MacBuntu kernel: [   17.010499] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:26 MacBuntu kernel: [   17.013367] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:26 MacBuntu kernel: [   17.013372] NVRM: rm_init_adapter(0) failed
Dec 21 00:38:26 MacBuntu kernel: [   17.309829] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:26 MacBuntu kernel: [   17.312699] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:26 MacBuntu kernel: [   17.312705] NVRM: rm_init_adapter(0) failed
Dec 21 00:38:26 MacBuntu kernel: [   17.585008] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:26 MacBuntu kernel: [   17.587874] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:26 MacBuntu kernel: [   17.587880] NVRM: rm_init_adapter(0) failed
Dec 21 00:38:27 MacBuntu kernel: [   17.859841] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:27 MacBuntu kernel: [   17.863069] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:27 MacBuntu kernel: [   17.863075] NVRM: rm_init_adapter(0) failed
Dec 21 00:38:27 MacBuntu kernel: [   18.134833] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:27 MacBuntu kernel: [   18.137699] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:27 MacBuntu kernel: [   18.137704] NVRM: rm_init_adapter(0) failed
Dec 21 00:38:27 MacBuntu kernel: [   18.409508] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:27 MacBuntu kernel: [   18.412380] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:27 MacBuntu kernel: [   18.412385] NVRM: rm_init_adapter(0) failed
Dec 21 00:38:31 MacBuntu kernel: [   21.900121] eth0: no IPv6 routers present
Dec 21 00:38:42 MacBuntu kernel: [   33.710840] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:42 MacBuntu kernel: [   33.713720] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:42 MacBuntu kernel: [   33.713726] NVRM: rm_init_adapter(0) failed
 

```

---

### Post by metatechbe on 2010-12-21
> **a.ross.cohen said:**
> Here is my kern.log. Sorry it took me so long to get it up here but I've been moving.
By the way I tried that other xorg.conf configuration and it didn't fix the problem.

```

Dec 21 00:38:26 MacBuntu kernel: [   17.010499] NVRM: failed to copy vbios to system memory.
Dec 21 00:38:26 MacBuntu kernel: [   17.013367] NVRM: RmInitAdapter failed! (0x30:0xffffffff:821)
Dec 21 00:38:26 MacBuntu kernel: [   17.013372] NVRM: rm_init_adapter(0) failed
 

```

Hello, have you tried the "nopat" kernel parameter ?
[http://ubuntuforums.org/showpost.php?p=10156587&postcount=1184](http://ubuntuforums.org/showpost.php?p=10156587&postcount=1184)

Regards,

metatech

---

