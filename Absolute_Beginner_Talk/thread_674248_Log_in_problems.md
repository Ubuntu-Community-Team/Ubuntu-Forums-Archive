---
title: "Log in problems"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Delfairen on 2008-01-21
Hi

I do not know quite where to start with this (except for searching the forums which I think I have done enough to make my brain hurt) I just installed the latest ati driver since they fixed the issue with 1680x1050 screens not being detected.

I had this working until I tried to re-enable compiz-fusion now when I try and login it accepts the login I get the login sound and then it drops me back to the login screen.

I need to find out what is not running correctly on startup but I am not sure how to do this.

Help would be appreciated and at least I can then respond with info on whether the ATI 8.1 drivers work correctly now with 1680x1050 monitors.

Thanks

---

### Post by jeffus_il on 2008-01-21
Your X Server could be crashing, so a log would be interesting.
In a terminal: ```
less /var/log/Xorg.0.log
```

---

### Post by Delfairen on 2008-01-21
Thanks. I've been called into work for a down system.... go figure! So I'll look when I get home and thanks a log was what I needed to look at :)

---

### Post by Delfairen on 2008-01-22
I've messed a lot tonight but I am still getting nowhere... I'm starting to think its ATI's lousy drivers again. I found some info that the new drivers work with Xserver 1.4 but I can't seem to find a lot of evidence to support this theory. 

