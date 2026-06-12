---
title: "ATI 9800 Pro driver problem"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by caravel on 2007-09-16
Hi, I have Feisty Fawn installed on my old PC (which also happens to be my only PC) which is a Athlon XP 2400+, 1GB RAM, with an ATI Radeon 9800 Pro 128MB AGP.  I'd finally had enough of vegetating with XP and decided to give Ubuntu another try.

I've been struggling with the ATI Proprietary driver for hours, and I was wondering if any one of the wise users here that have given me much help in the past could provide any input?  So far I've followed the [Wiki](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) to the letter.  About 2 weeks ago I tried to get fglrx working and X fails to initialize.  There is nothing but a black screen and my monitor appears to go to sleep.  Today I tried the ATI proprietary driver, following the same guide and still no good.  There were no errors or anything out of the ordinary except in the part where the symbolic links have to be created.  This gives an error that the folders and files already exist.

I have gotten the driver working before under Dapper with my old Radeon 9000Pro, but with Feisty and the 9800 I'm having no luck at all and have to keep booting into recovery mode, and editing xorg.conf changing it from "fglrx" back to "ati" just to get X working again.

Any help would be greatly appreciated, thanks in advance. :)

Edit: I almost forgot, I also tried enabling fglrx that comes with Ubuntu via the Restricted Drivers Manager and that had exactly the same result - monitor goes to sleep.

---

### Post by w4ett on 2007-09-16
You might want to give Envy a try:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

most folks have better luck running it from the terminal like this:

```
sudo envy -t
```

Good luck

---

### Post by caravel on 2007-09-16
Thanks for the reply **w4ett**,

I've installed it, done sudo envy -t in the terminal and it has installed the proprietary ATI driver.  I can see it in the restricted drivers.  After installation it rebooted and unfortunately the same problem returned.  I had to remove /etc/X11/xorg.conf and restore the backup file.  I'm now back again with the "ati" driver, and when I check restricted drivers it says the ATI proprietary driver is installed but disabled - I expect this is because I've disabled it.  I'm pretty much at a loss as to what to do.  Is there any log file I can find and post up here that may show what is happening when the monitor goes to sleep and X fails to start?

Thanks again.

Caravel

---

### Post by w4ett on 2007-09-16
It's in:
```
/var/log/Xorg.0.log
```

---

### Post by caravel on 2007-09-17
**w4ett**,

Thanks for the reply, these are the two logs I've found.  I hope you can make some sense of them, because I can't tell which are errors that are something to worry about and which are not.  I can't find any reference to fglrx in these files so I'm hoping they're the correct ones.

Thanks again.

Caravel

