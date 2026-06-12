---
title: "The X server is now disable !!! enable GDM???"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by benevolent on 2007-10-08
***The X server is now disable restart GDM when configured correctly***


How can I restart GDM so i can enable the X server????? I've quoted the log file


```
sudo /etc/init.d/ restart
``` this one is correct????







```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux dimitris 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct  8 22:00:39 2007
(EE) Unable to locate/open config file
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
(II) PCI: 00:00:0: chip 1106,0258 card 1106,0258 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1258 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2258 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3258 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4258 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7258 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 1102,0004 card 1102,0052 rev 03 class 04,01,00 hdr 80
(II) PCI: 00:0b:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 00:0c:0: chip 134d,2189 card 134d,1002 rev 04 class 07,03,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1462,0430 rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1106,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:12:0: chip 1106,3065 card 1462,043c rev 78 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71c1 card 174b,e040 rev 9e class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e1 card 174b,e041 rev 9e class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000f (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xffd00000 - 0xffdfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd7f00000 - 0xf7efffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x71c1) rev 158, Mem @ 0xe0000000/28, 0xffdf0000/16, I/O @ 0xa800/8, BIOS @ 0xffdc0000/17
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x71e1) rev 158, Mem @ 0xffde0000/16
New driver is "ati"
(==) Using default built-in configuration (55 lines)
(==) --- Start of built-in configuration ---
	Section "Module"
		Load	"extmod"
		Load	"dbe"
		Load	"glx"
		Load	"freetype"
		Load	"type1"
		Load	"record"
		Load	"dri"
	EndSection
	Section "Monitor"
		Identifier	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default ati Device 0"
		Driver	"ati"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default ati Screen 0"
		Device	"Builtin Default ati Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vga Device 0"
		Driver	"vga"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vga Screen 0"
		Device	"Builtin Default vga Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default ati Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default vga Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default ati Device 0"
(**) |-->Screen "Builtin Default fbdev Screen 0" (1)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default vesa Device 0"
(**) |-->Screen "Builtin Default vga Screen 0" (3)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default vga Device 0"
(==) |-->Input Device "<default pointer>"
(==) |-->Input Device "<default keyboard>"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the default mouse configuration.
(WW) The core keyboard device wasn't specified explicitly in the layout.
	Using the default keyboard configuration.
(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/X11R6/lib/X11/fonts/Type1".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/X11R6/lib/X11/fonts/Type1").
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xffefad00 - 0xffefadff (0x100) MX[B]
	[1] -1	0	0xffefae00 - 0xffefaeff (0x100) MX[B]
	[2] -1	0	0xffefb000 - 0xffefbfff (0x1000) MX[B]
	[3] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[4] -1	0	0xffde0000 - 0xffdeffff (0x10000) MX[B](B)
	[5] -1	0	0xffdc0000 - 0xffddffff (0x20000) MX[B](B)
	[6] -1	0	0xffdf0000 - 0xffdfffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[13] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xffefad00 - 0xffefadff (0x100) MX[B]
	[1] -1	0	0xffefae00 - 0xffefaeff (0x100) MX[B]
	[2] -1	0	0xffefb000 - 0xffefbfff (0x1000) MX[B]
	[3] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[4] -1	0	0xffde0000 - 0xffdeffff (0x10000) MX[B](B)
	[5] -1	0	0xffdc0000 - 0xffddffff (0x20000) MX[B](B)
	[6] -1	0	0xffdf0000 - 0xffdfffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[13] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
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
	[4] -1	0	0xffefad00 - 0xffefadff (0x100) MX[B]
	[5] -1	0	0xffefae00 - 0xffefaeff (0x100) MX[B]
	[6] -1	0	0xffefb000 - 0xffefbfff (0x1000) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xffde0000 - 0xffdeffff (0x10000) MX[B](B)
	[9] -1	0	0xffdc0000 - 0xffddffff (0x20000) MX[B](B)
	[10] -1	0	0xffdf0000 - 0xffdfffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.3.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vga"
(II) Loading /usr/lib/xorg/modules/drivers//vga_drv.so
(II) Module vga: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
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
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(II) VGA: Generic VGA driver (version 4.1) for chipsets: generic
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "Builtin Default ati Device 0".
(--) Assigning device section with no busID to primary device
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 1.1
(II) FBDEV(0): using default device
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffefad00 - 0xffefadff (0x100) MX[B]
	[5] -1	0	0xffefae00 - 0xffefaeff (0x100) MX[B]
	[6] -1	0	0xffefb000 - 0xffefbfff (0x1000) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xffde0000 - 0xffdeffff (0x10000) MX[B](B)
	[9] -1	0	0xffdc0000 - 0xffddffff (0x20000) MX[B](B)
	[10] -1	0	0xffdf0000 - 0xffdfffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(--) Assigning device section with no busID to primary device
(--) Chipset generic found

Fatal server error:
Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices


```


