---
title: "Random problems"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Tigairius on 2007-06-07
I've had so many problems with Ubuntu so far, I randomly get X Server errors, I've had to reconfigure the XServer-Xorg stuff four times. Sometimes I get XServer errors, I just restart my computer and it works perfectly. Sometimes I can't open just.. random programs. Sometimes things won't unpack, sometimes my sound won't work. Sometimes when I try to log on I get that "10 second" error. Just a bunch of random errors that are usually fixed by restarting the computer, it's just really inconvenient, is there any way I could fix these?

---

### Post by meatpan on 2007-06-07
Yes.

I can almost guarantee that others have encountered the same problems as you.  If not, then we'll help you figure it out.  Approach each problem on its own (it seems less overwhelming this way), and for each problem, try to post as many details and observations as possible.    

I recommend tackling the x-windows problems first.  X server crashes are typically reported in /var/log/Xorg.0.log.   Posting this file might help some people debug your problem.   Also, write down the hardware specs you have, and be sure to include the video card.

---

### Post by Tigairius on 2007-06-07
Xorg.0.log:
[PHP]

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Tigairius 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  7 17:40:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "COMPAQ FP7317"
(**) |   |-->Device "NVIDIA GeForce 6200"
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
(II) PCI: 00:00:0: chip 8086,2570 card 1043,80a5 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1043,8095 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0221 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:0a:0: chip 11c1,044c card 11c1,044c rev 02 class 07,80,00 hdr 00
(II) PCI: 02:0e:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:0f:0: chip 10ec,8139 card 1043,80b3 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf3d00000 - 0xf7dfffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd3c00000 - 0xf3bfffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf7e00000 - 0xf7efffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xf6000000/24, 0xe0000000/28, 0xf5000000/24, BIOS @ 0xf7de0000/17
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
	[0] -1	0	0xf7eff800 - 0xf7eff8ff (0x100) MX[B]
	[1] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[2] -1	0	0xf7eff000 - 0xf7eff7ff (0x800) MX[B]
	[3] -1	0	0xf7effc00 - 0xf7effcff (0x100) MX[B]
	[4] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[5] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[6] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[7] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf7eff800 - 0xf7eff8ff (0x100) MX[B]
	[1] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[2] -1	0	0xf7eff000 - 0xf7eff7ff (0x800) MX[B]
	[3] -1	0	0xf7effc00 - 0xf7effcff (0x100) MX[B]
	[4] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[5] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[6] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[7] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
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
	[4] -1	0	0xf7eff800 - 0xf7eff8ff (0x100) MX[B]
	[5] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[6] -1	0	0xf7eff000 - 0xf7eff7ff (0x800) MX[B]
	[7] -1	0	0xf7effc00 - 0xf7effcff (0x100) MX[B]
	[8] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[9] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[10] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[11] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[14] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7eff800 - 0xf7eff8ff (0x100) MX[B]
	[5] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[6] -1	0	0xf7eff000 - 0xf7eff7ff (0x800) MX[B]
	[7] -1	0	0xf7effc00 - 0xf7effcff (0x100) MX[B]
	[8] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[9] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[10] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[11] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[14] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7eff800 - 0xf7eff8ff (0x100) MX[B]
	[5] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[6] -1	0	0xf7eff000 - 0xf7eff7ff (0x800) MX[B]
	[7] -1	0	0xf7effc00 - 0xf7effcff (0x100) MX[B]
	[8] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[9] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[10] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[11] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[14] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[24] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[34] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.05.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     COMPAQ FP7317 (CRT-0)
(--) NVIDIA(0): COMPAQ FP7317 (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (78, 72); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf7eff800 - 0xf7eff8ff (0x100) MX[B]
	[8] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[9] -1	0	0xf7eff000 - 0xf7eff7ff (0x800) MX[B]
	[10] -1	0	0xf7effc00 - 0xf7effcff (0x100) MX[B]
	[11] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[12] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[13] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[14] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[15] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[16] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[17] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
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
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
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
[/PHP]

Graphics Card: NVidia GeForce 6200
120GB hd, 1.5GB ram, 2.60 GHz, 

I am running Ubuntu 7.04 on a slave drive.

Should I also post Xorg.0.log.old and Xorg.20.log?

---

### Post by Rocket2DMn on 2007-06-07
The X-server errors sound like you may have a driver issue, or something is incorrectly configured.  Please post your xorg.conf file, too.

---

### Post by Tigairius on 2007-06-07
xorg.conf
[PHP]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce 6200"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Videoram	200000
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"COMPAQ FP7317"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6200"
	Monitor		"COMPAQ FP7317"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/PHP]

---

### Post by alien21010 on 2007-06-07
The fonts issue has been discussed previously on this board, at least if I remember correctly it has.  Basically you either have to symlink where the fonts are, or copy them into that directory.  I was having this same issue, copying the offending fonts resolved the issue.

---

### Post by Tigairius on 2007-06-07
Which directory do I need to copy the fonts in to? From which directory?

---

### Post by Tigairius on 2007-06-08
*poke*

---

### Post by Tigairius on 2007-06-08
Can I get some help please?

---