Xorg.0.log.old
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux thecaravel 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 16 22:47:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3099 card 1106,3099 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 1317,0985 card 1317,0574 rev 11 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 1106,3147 card 1106,3147 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1458,a002 rev 40 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e48 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e68 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfc00000 - 0xdfcfffff (0x20100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] rev 0, Mem @ 0xd0000000/27, 0xdfef0000/16, I/O @ 0xb800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) rev 0, Mem @ 0xc8000000/27, 0xdfee0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[3] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[3] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) ATI: ATI driver (version 6.6.3) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]".
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9800PRO NH (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xdfef0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): Assuming overlay scaler buffer width is 1536
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9800PRO NH (AGP)" (ChipID = 0x4e48)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(--) RADEON(0): BIOS at 0xdfec0000
(II) RADEON(0): AGP card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Generation 1 PCI interface in multifunction mode, accessible memory limited to one aperture
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (256 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): VBE DDC probing on port 1 ::: 
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): VESA BIOS detected
(II) RADEON(0): VESA VBE Version 2.0
(II) RADEON(0): VESA VBE Total Mem: 131072 kB
(II) RADEON(0): VESA VBE OEM: ATI R350
(II) RADEON(0): VESA VBE OEM Software Rev: 1.0
(II) RADEON(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) RADEON(0): VESA VBE OEM Product: R350
(II) RADEON(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) RADEON(0): VESA VBE DDC supported
(II) RADEON(0): VESA VBE DDC Level 2
(II) RADEON(0): VESA VBE DDC transfer in appr. 2 sec.
(II) RADEON(0): VESA VBE DDC read successfully
(II) RADEON(0): DDC info nullified on port 1 :::
(II) RADEON(0): Analog device indicated in DDC but port 2 CRT physically connected
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: MAX  Model: 7e4  Serial#: 808662329
(II) RADEON(0): Year: 2000  Week: 46
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 26  vert.: 20
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.643 redY: 0.324   greenX: 0.301 greenY: 0.606
(II) RADEON(0): blueX: 0.142 blueY: 0.056   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 640  h_sync: 1312  h_sync_end 1344 h_blank_end 832 h_border: 0
(II) RADEON(0): v_active: 400  v_sync: 417  v_sync_end 420 v_blanking: 445 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 35.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 720  h_sync: 1476  h_sync_end 1512 h_blank_end 936 h_border: 0
(II) RADEON(0): v_active: 400  v_sync: 417  v_sync_end 420 v_blanking: 446 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 640  h_sync: 1296  h_sync_end 1360 h_blank_end 840 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 513  v_sync_end 516 v_blanking: 500 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 640  h_sync: 1296  h_sync_end 1360 h_blank_end 840 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 513  v_sync_end 516 v_blanking: 500 v_border: 0
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff003438e40739353330
(II) RADEON(0): 	2e0a0101081a14b9e88152a4534d9b24
(II) RADEON(0): 	0e484f27d80045593159615901010101
(II) RADEON(0): 	0101010101014e0c80c020902d10a020
(II) RADEON(0): 	138404c31000001ade0dd0d820902e10
(II) RADEON(0): 	f424138404c31000001c4e0c80c820e0
(II) RADEON(0): 	14109040138804c3100000184e0c80c8
(II) RADEON(0): 	20e014109040138804c3100000180035
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=32400
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) RADEON(0): Generic Monitor: Using vrefresh range of 50.00-120.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) RADEON(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RADEON(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) RADEON(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) RADEON(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RADEON(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) RADEON(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) RADEON(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) RADEON(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) RADEON(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) RADEON(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) RADEON(0): Display dimensions: (260, 200) mm
(--) RADEON(0): DPI set to (100, 97)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[11] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[16] 0	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit d0000000 0
(**) RADEON(0): Map: 0xd0000000, 0x08000000
(==) RADEON(0): Write-combining range (0xd0000000,0x8000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81f4b90)
(**) RADEON(0): Read: 0x0030000c 0x00030065 0x00000000
(**) RADEON(0): Read: rd=12, fd=101, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81f4b90
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1024x768       94.50  1024 1072 1168 1376   768  769  772  808 (24,32) +H +V
1024x768       94.50  1024 1072 1168 1376   768  769  772  808 (24,32) +H +V
(**) RADEON(0): Pitch = 8388736 bytes (virtualX = 1024, displayWidth = 1024)
(**) RADEON(0): dc=9450, of=37800, fd=168, pd=4
(**) RADEON(0): RADEONInit returns 0x81f5540
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f5540)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x000200a8 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=168, pd=2
(**) RADEON(0): GRPH_BUFFER_CNTL from 20204c4c to 20147c6c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 128
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(WW) RADEON(0): Option "VideoOverlay" is not used
(WW) RADEON(0): Option "OpenGLOverlay" is not used
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONCloseScreen
(**) RADEON(0): RADEONDRIStop
(**) RADEON(0): RADEONDisplayPowerManagementSet(0,0x0)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f4b90)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0030000c 0x00030065 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=101, pd=3
(**) RADEON(0): Disposing accel...
(**) RADEON(0): Disposing cusor info
(**) RADEON(0): Disposing DGA
(**) RADEON(0): Unmapping memory
```

Xorg.0.log
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux thecaravel 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 17 21:57:38 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3099 card 1106,3099 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 1317,0985 card 1317,0574 rev 11 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 1106,3147 card 1106,3147 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1458,a002 rev 40 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e48 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e68 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfc00000 - 0xdfcfffff (0x20100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] rev 0, Mem @ 0xd0000000/27, 0xdfef0000/16, I/O @ 0xb800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) rev 0, Mem @ 0xc8000000/27, 0xdfee0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[3] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[3] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) ATI: ATI driver (version 6.6.3) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]".
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9800PRO NH (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xdfef0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): Assuming overlay scaler buffer width is 1536
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9800PRO NH (AGP)" (ChipID = 0x4e48)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(--) RADEON(0): BIOS at 0xdfec0000
(II) RADEON(0): AGP card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.25.0
(II) RADEON(0): AGP Fast Write disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEON(0): Page flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 1 PCI interface in multifunction mode, accessible memory limited to one aperture
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (256 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): VBE DDC probing on port 1 ::: 
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): VESA BIOS detected
(II) RADEON(0): VESA VBE Version 2.0
(II) RADEON(0): VESA VBE Total Mem: 131072 kB
(II) RADEON(0): VESA VBE OEM: ATI R350
(II) RADEON(0): VESA VBE OEM Software Rev: 1.0
(II) RADEON(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) RADEON(0): VESA VBE OEM Product: R350
(II) RADEON(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) RADEON(0): VESA VBE DDC supported
(II) RADEON(0): VESA VBE DDC Level 2
(II) RADEON(0): VESA VBE DDC transfer in appr. 2 sec.
(II) RADEON(0): VESA VBE DDC read successfully
(II) RADEON(0): DDC info nullified on port 1 :::
(II) RADEON(0): Analog device indicated in DDC but port 2 CRT physically connected
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: MAX  Model: 7e4  Serial#: 808662329
(II) RADEON(0): Year: 2000  Week: 46
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 26  vert.: 20
(II) RADEON(0): Gamma: 2.85
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.643 redY: 0.324   greenX: 0.301 greenY: 0.606
(II) RADEON(0): blueX: 0.142 blueY: 0.056   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 640  h_sync: 1312  h_sync_end 1344 h_blank_end 832 h_border: 0
(II) RADEON(0): v_active: 400  v_sync: 417  v_sync_end 420 v_blanking: 445 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 35.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 720  h_sync: 1476  h_sync_end 1512 h_blank_end 936 h_border: 0
(II) RADEON(0): v_active: 400  v_sync: 417  v_sync_end 420 v_blanking: 446 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 640  h_sync: 1296  h_sync_end 1360 h_blank_end 840 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 513  v_sync_end 516 v_blanking: 500 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 640  h_sync: 1296  h_sync_end 1360 h_blank_end 840 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 513  v_sync_end 516 v_blanking: 500 v_border: 0
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff003438e40739353330
(II) RADEON(0): 	2e0a0101081a14b9e88152a4534d9b24
(II) RADEON(0): 	0e484f27d80045593159615901010101
(II) RADEON(0): 	0101010101014e0c80c020902d10a020
(II) RADEON(0): 	138404c31000001ade0dd0d820902e10
(II) RADEON(0): 	f424138404c31000001c4e0c80c820e0
(II) RADEON(0): 	14109040138804c3100000184e0c80c8
(II) RADEON(0): 	20e014109040138804c3100000180035
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=32400
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) RADEON(0): Generic Monitor: Using vrefresh range of 50.00-120.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) RADEON(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RADEON(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) RADEON(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) RADEON(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RADEON(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) RADEON(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) RADEON(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) RADEON(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) RADEON(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) RADEON(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) RADEON(0): Display dimensions: (260, 200) mm
(--) RADEON(0): DPI set to (100, 97)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[11] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[16] 0	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit d0000000 0
(**) RADEON(0): Map: 0xd0000000, 0x08000000
(==) RADEON(0): Write-combining range (0xd0000000,0x8000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81f4b90)
(**) RADEON(0): Read: 0x0030000c 0x00030065 0x00000000
(**) RADEON(0): Read: rd=12, fd=101, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81f4b90
(==) RADEON(0): Using 24 bit depth buffer
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf8d0e000
(II) RADEON(0): [drm] mapped SAREA 0xf8d0e000 to 0xb7cbe000
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x3099; Card 0x1002/0x4e48]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xaf8cc000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xaf8cb000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaf6cb000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xaf1eb000
(II) RADEON(0): [drm] register handle = 0xdfef0000
(II) RADEON(0): [dri] Visual configs initialized
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1024x768       94.50  1024 1072 1168 1376   768  769  772  808 (24,32) +H +V
1024x768       94.50  1024 1072 1168 1376   768  769  772  808 (24,32) +H +V
(**) RADEON(0): Pitch = 8388736 bytes (virtualX = 1024, displayWidth = 1024)
(**) RADEON(0): dc=9450, of=37800, fd=168, pd=4
(**) RADEON(0): RADEONInit returns 0x81f5540
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f5540)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x000200a8 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=168, pd=2
(**) RADEON(0): GRPH_BUFFER_CNTL from 20204c4c to 20157c6c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Will use back buffer at offset 0xc00000
(II) RADEON(0): Will use depth buffer at offset 0xf00000
(II) RADEON(0): Will use 112640 kb for textures at offset 0x1200000
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(**) RADEON(0): DRI Finishing init !
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xd7ffd000 is: 0xd7ffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(**) RADEON(0): GRPH_BUFFER_CNTL from 20204c4c to 20157c6c
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 128
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(WW) RADEON(0): Option "VideoOverlay" is not used
(WW) RADEON(0): Option "OpenGLOverlay" is not used
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
```