My vga is X1650PRO... I tried to install ati drivers, and i crash my system:(

How can I restore it? 


thx in advance

---

### Post by Dr Small on 2007-10-08
```
sudo /etc/init.d/gdm restart
```

---

### Post by benevolent on 2007-10-08
i tried to dkpg-reconfigure xserver first and now i have

**Fatal server error: failed to initialize core devices**


:(:(

---

### Post by jonathanmotes on 2007-10-08
There is a terminal "command" documented in the xorg.conf file that seems to work better at configuring things than the generic "dkpg-reconfigure xserver" (at least for me). I don't remember it right now (I'm not using Linux at the moment). It sets things up automatically. Open the xorg.conf file like this:
```
sudo gedit etc/X11/xorg.conf
```

Look a few lines down for it. In my experience it allowed me to at least get to the desktop where I could configure things better.

Hope this helps!

---

### Post by Dr Small on 2007-10-08
Since he doesn't have X working properly, can't use gedit, so you'll have to use nano.
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by benevolent on 2007-10-08
yes.... and then?????


(also Ii use pico)

---

### Post by coffeecat on 2007-10-08
I should imagine the command that jonathanmotes was thinking of would be:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That's what appears at the end of the commented lines in my Feisty xorg.conf.

If that doesn't do the trick, try putting "vesa" in the Driver line of the Device section of xorg.conf (instead of whatever you've got for your ATI card). That should at least get you a GUI so you can trouble-shoot your problem. But, be warned - the vesa driver is pretty minimal.

---

### Post by benevolent on 2007-10-08
ok, I'm at the xorg.conf


i have the vesa drivers and still the X doesn't start... Should i change something from here????

---

### Post by jonathanmotes on 2007-10-08
What kind of computer are you using? I had a recent experience like yours with an HP dv9000 series laptop running Gutsy. I had to use special boot-up options to get the live disc to work. After I installed Gutsy, I removed the options that I used (noapci noirqdebug) and the laptop continued to boot up normally. However, after the last kernel update, it refused to start X, so I had to reapply my boot options. 

I guess my question, then is: did you have to use any special booting options in order to install Ubuntu? You can check your boot options by looking in a file: ```
sudo nano /boot/grub/menu.lst
``` In my case, line 92 specifies boot options. It shows this: ```
# defoptions=quiet splash noapic noirdebug
``` Anything after the "splash" option was entered by me.

In response to the above post from coffeecat, yes ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` is what I was thinking of. And as Dr. Small mentioned, you do need Nano or some other terminal based editor to open the xorg file. Sorry!

---

### Post by benevolent on 2007-10-08
hm... no, I didn't use any special options!!!


let me start over.. I was running ubuntu.. I used to have nvidia (due to hardware problems @$@%#^) and i changed with my new ati!!! Everything was cool!!! except 3d acceleration!!! So i tried to install drivers from [www.ati.com](www.ati.com) manually (sh atidrivers.run)

I installed them... and at the next reboot, I'm having this problem.. X server error!!!


Also, i think i messed things up the first time i try to dpkg-configure....


And at /etc/x11 there are many xorg.conf files :P :think:


please please help me :(

---

### Post by jonathanmotes on 2007-10-08
OK, well, the xorg configuration file that I was talking about is named xorg.conf. 

Also, this: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` completely reconfigures and "overwrites" any changes that the "dkpg-reconfigure xserver" did (to the xorg configuration file). Can you verify that you tried the code above and then rebooted? 

Also, ATI has supposed to have released some new open source drivers (maybe that is what you were installing?). I know the updates yesterday (at least in Gutsy) included one that I think is supposed to have 3D acceleration. If you have a wired internet connection, you might want to try doing ```
sudo apt-get update
``` and then doing the "dpkg-reconfigure -phigh xserver-xorg" again.

By the way, if you are getting to a terminal prompt to enter commands by booting in recovery mode, you don't need to include "sudo" when entering any of the commands. And if you are booting in recovery, you can try typing "startx" (without the quotes) after reconfiguring the xorg file to see if you can start the graphics server with root permissions to try and enable different graphics drivers....but I'm not sure this is a good idea....

A final note: If you manage to get to a desktop and don't have a 3D desktop, look in the restricted drivers manager and see if there is a driver in there for your card (if you haven't already done so).

If all else fails, you can reinstall. You will quite possibly have a 3D driver available in the updates.

I hope this helps!

---

### Post by dz0004455 on 2007-10-08
i would try using envy, look it up, and if it doesnt work, try to boot using an older linux kernel and wait for the newer drivers to come out.  I always wait to update the kernel, until i can get the linux headers compatible with the nvidia driver. i think

---

### Post by benevolent on 2007-10-09
hm... well...


I can verify because I follow the steps from* [here](http://users.bigpond.net.au/hermanzone/p7.html)*

I try with ati, vesa and vga!!!

maybe this error output might help you (to help me)


> 
(WW) RADEON: No mathcing device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected

fatal server error, no screens found



till your next answers, I'll try to boot previously kernels or try recovery mode!!!


thx again!!!!! :neutral:


Also, when I'm typing lspci -x | grep -i "vga\|display" I get

> 01:00.0 VGA compatible controller:ATI Technologies Inc unknown device 71c1 (rev 9e)
01:00.1 Display Controller: ATI Technologies Inc Unknown device 71e1 (rev 9e)

---

### Post by benevolent on 2007-10-11
anyone please????

---

### Post by Talldarknfugly on 2007-10-14
> **benevolent said:**
> hm... no, I didn't use any special options!!!


let me start over.. I was running ubuntu.. I used to have nvidia (due to hardware problems @$@%#^) and i changed with my new ati!!! Everything was cool!!! except 3d acceleration!!! So i tried to install drivers from [www.ati.com](www.ati.com) manually (sh atidrivers.run)

I installed them... and at the next reboot, I'm having this problem.. X server error!!!


Also, i think i messed things up the first time i try to dpkg-configure....


And at /etc/x11 there are many xorg.conf files :P :think:


please please help me :(
What a coincidence that you're having this same issue about the same time I am.
Mine started tonight and I've spent about 6hrs trouble-shooting it so here's what worked for me.
Remember the xorg.config files that you said you have in excess?
They're all backed up versions for each time you do an update.
The task is to check for the OLDEST one of those files (hopefully u didnt delete it)
That last file, run a cat command on it, and browse through it. There you will find your pc config so you dont have to use the generic "vesa"
For me, mine was i810 or something like that. Once you find it, run the dpkg reconfigure command again and this time, use the driver name you found in that document to update.

Thats what I did and after 6hrs of CLI, voilla! Back in business
Good luck

---