Well here is the Xorg.0.log info I can't see any errors and only a couple of warnings.

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux Ubuntu-Desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 21 23:31:59 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 10

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 1002,5950 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 1002,437a card 1462,7141 rev 80 class 01,01,8f hdr 00
(II) PCI: 00:12:0: chip 1002,4379 card 1462,7141 rev 80 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 1462,7191 rev 80 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1462,7191 rev 80 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1462,7191 rev 80 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 1462,7191 rev 81 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 1462,7191 rev 80 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,437b card 1462,7191 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 80 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 80 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,7249 card 1002,0b12 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,7269 card 1002,0b13 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 1814,0601 card 1814,2860 rev 00 class 02,80,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 1462,191c rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc R580 [Radeon X1900 XT] Primary rev 0, Mem @ 0xd0000000/28, 0xfeaf0000/16, I/O @ 0xd800/8, BIOS @ 0xfeac0000/17
(--) PCI: (1:0:1) ATI Technologies Inc R580 [Radeon X1900 XT] Secondary rev 0, Mem @ 0xfeae0000/16
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
(II) Active PCI resource ranges:
	[0] -1	0	0xfebebc00 - 0xfebebcff (0x100) MX[B]
	[1] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[2] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[3] -1	0	0x88100000 - 0x881003ff (0x400) MX[B]
	[4] -1	0	0xfe9f8000 - 0xfe9f8fff (0x1000) MX[B]
	[5] -1	0	0xfe9f9000 - 0xfe9f9fff (0x1000) MX[B]
	[6] -1	0	0xfe9fa000 - 0xfe9fafff (0x1000) MX[B]
	[7] -1	0	0xfe9fb800 - 0xfe9fb9ff (0x200) MX[B]
	[8] -1	0	0xfe9fbc00 - 0xfe9fbdff (0x200) MX[B]
	[9] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[10] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[11] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[20] -1	0	0x00008800 - 0x0000880f (0x10) IX[B]
	[21] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[22] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[23] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebebc00 - 0xfebebcff (0x100) MX[B]
	[1] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[2] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[3] -1	0	0x88100000 - 0x881003ff (0x400) MX[B]
	[4] -1	0	0xfe9f8000 - 0xfe9f8fff (0x1000) MX[B]
	[5] -1	0	0xfe9f9000 - 0xfe9f9fff (0x1000) MX[B]
	[6] -1	0	0xfe9fa000 - 0xfe9fafff (0x1000) MX[B]
	[7] -1	0	0xfe9fb800 - 0xfe9fb9ff (0x200) MX[B]
	[8] -1	0	0xfe9fbc00 - 0xfe9fbdff (0x200) MX[B]
	[9] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[10] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[11] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[20] -1	0	0x00008800 - 0x0000880f (0x10) IX[B]
	[21] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[22] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[23] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
	[4] -1	0	0xfebebc00 - 0xfebebcff (0x100) MX[B]
	[5] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[6] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[7] -1	0	0x88100000 - 0x881003ff (0x400) MX[B]
	[8] -1	0	0xfe9f8000 - 0xfe9f8fff (0x1000) MX[B]
	[9] -1	0	0xfe9f9000 - 0xfe9f9fff (0x1000) MX[B]
	[10] -1	0	0xfe9fa000 - 0xfe9fafff (0x1000) MX[B]
	[11] -1	0	0xfe9fb800 - 0xfe9fb9ff (0x200) MX[B]
	[12] -1	0	0xfe9fbc00 - 0xfe9fbdff (0x200) MX[B]
	[13] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[14] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[15] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[26] -1	0	0x00008800 - 0x0000880f (0x10) IX[B]
	[27] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[28] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[29] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[35] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[36] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebebc00 - 0xfebebcff (0x100) MX[B]
	[5] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[6] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[7] -1	0	0x88100000 - 0x881003ff (0x400) MX[B]
	[8] -1	0	0xfe9f8000 - 0xfe9f8fff (0x1000) MX[B]
	[9] -1	0	0xfe9f9000 - 0xfe9f9fff (0x1000) MX[B]
	[10] -1	0	0xfe9fa000 - 0xfe9fafff (0x1000) MX[B]
	[11] -1	0	0xfe9fb800 - 0xfe9fb9ff (0x200) MX[B]
	[12] -1	0	0xfe9fbc00 - 0xfe9fbdff (0x200) MX[B]
	[13] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[14] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[15] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[26] -1	0	0x00008800 - 0x0000880f (0x10) IX[B]
	[27] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[28] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[29] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[35] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[36] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebebc00 - 0xfebebcff (0x100) MX[B]
	[5] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[6] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[7] -1	0	0x88100000 - 0x881003ff (0x400) MX[B]
	[8] -1	0	0xfe9f8000 - 0xfe9f8fff (0x1000) MX[B]
	[9] -1	0	0xfe9f9000 - 0xfe9f9fff (0x1000) MX[B]
	[10] -1	0	0xfe9fa000 - 0xfe9fafff (0x1000) MX[B]
	[11] -1	0	0xfe9fb800 - 0xfe9fb9ff (0x200) MX[B]
	[12] -1	0	0xfe9fbc00 - 0xfe9fbdff (0x200) MX[B]
	[13] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[14] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[15] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x00008800 - 0x0000880f (0x10) IX[B]
	[30] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[31] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[32] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[34] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[35] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[38] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[39] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.12
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: R580
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: ACR  Model: ad74  Serial#: 1679822821
(II) VESA(0): Year: 2006  Week: 42
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) VESA(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) VESA(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) VESA(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) VESA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) VESA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) VESA(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) VESA(0): Monitor name: Acer AL2216W
(II) VESA(0): Serial No: ETL7409038
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff00047274ade50f2064
(II) VESA(0): 	2a100103e82f1e782ec585a459499a24
(II) VESA(0): 	125054bfef0081808140714f9500950f
(II) VESA(0): 	b30081c08bc021399030621a274068b0
(II) VESA(0): 	3600d9281100001c000000fd00384c1e
(II) VESA(0): 	5215000a202020202020000000fc0041
(II) VESA(0): 	63657220414c32323136570a000000ff
(II) VESA(0): 	0045544c3734303930333820202000e6
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) VESA(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) VESA(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) VESA(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) VESA(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) VESA(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) VESA(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) VESA(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(II) VESA(0): Modeline "1280x720"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
(II) VESA(0): Modeline "1360x765"   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync
(II) VESA(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 101 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 103 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 105 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 18
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 18
	LinNumberOfImagePages: 18
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 107 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 109 (132x25)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xb000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 10a (132x43)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xb000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 130 (132x44)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xb000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 44
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 110 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 112 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 113 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 115 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 116 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 118 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 119 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 11a (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 11b (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 10d (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 10f (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 120 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 193 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 194 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 195 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 196 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1b3 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 512
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1b4 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1b5 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1b6 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2048
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 18
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 18
	LinNumberOfImagePages: 18
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1c3 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1c4 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1c5 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1c6 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 17
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 17
	LinNumberOfImagePages: 17
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 184 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 133 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 768
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 768
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 134 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1472
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1472
	BnkNumberOfImagePages: 27
	LinNumberOfImagePages: 27
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 135 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1472
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1472
	BnkNumberOfImagePages: 27
	LinNumberOfImagePages: 27
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 136 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2944
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 13
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2944
	BnkNumberOfImagePages: 13
	LinNumberOfImagePages: 13
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 153 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1152
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1152
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 154 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2304
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2304
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 155 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2304
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2304
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 156 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 4608
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4608
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 163 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 164 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 165 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 166 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 121 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 122 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 123 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 124 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 143 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1408
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1408
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 144 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2816
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2816
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 145 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2816
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2816
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 146 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 5632
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5632
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 173 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 174 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 175 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 176 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 184 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1d3 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1856
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1856
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1d4 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3712
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3712
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1d5 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3712
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3712
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1d6 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 7424
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 7424
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1e3 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1e4 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1e5 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1e6 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005013
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Failsafe Monitor: Using hsync range of 30.00-82.00 kHz
(II) VESA(0): Failsafe Monitor: Using vrefresh range of 56.00-76.00 Hz
(II) VESA(0): Not using built-in mode "1920x1440" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1856x1392" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1152x864" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "720x400"
(**) VESA(0): Display dimensions: (470, 300) mm
(**) VESA(0): DPI set to (43, 50)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (111)
(II) VESA(0): Attempting to use 70Hz refresh for mode "720x400" (135)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebebc00 - 0xfebebcff (0x100) MX[B]
	[5] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[6] -1	0	0xfe9e8000 - 0xfe9ebfff (0x4000) MX[B]
	[7] -1	0	0x88100000 - 0x881003ff (0x400) MX[B]
	[8] -1	0	0xfe9f8000 - 0xfe9f8fff (0x1000) MX[B]
	[9] -1	0	0xfe9f9000 - 0xfe9f9fff (0x1000) MX[B]
	[10] -1	0	0xfe9fa000 - 0xfe9fafff (0x1000) MX[B]
	[11] -1	0	0xfe9fb800 - 0xfe9fb9ff (0x200) MX[B]
	[12] -1	0	0xfe9fbc00 - 0xfe9fbdff (0x200) MX[B]
	[13] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[14] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[15] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x00008800 - 0x0000880f (0x10) IX[B]
	[30] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[31] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[32] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[34] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[35] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[38] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[39] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.12
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: R580
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xd0000000,0x1000000)
(II) VESA(0): virtual address = 0xb6a9f000,
	physical address = 0xd0000000, size = 16777216
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Generic Keyboard: XkbModel: "pc101"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9

```

And the xorg.conf file

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Videoram	512
	Option		"UseFBDev"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Acer AL2216W"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection

```

---

### Post by jeffus_il on 2008-01-22
The log file seems unconnected to the xorg.conf, the log file loads a VESA driver and the conf a fglrx!

---

### Post by xeth_delta on 2008-01-22
What is the output from dmesg? Any errors there? By the way, do you have enough space on the linux partition? A full disk would create log-in problems.

---

### Post by Delfairen on 2008-01-22
How could they be so disjoined? They were both from the same boot I did get the message saying x was starting in low graphics mode could this be using vesa as a fallback?

---

### Post by jeffus_il on 2008-01-22
Must be that, yes, the question is why did it decide to start in the low graphics mode?

---

### Post by Delfairen on 2008-01-22
dmesg

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffde000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524240) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524240
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524240
[    0.000000] On node 0 totalpages: 524240
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292561 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9740 checksum 0
[    0.000000] ACPI: RSDP 000F9740, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFD0000, 0034 (r1 A M I  OEMRSDT  11000522 MSFT       97)
[    0.000000] ACPI: FACP 7FFD0200, 0084 (r2 A M I  OEMFACP  11000522 MSFT       97)
[    0.000000] ACPI: DSDT 7FFD0430, 3E6E (r1  1ABZR 1ABZRB49      B49 INTL  2002026)
[    0.000000] ACPI: FACS 7FFDE000, 0040
[    0.000000] ACPI: APIC 7FFD0390, 005C (r1 A M I  OEMAPIC  11000522 MSFT       97)
[    0.000000] ACPI: MCFG 7FFD03F0, 003C (r1 A M I  OEMMCFG  11000522 MSFT       97)
[    0.000000] ACPI: OEMB 7FFDE040, 0056 (r1 A M I  AMI_OEM  11000522 MSFT       97)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f780000)
[    0.000000] Built 1 zonelists.  Total pages: 520145
[    0.000000] Kernel command line: root=UUID=b448d013-cc91-483c-af76-d4bbfe1d42ab ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2400.236 MHz processor.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 2067460k/2096960k available (2015k kernel code, 28156k reserved, 916k data, 364k init, 1179456k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.084000] Calibrating delay using timer specific routine.. 4822.47 BogoMIPS (lpj=9644950)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.344000] ACPI: Core revision 20070126
[    0.344000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.344000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
[    0.344000] SMP alternatives: switching to SMP code
[    0.344000] Booting processor 1/1 eip 3000
[    0.356000] Initializing CPU#1
[    0.436000] Calibrating delay using timer specific routine.. 4776.15 BogoMIPS (lpj=9552309)
[    0.436000] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[    0.436000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.436000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.436000] CPU 1(2) -> Core 1
[    0.436000] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[    0.436000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
[    0.436000] Total of 2 processors activated (9598.62 BogoMIPS).
[    0.436000] ENABLING IO-APIC IRQs
[    0.436000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.436000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.436000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[    0.436000] ...trying to set up timer as Virtual Wire IRQ... works.
[    0.480000] Brought up 2 CPUs
[    0.560000] migration_cost=0
[    0.560000] Booting paravirtualized kernel on bare hardware
[    0.560000] Time:  7:53:55  Date: 00/22/108
[    0.560000] NET: Registered protocol family 16
[    0.560000] EISA bus registered
[    0.560000] ACPI: bus type pci registered
[    0.560000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[    0.560000] PCI: Using configuration type 1
[    0.560000] Setting up standard PCI resources
[    0.568000] ACPI: EC: Look up EC in DSDT
[    0.568000] ACPI: Interpreter enabled
[    0.568000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.568000] ACPI: Using IOAPIC for interrupt routing
[    0.572000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.572000] PCI: Probing PCI hardware (bus 00)
[    0.576000] PCI: Transparent bridge - 0000:00:14.4
[    0.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.580000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.580000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.580000] pnp: PnP ACPI init
[    0.580000] ACPI: bus type pnp registered
[    0.584000] pnp: PnP ACPI: found 12 devices
[    0.584000] ACPI: ACPI bus type pnp unregistered
[    0.584000] PnPBIOS: Disabled by ACPI PNP
[    0.584000] PCI: Using ACPI for IRQ routing
[    0.584000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.592000] NET: Registered protocol family 8
[    0.592000] NET: Registered protocol family 20
[    0.592000] pnp: 00:06: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.592000] pnp: 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.592000] pnp: 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.592000] pnp: 00:09: ioport range 0x600-0x60f has been reserved
[    0.592000] pnp: 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.592000] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.592000] pnp: 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.592000] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.592000] pnp: 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
[    0.624000] PCI: Bridge: 0000:00:02.0
[    0.624000]   IO window: d000-dfff
[    0.624000]   MEM window: fea00000-feafffff
[    0.624000]   PREFETCH window: d0000000-dfffffff
[    0.624000] PCI: Bridge: 0000:00:14.4
[    0.624000]   IO window: e000-efff
[    0.624000]   MEM window: feb00000-febfffff
[    0.624000]   PREFETCH window: 88000000-880fffff
[    0.624000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.624000] NET: Registered protocol family 2
[    0.628000] Time: acpi_pm clocksource has been installed.
[    0.628000] Switched to high resolution mode on CPU 0
[    0.628000] Switched to high resolution mode on CPU 1
[    0.676000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.676000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.676000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.676000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.676000] TCP reno registered
[    0.692000] checking if image is initramfs... it is
[    1.172000] Freeing initrd memory: 7032k freed
[    1.172000] audit: initializing netlink socket (disabled)
[    1.172000] audit(1200988436.128:1): initialized
[    1.172000] highmem bounce pool size: 64 pages
[    1.172000] VFS: Disk quotas dquot_6.5.1
[    1.172000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.172000] io scheduler noop registered
[    1.172000] io scheduler anticipatory registered
[    1.172000] io scheduler deadline registered
[    1.172000] io scheduler cfq registered (default)
[    1.172000] PCI: MSI quirk detected. MSI deactivated.
[    1.224000] Boot video device is 0000:01:00.0
[    1.224000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.224000] assign_interrupt_mode Found MSI capability
[    1.224000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.224000] isapnp: Scanning for PnP cards...
[    1.576000] isapnp: No Plug & Play device found
[    1.592000] Real Time Clock Driver v1.12ac
[    1.592000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.596000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.596000] input: Macintosh mouse button emulation as /class/input/input0
[    1.596000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.596000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.596000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.596000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.596000] mice: PS/2 mouse device common for all mice
[    1.596000] EISA: Probing bus 0 at eisa.0
[    1.596000] Cannot allocate resource for EISA slot 8
[    1.596000] EISA: Detected 0 cards.
[    1.596000] TCP cubic registered
[    1.596000] NET: Registered protocol family 1
[    1.596000] Using IPI No-Shortcut mode
[    1.596000]   Magic number: 8:700:875
[    1.600000] Freeing unused kernel memory: 364k freed
[    2.776000] AppArmor: AppArmor initialized<5>audit(1200988437.628:2):  type=1505 info="AppArmor initialized" pid=1212
[    2.780000] fuse init (API version 7.8)
[    2.784000] Failure registering capabilities with primary security module.
[    3.224000] usbcore: registered new interface driver usbfs
[    3.224000] usbcore: registered new interface driver hub
[    3.224000] usbcore: registered new device driver usb
[    3.228000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.228000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[    3.228000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.228000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.228000] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe9fa000
[    3.236000] SCSI subsystem initialized
[    3.240000] libata version 2.21 loaded.
[    3.304000] usb usb1: configuration #1 chosen from 1 choice
[    3.304000] hub 1-0:1.0: USB hub found
[    3.304000] hub 1-0:1.0: 4 ports detected
[    3.328000] FDC 0 is a post-1991 82077
[    3.340000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.348000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.348000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.408000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[    3.408000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.408000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.408000] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe9f9000
[    3.468000] usb usb2: configuration #1 chosen from 1 choice
[    3.468000] hub 2-0:1.0: USB hub found
[    3.468000] hub 2-0:1.0: 4 ports detected
[    3.572000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    3.572000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.572000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.572000] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe9f8000
[    3.712000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    3.712000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.712000] usb usb3: configuration #1 chosen from 1 choice
[    3.712000] hub 3-0:1.0: USB hub found
[    3.712000] hub 3-0:1.0: 8 ports detected
[    3.816000] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.816000] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    3.816000] sata_sil 0000:00:11.0: version 2.2
[    3.816000] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 17
[    3.816000] scsi0 : sata_sil
[    3.816000] scsi1 : sata_sil
[    3.816000] ata1: SATA max UDMA/100 cmd 0xf883cc80 ctl 0xf883cc8a bmdma 0xf883cc00 irq 17
[    3.816000] ata2: SATA max UDMA/100 cmd 0xf883ccc0 ctl 0xf883ccca bmdma 0xf883cc08 irq 17
[    3.816000] 8139too Fast Ethernet driver 0.9.28
[    4.284000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    4.292000] ata1.00: ATA-7: WDC WD1600JS-00MHB0, 02.01C03, max UDMA/133
[    4.292000] ata1.00: 312581808 sectors, multi 16: LBA48 
[    4.300000] ata1.00: configured for UDMA/100
[    4.612000] ata2: SATA link down (SStatus 0 SControl 310)
[    4.612000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-00M 02.0 PQ: 0 ANSI: 5
[    4.612000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[    4.612000] scsi2 : sata_sil
[    4.612000] scsi3 : sata_sil
[    4.612000] ata3: SATA max UDMA/100 cmd 0xf8876880 ctl 0xf887688a bmdma 0xf8876800 irq 18
[    4.612000] ata4: SATA max UDMA/100 cmd 0xf88768c0 ctl 0xf88768ca bmdma 0xf8876808 irq 18
[    4.924000] ata3: SATA link down (SStatus 0 SControl 310)
[    5.236000] ata4: SATA link down (SStatus 0 SControl 310)
[    5.236000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    5.236000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[    5.236000] ATIIXP: chipset revision 128
[    5.236000] ATIIXP: not 100% native mode: will probe irqs later
[    5.236000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:DMA
[    5.236000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:pio, hdd:pio
[    5.236000] Probing IDE interface ide0...
[    5.500000] usb 3-8: new high speed USB device using ehci_hcd and address 6
[    5.632000] usb 3-8: configuration #1 chosen from 1 choice
[    5.936000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    6.220000] usb 1-2: configuration #1 chosen from 1 choice
[    6.248000] hdb: LITE-ON DVDRW SHM-165H6S, ATAPI CD/DVD-ROM drive
[    6.304000] hdb: selected mode 0x44
[    6.304000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.316000] Probing IDE interface ide1...
[    6.532000] usb 1-4: new full speed USB device using ohci_hcd and address 4
[    6.884000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[    6.884000] eth0: RealTek RTL8139 at 0xf8816c00, 00:13:d3:bf:c6:ec, IRQ 20
[    6.884000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.892000] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[    6.892000] Uniform CD-ROM driver Revision: 3.20
[    6.892000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.892000] sd 0:0:0:0: [sda] Write Protect is off
[    6.892000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.892000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.892000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.892000] sd 0:0:0:0: [sda] Write Protect is off
[    6.892000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.892000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.892000]  sda:<6>usb 1-4: configuration #1 chosen from 1 choice
[    6.900000]  sda1 sda2 < sda5 >
[    6.920000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.924000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.088000] Attempting manual resume
[    7.088000] swsusp: Resume From Partition 8:5
[    7.088000] PM: Checking swsusp image.
[    7.088000] PM: Resume from disk failed.
[    7.120000] kjournald starting.  Commit interval 5 seconds
[    7.120000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.200000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    7.412000] usb 2-1: configuration #1 chosen from 1 choice
[    7.716000] usb 2-2: new low speed USB device using ohci_hcd and address 3
[    7.928000] usb 2-2: configuration #1 chosen from 1 choice
[    7.928000] usbcore: registered new interface driver libusual
[    7.928000] usbcore: registered new interface driver hiddev
[    8.152000] Initializing USB Mass Storage driver...
[    8.152000] scsi4 : SCSI emulation for USB Mass Storage devices
[    8.152000] usb-storage: device found at 6
[    8.152000] usb-storage: waiting for device to settle before scanning
[    9.120000] hiddev96: USB HID v1.10 Device [American Power Conversion Back-UPS ES 750 FW:841.I1 .D USB FW:I1 ] on usb-0000:00:13.0-2
[    9.124000] input: Logitech USB Receiver as /class/input/input1
[    9.124000] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.1-1
[    9.128000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[    9.128000] input: Logitech USB Receiver as /class/input/input2
[    9.128000] input,hiddev97: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1
[    9.140000] input: Logitech USB Receiver as /class/input/input3
[    9.140000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-2
[    9.140000] usbcore: registered new interface driver usbhid
[    9.140000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    9.140000] usbcore: registered new interface driver usb-storage
[    9.140000] USB Mass Storage support registered.
[   12.784000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.880000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.904000] Linux agpgart interface v0.102 (c) Dave Jones
[   12.912000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   13.040000] input: PC Speaker as /class/input/input4
[   13.128000] usbcore: registered new interface driver xpad
[   13.128000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   13.152000] usb-storage: device scan complete
[   13.156000] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[   13.180000] sd 4:0:0:0: [sdb] 4013709 512-byte hardware sectors (2055 MB)
[   13.180000] sd 4:0:0:0: [sdb] Write Protect is off
[   13.180000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   13.180000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   13.188000] sd 4:0:0:0: [sdb] 4013709 512-byte hardware sectors (2055 MB)
[   13.192000] sd 4:0:0:0: [sdb] Write Protect is off
[   13.192000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   13.192000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   13.192000]  sdb: sdb1
[   13.192000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   13.192000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   13.296000] Bluetooth: Core ver 2.11
[   13.296000] NET: Registered protocol family 31
[   13.296000] Bluetooth: HCI device and connection manager initialized
[   13.296000] Bluetooth: HCI socket layer initialized
[   13.348000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.368000] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   13.368000] [fglrx] ASYNCIO init succeed!
[   13.368000] [fglrx] PAT is enabled successfully!
[   13.368000] [fglrx] module loaded - fglrx 8.45.4 [Jan 16 2008] on minor 0
[   13.380000] Bluetooth: HCI USB driver ver 2.9
[   13.384000] usbcore: registered new interface driver hci_usb
[   13.460000] usbcore: registered new interface driver lmpcm_usb
[   13.460000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   13.604000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   13.784000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   14.772000] lp: driver loaded but no devices found
[   14.824000] Adding 6080560k swap on /dev/sda5.  Priority:-1 extents:1 across:6080560k
[   15.040000] EXT3 FS on sda1, internal journal

```

And I have 113Gb free in total on the drive.

---

### Post by jeffus_il on 2008-01-22
Is fglrx loaded? ```
lsmod | grep fglrx
```
Can you ```
sudo modprobe fglrx
```

Quote from a gentoo wiki:
> ** Unable to modprobe fglrx **

 If the module cannot be loaded ("operation not permitted"), check if the kernel Direct Rendering Manager (Device Drivers -> Character devices -> Direct Rendering Manager) is enabled. If so: Disable and recompile :-) 
Or if you are using a precompiled kernel you can unload the *dri* and *radeon* module before modprobing *fglrx*. 
modprobe -r dri radeon 
modprobe fglrx


[http://gentoo-wiki.com/HOWTO_ATI_Drivers#Unable_to_modprobe_fglrx](http://gentoo-wiki.com/HOWTO_ATI_Drivers#Unable_to_modprobe_fglrx)

---

### Post by xeth_delta on 2008-01-22
Now this is unusual, from dmesg the fglrx module seems to be loading OK:
```
[   13.368000] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   13.368000] [fglrx] ASYNCIO init succeed!
[   13.368000] [fglrx] PAT is enabled successfully!
[   13.368000] [fglrx] module loaded - fglrx 8.45.4 [Jan 16 2008] on minor 0
```
and indeed, the X server log seems to indicate a vesa module load.

---

### Post by Delfairen on 2008-01-22
Well the lsmod came back with the following info

```

fglrx                1476940  0
agpgart                35016  2 fglrx,ati_agp

```

But the modprobe came back blank

---

### Post by Delfairen on 2008-01-22
When I try and get the fglrxinfo I get the following

```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)

```

---

### Post by jeffus_il on 2008-01-22
Want to choose a session other than gnome as a test like openbox, if you don't have it installed ```
sudo aptitude install openbox
```

---

### Post by Delfairen on 2008-01-22
Trying that now.

I made one change to the xorg.conf but it made no difference and that was to Load "dri"

---

### Post by xeth_delta on 2008-01-22
Just out curiousity, why don't you try starting X with a different driver. Replace "fglrx" with "radeon" in "/etc/X11/xorg.conf". This might show you if the strange behaviour is produced by the fglrx driver.

---

### Post by xeth_delta on 2008-01-22
Another question, what ati graphics card model are you trying to configure?

---

### Post by Delfairen on 2008-01-22
No Change Jeff and I'll check a different one in a min Xeth. In case you're curious the login screen is at the same low resolution.

---

### Post by Delfairen on 2008-01-22
The card is an 512Mb ATI X1900 XT PCIE

---

### Post by Delfairen on 2008-01-22
Changed to Radeon instead of fglrx - no change
Changed back and prayed it just worked but alas no change
Added a second Busid to the device section as the card has a primary and secondary but still the same low res message before the login screen. the Ubuntu load screen is however in the full 1680x1050 res.

---

### Post by xeth_delta on 2008-01-22
Make a back-up of "/etc/X11/xorg.conf". I am starting to believe that this does not have to do with this configuration file itself, since you mentioned it worked before trying to re-enable compiz.

Anyway, you could try:
```
sudo dpkg-reconfigure xserver-xorg
```

If nothing changes, replace the new xorg.conf with the back-up you made.

---

### Post by Delfairen on 2008-01-22
Well I have a nice black screen now and Ctrl+Alt+F2 doesn't even bring up a tty... lol

EDIT:

Ok back in again.

---

### Post by xeth_delta on 2008-01-22
> **Delfairen said:**
> Well I have a nice black screen now and Ctrl+Alt+F2 doesn't even bring up a tty... lol

EDIT:

Ok back in again.

Did you try uninstalling compiz and purging its configuration files?

---

### Post by Delfairen on 2008-01-22
I just removed compiz and all the config still no change. I'm not sure where to head next I guess reinstall compiz. I feel there is something more basic though since I do not get the correct res in the login screen even.

---

### Post by xeth_delta on 2008-01-22
> **Delfairen said:**
> I just removed compiz and all the config still no change. I'm not sure where to head next I guess reinstall compiz. I feel there is something more basic though since I do not get the correct res in the login screen even.

Did you use "aptitude purge compiz"?

---

### Post by Delfairen on 2008-01-22
I used the synaptic package manager.

---

### Post by Delfairen on 2008-01-22
Running the purge now and then will try again.

---

### Post by Delfairen on 2008-01-22
Nada. Same low res warning at the beginning before the login screen.

---

### Post by xeth_delta on 2008-01-22
> **Delfairen said:**
> Nada. Same low res warning at the beginning before the login screen.

What exactly is the warning?

---