---

### Post by luptinpitman on 2007-09-17
Just taking a shot here, may or may not be of any help.

As a little background, I struggled with problem after problem for more than 6 months with a Radeon 9250 in everything from Dapper to Feisty so I know the hell you are dealing with.  I was trying to get WoW running on my ubuntu box and no matter what I did I never could seem to get it to work...

Replacing the ATI card with an nVidia 7xxx card solved every graphic problem I ever had (including Beryl), FYI.  (I didn't want to give up the good fight, but I finally caved and admitted defeat and it was the best decision I've made to date concerning linux).

Have you tried reconfiguring X from scratch after installing the proprietary drivers with ENVY?  Might help.  I looked at so many how-to's on ATI and ubuntu I went cross-eyed and deleted all of them :(

Check out:  [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

Basic info on how to reconfigure X.  Might help...

---

### Post by caravel on 2007-09-18
Replacing the card is not an option at the moment.

I haven't tried reconfiguring from scratch as yet, I'll enable the driver and try doing "dpkg-reconfigure xserver-xorg" now, I'd forgotten to try that.

Thanks

---

### Post by w4ett on 2007-09-18
> Thanks for the reply, these are the two logs I've found.  I hope you can make some sense of them, because I can't tell which are errors that are something to worry about and which are not.  I can't find any reference to fglrx in these files so I'm hoping they're the correct ones.

Thanks again.

Caravel


We.. the 2nd log looks ok to me...dri enabled and all check return a -7 which means an ok status (Unless I missed something-my eyes ARE getting old)...but it references the xorg-driver ati...not fglrx......as you said.

---

### Post by caravel on 2007-09-18
**luptinpitman**,

Reconfiguring the xserver didn't help.  I did try that in the past as well as the "aticonfig --initial" with Dapper and my old card and have never found it to work.

**w4ett**,

I suppose I need to enable the broken fglrx driver again reboot again and obtain a log from that?

Thanks again.

---

### Post by overdrank on 2007-09-18
> **caravel said:**
> **luptinpitman**,

Reconfiguring the xserver didn't help.  I did try that in the past as well as the "aticonfig --initial" with Dapper and my old card and have never found it to work.

**w4ett**,

I suppose I need to enable the broken fglrx driver again reboot again and obtain a log from that?

Thanks again.

HI if you care to try this "how to" has worked for me installing on ati from 7000 to 9600 cards.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Hope this helps and good luck! :)

---

### Post by w4ett on 2007-09-18
> **caravel said:**
> **luptinpitman**,

Reconfiguring the xserver didn't help.  I did try that in the past as well as the "aticonfig --initial" with Dapper and my old card and have never found it to work.

**w4ett**,

I suppose I need to enable the broken fglrx driver again reboot again and obtain a log from that?

Thanks again.

I would remove and purge the old fglrx driver and start from scratch...Remember tho...the newest 8.41 driver IS NOT compatible with your card.....hopefully the next release  in Oct (8.42) will...it's also supposed to support aiglx  For now, I'd use the driver included in the Restricted Driver Manager in Feisty until all the bugs get sorted out.

---

### Post by caravel on 2007-09-18
**w4ett**,

I've used the driver version 8.40.4-1 all along and not the later driver as I had heard that won't work.  I've also tried complete removal and reinstallation.  The restricted driver manager was the first method I tried this time around with the same result - xserver crashes.

Shall I try again and post up the log from that?

Thanks again.

---

### Post by w4ett on 2007-09-18
> **caravel said:**
> **w4ett**,

I've used the driver version 8.40.4-1 all along and not the later driver as I had heard that won't work.  I've also tried complete removal and reinstallation.  The restricted driver manager was the first method I tried this time around with the same result - xserver crashes.

Shall I try again and post up the log from that?

Thanks again.

Well....with as many attempts as have been made...at this point I'd start from scratch...I would also try using Envy:

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then run it from the terminal (most folks have better luck in non-gui mode)  from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to purge the old fglrx drivers and then  install the correct ATI  proprietary driver.

Good Luck

---

### Post by caravel on 2007-09-18
**w4ett** thank you for your continued patience,

I have already tried envy and done exactly as you described.  Sadly it had the same result.  I did purge the old driver first then installed the ATI proprietary driver with envy.  After which I edited xorg.conf to disable fglrx and restore the ati xorg driver.  When checking the restricted drivers it did say that I had the ATI Proprietary driver installed but disabled.  Enabling it again causes the same problem to return.

Thanks

Caravel

---

### Post by caravel on 2007-09-21
Ok I have tried Envy again.  I removed the driver, rebooted, reinstalled the ATI driver, and rebooted again.  Same problem, blank screen and crashed (CTRL+ALT+BKSP does nothing, trying to switch to any of the virtual consoles also does nothing, only hitting the reset button works).  This is the log:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux thecaravel 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 21 22:18:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3099 card 1106,3099 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 1317,0985 card 1317,0574 rev 11 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 1106,3147 card 1106,3147 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1458,a002 rev 40 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e48 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e68 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfc00000 - 0xdfcfffff (0x20100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] rev 0, Mem @ 0xd0000000/27, 0xdfef0000/16, I/O @ 0xb800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) rev 0, Mem @ 0xc8000000/27, 0xdfee0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[3] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[3] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.40.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.40.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.402                    
(II) ATI Proprietary Linux Driver Build Date: Jul 31 2007 22:20:14
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4E48) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6988
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[9] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B](B)
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "off"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9800 PRO" (Chipset = 0x4e48)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xdfef0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R350
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.40.4
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MAX  Model: 7e4  Serial#: 808662329
(II) fglrx(0): Year: 2000  Week: 46
(II) fglrx(0): EDID Version: 1.1
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 26  vert.: 20
(II) fglrx(0): Gamma: 2.85
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.643 redY: 0.324   greenX: 0.301 greenY: 0.606
(II) fglrx(0): blueX: 0.142 blueY: 0.056   whiteX: 0.281 whiteY: 0.311
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@87Hz (interlaced)
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) fglrx(0): h_active: 640  h_sync: 1312  h_sync_end 1344 h_blank_end 832 h_border: 0
(II) fglrx(0): v_active: 400  v_sync: 417  v_sync_end 420 v_blanking: 445 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 35.5 MHz   Image Size:  260 x 195 mm
(II) fglrx(0): h_active: 720  h_sync: 1476  h_sync_end 1512 h_blank_end 936 h_border: 0
(II) fglrx(0): v_active: 400  v_sync: 417  v_sync_end 420 v_blanking: 446 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) fglrx(0): h_active: 640  h_sync: 1296  h_sync_end 1360 h_blank_end 840 h_border: 0
(II) fglrx(0): v_active: 480  v_sync: 513  v_sync_end 516 v_blanking: 500 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 31.5 MHz   Image Size:  260 x 195 mm
(II) fglrx(0): h_active: 640  h_sync: 1296  h_sync_end 1360 h_blank_end 840 h_border: 0
(II) fglrx(0): v_active: 480  v_sync: 513  v_sync_end 516 v_blanking: 500 v_border: 0
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff003438e40739353330
(II) fglrx(0): 	2e0a0101081a14b9e88152a4534d9b24
(II) fglrx(0): 	0e484f27d80045593159615901010101
(II) fglrx(0): 	0101010101014e0c80c020902d10a020
(II) fglrx(0): 	138404c31000001ade0dd0d820902e10
(II) fglrx(0): 	f424138404c31000001c4e0c80c820e0
(II) fglrx(0): 	14109040138804c3100000184e0c80c8
(II) fglrx(0): 	20e014109040138804c3100000180035
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
```

I rebooted into recovery mode immediately after the crash and saved that log to be sure it was the correct one.

If anyone has any more ideas, I'd appreciate it.

Regards

Caravel

---

### Post by caravel on 2007-09-22
I've tried again,  And tried aticonfig --initial after doing it all.  I've also checked and made sure I had the symbolic link between fglrx.ko in the volatile directory from the misc directory.

I've tried manually, I've tried via apt-get, ATI and envy, still no good.

Still the same problem.  It's as if the thing tries to start up and then crashes.  Unless anyone has any other ideas then I'm pretty much stumped.  I may have to throw this card out and get an Nvidia 6xxx or 7xxx series.

---

### Post by w4ett on 2007-09-22
After looking over the logs, (unless I am missing something--My eyes ARE getting old :p ) the card/driver combo SHOULD work.

As you suggest, I would start looking at hardware issues....Maybe try the card in another machine?  I have seen certain (un-reproduceable) errors caused by card & bus controller incompaibility (I have an Nvidia card that refuses to work in an SiS based board but is ok in a Via board)

Just food for thought.

---

### Post by caravel on 2007-09-22
The card was working fine under Windows XP...  The motherboard chipset is a VIA KT266A, it's never given me any problems before.  I had a Radeon 9000Pro working ok in this same motherboard with Dapper and fglrx, but have never been able to get this card working with Feisty.  I *think* I've tried Edgy once with this same card and had the same problem in the past also.

Thanks

Caravel

---

### Post by w4ett on 2007-09-22
> **caravel said:**
> The card was working fine under Windows XP...  The motherboard chipset is a VIA KT266A, it's never given me any problems before.  I had a Radeon 9000Pro working ok in this same motherboard with Dapper and fglrx, but have never been able to get this card working with Feisty.  I *think* I've tried Edgy once with this same card and had the same problem in the past also.

Thanks

Caravel

That is a similiar situation that I experienced....card would work fine in XP, but nothing that I did seemed to make any headway in Feisty or Gutsy.  I do expect the proprietary drivers for the controller chipests to work in windows since it is the predominant OS the motherboard are designed for..(especially the smaller manufacturers like Via and SiS, who have a smaller market share)

---

### Post by caravel on 2007-09-22
I see what you're getting at, though the Radeon 9000 did work with that same chipset and Dapper.  But as you say, perhaps in this case it's the combination.

I suppose I'll carry using the xorg driver until I can get a new graphics card.  Thanks for all your help on that one.

I suppose you wouldn't know why the "grub loading stage1.5." followed by "grub loading..." takes ages?  I think it's something to do with my HDD as the BIOS take ages to detect it also.

Thanks

Caravel

---

### Post by w4ett on 2007-09-22
With both the bios detection delay and the grub delay, I would suspect a hardware (conceivably ide cable problems)......I'd suggest trying a replacement ribbon cable...after time heat and dust particles  corrode contacts and can cause extended access time.  In any event, it's a cheap troubleshooting method...oh...one other thing...in your bios disable the SMART drive checking, Bushmaster (if you have it) and other drive options should be set to the system defaults.  This might speed things up a little bit.

---

### Post by caravel on 2007-09-22
SMART is always off, I've never used it.  I already have a pretty new cable and it is a new drive but I will try another new cable, thanks.  My wife has an almost identical PC (same motherboard) and the same HDD as mine, and that also has the same slow detection problem in the BIOS, though she is using Windows XP.

---

### Post by caravel on 2007-11-12
Is there any improvement as regards Gutsy Gibbon and ATI drivers?

Also I think I resolved the slow grub issue but need to test it first.  It may have been due to me having the jumper on my hard disk set to master with slave present instead of master or single drive.  This caused a delay with the BIOS scanning for a slave.

---

### Post by w4ett on 2007-11-13
> **caravel said:**
> Is there any improvement as regards Gutsy Gibbon and ATI drivers?

Also I think I resolved the slow grub issue but need to test it first.  It may have been due to me having the jumper on my hard disk set to master with slave present instead of master or single drive.  This caused a delay with the BIOS scanning for a slave.

I have noticed a slightly slower framerate in glxgears (780 v. 830) in Gusty, but better support in Compiz (smoother response et. al.)  All in all, not a bad trade-off IMO.

---

### Post by caravel on 2007-12-18
I'll be saying goodbye to ATI ASAP.  My current card is overheating and due to the problems in this thread I won't be too worried about saving it.  Sometime in the new year I will acquire an Nvidia card, probably a 7600GT unless anyone knows of any issues of course?

:)

---

### Post by brett611 on 2007-12-18
try this link 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by caravel on 2007-12-31
Well, I'll be getting a 7300GT in a week or so and reinstalling Ubuntu again.  Is there anything I need to look out for with the Nvidia drivers?  Any how to or guides?

Many Thanks

caravel

---

### Post by overdrank on 2007-12-31
> **caravel said:**
> Well, I'll be getting a 7300GT in a week or so and reinstalling Ubuntu again.  Is there anything I need to look out for with the Nvidia drivers?  Any how to or guides?

Many Thanks

caravel

Hi and I just install a 7300 in my sons system and it worked well and if you are not happy with the restricted drivers you can try Envy. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by caravel on 2008-01-07
Well I've got the 7300GT installed and just enabled the restricted drivers and it appears to be working fine... but the Linux breaking loon inside me now wonders about the difference between the restricted drivers and the one that envy will install or the latest drivers from Nvidia?!  Will these be the latest proprietary driver?  Should I try it, or leave well alone?  Are there any other differences/advantages?

The installation so far has been easy, too easy in fact.  I feel somewhat cheated out of the usual hassle of creating symbolic links, modifying the xorg.conf tearing out handfuls of fur and staring at a black screen.

As a bonus I now have compiz working and Quake4 and Doom3 running natively, which were very easy to install.  I'm not sure why I see so many people trying to run it under wine when I searched google for info on it??

The only issues I have are with the AA settings for compiz (I assume it's compiz anyway, it used to be beryl IIRC) which don't seem to be sticking, unless I'm changing the wrong options?

I also find that I have to turn compiz off before trying to run any full screen OpenG (such as games)L, but I can live with that.

Overall though, I'm impressed.  In windows the Nvidia drivers cause constant BSoDs due to the nv4_disp "driver stuck in infinite loop" bug so at the moment I'm having better luck in linux with this card!

---

### Post by w4ett on 2008-01-07
> Well I've got the 7300GT installed and just enabled the restricted drivers and it appears to be working fine... but the Linux breaking loon inside me now wonders about the difference between the restricted drivers and the one that envy will install or the latest drivers from Nvidia?! Will these be the latest proprietary driver? Should I try it, or leave well alone? Are there any other differences/advantages?

The restricted drivers used by Envy are the newest "bleeding edge" drivers provided by Nvidia....the ones in the restricted driver manager are a little bit older, but this is not necessarily a bad thing.  These tend to be a bit more stable on most systems, and if you are not running the newest video chipsets from Nvidia, you will be ok with the ubuntu provided proprietary driver.

If you haven't already done so, install the emerald theme and the control manager  for compiz via the Synaptic Package Manager.  This will provide you an extra layer of controls and options.

Good Luck

---

### Post by caravel on 2008-01-07
Hi **w4ett**,

I have the control manager, at least I think I have, and have messed about enabling the rotating desktop cube and some other stuff.  Or is that not the control manager?  Also I've not heard of the emerald theme, I'll look that up.  You wouldn't have any idea about getting AA working on the desktop I suppose?

Regards

Caravel

---

### Post by w4ett on 2008-01-07
> **caravel said:**
> Hi **w4ett**,

I have the control manager, at least I think I have, and have messed about enabling the rotating desktop cube and some other stuff.  Or is that not the control manager?  Also I've not heard of the emerald theme, I'll look that up.  You wouldn't have any idea about getting AA working on the desktop I suppose?

Regards

Caravel

You might look here:
> [http://ubuntuforums.org/showthread.php?t=500486](http://ubuntuforums.org/showthread.php?t=500486)
and see if this might help.

---

### Post by caravel on 2008-03-30
Well after two months with a perfectly working 7300GT I had to give up on it.  The reason?  Windows.  The card runs like a hog under windows due to a bug. (if you've used windows and you've heard of the "infinite loop bug", you'll know what I mean).  So a few days ago I fixed the heatsink onto the Radeon 9800, applied some arctic silver 5 and tightened up the clamps that hold the heatsink on.  And now it's running totally stable in Windows (a lot more stable than the 7300GT was).

So now this brings me back to the same old problem, Ubnuntu/Linux + ATI.  You can read this thread to see what I've tried so far.  But this is what I tried yesterday.

Envy:  Removed the Nvidia driver, tried all three ATI driver versions that Envy provides (removing in between installs) same result every time.  Black screen, monitor goes to sleep, lock up, nothing responds.  The only way out is to hard reset, boot into safe mode and edit xorg.conf at the command line replacing "fglrx" with "ati".

Why does this card simply refuse to work under ubuntu with fglrx?

---

### Post by caravel on 2008-03-30
Bump.

I supopose I'll wait until 8.04 comes out and try again? :confused:

---

### Post by caravel on 2008-04-03
Well I was up till 2am last not trying the installation in the ATI wiki for Gutsy.  I followed it **to the letter** for a manual install but the screen still blacks out and the monitor goes on standby forcing me to use sysrq s u b and then hard reset because it doesn't reboot.  I had removed all of the old fglrx and blacklisted.  In short I've tried everything and will now have to give up.  Once I finish what I need to do in Windows I will probably  get rid of Windows and the ATI card and put my 7300GT back in there.

---

