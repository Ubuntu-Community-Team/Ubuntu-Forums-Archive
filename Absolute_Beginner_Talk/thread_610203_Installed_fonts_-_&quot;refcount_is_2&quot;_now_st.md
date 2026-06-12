---
title: "Installed fonts - &quot;refcount is 2&quot; now stuck at command line"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by JGT on 2007-11-11
Help! I tried to install Japanese fonts following the community documentation.

I now can't log in - if I type my password, I'm asked for it again. 

Logging in at the command line then typing "startx" produces a lot of text. The last line is as follows. Sorry if this is a bit inaccurate - I'm retyping from rough notes:

FreeFontPath: FPE "usr/share/fonts/X11/mics" refcount is 2: should be 1.

Please help - thank-you

John

---

### Post by Bachstelze on 2007-11-11
Could you please provide a link to the instructions you followed ?

---

### Post by JGT on 2007-11-11
Here it is. 

[https://help.ubuntu.com/community/Installing_Japanese_Input_and_Fonts](https://help.ubuntu.com/community/Installing_Japanese_Input_and_Fonts)

Thanks

John

---

### Post by Bachstelze on 2007-11-11
It would help if we could have a look at your Xorg log, it's located at /var/log/Xorg.0.log. If you're not comfortable with the command-line, use the live cd (or a Windows Ext3 driver if you're dual-booting) to fech it and post it here.

---

### Post by JGT on 2007-11-11
Thanks. Here it is via Live CD.

[Deleted - correct code below]

---

### Post by JGT on 2007-11-12
(bump)

---

### Post by Sandlst on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=138029]("http://ubuntuforums.org/showthread.php?t=138029")
I know it's a bit of a stretch, but the startx error message is the same, so I figured it was worth a shot, good luck!

---

### Post by bakeneko on 2007-11-13
The Xorg.0.log you posted --
Is it from /var/log under the liveCD environment, or retrieved from your hard drive (/media/disk/var/log or similar?)
We really need to be looking at the second.

---

### Post by JGT on 2007-11-14
bakeneko: Thanks for tip - here is the correct Xorg.0.log I'm sure!

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux john-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 15 00:08:42 2007
(==) Using config file: "/etc/X11/xorg.conf"
[(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL E196FP"
(**) |   |-->Device "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
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
(II) Loader magic: 0x81ea440
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 1028,01c4 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2582 card 1028,01c4 rev 04 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,2668 card 1028,01c4 rev 04 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1028,01c4 rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1028,01c4 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1028,01c4 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1028,01c4 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1028,01c4 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d4 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1028,01c4 rev 04 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2652 card 1028,01c4 rev 04 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1028,01c4 rev 04 class 0c,05,00 hdr 00
(II) PCI: 03:01:0: chip 11c1,5811 card 1028,8010 rev 61 class 0c,00,10 hdr 00
(II) PCI: 03:02:0: chip 11c1,0480 card 1668,0480 rev 00 class 07,80,00 hdr 00
(II) PCI: 03:08:0: chip 8086,1064 card 1028,01c4 rev 04 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xdff80000/19, 0xc0000000/28, 0xdff40000/18, I/O @ 0xecd8/3
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
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdfcfdf00 - 0xdfcfdfff (0x100) MX[B]
	[2] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[3] -1	0	0xdff3bc00 - 0xdff3bfff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xdff3c000 - 0xdff3ffff (0x4000) MX[B]
	[6] -1	0	0xdff40000 - 0xdff7ffff (0x40000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0x0000d4c0 - 0x0000d4ff (0x40) IX[B]
	[10] -1	0	0x0000d4b8 - 0x0000d4bf (0x8) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[14] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[15] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[16] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[17] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[18] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[26] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[27] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[28] -1	0	0x0000ecd8 - 0x0000ecdf (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdfcfdf00 - 0xdfcfdfff (0x100) MX[B]
	[2] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[3] -1	0	0xdff3bc00 - 0xdff3bfff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xdff3c000 - 0xdff3ffff (0x4000) MX[B]
	[6] -1	0	0xdff40000 - 0xdff7ffff (0x40000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0x0000d4c0 - 0x0000d4ff (0x40) IX[B]
	[10] -1	0	0x0000d4b8 - 0x0000d4bf (0x8) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[14] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[15] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[16] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[17] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[18] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[26] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[27] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[28] -1	0	0x0000ecd8 - 0x0000ecdf (0x8) IX[B](B)
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
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfcfdf00 - 0xdfcfdfff (0x100) MX[B]
	[6] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[7] -1	0	0xdff3bc00 - 0xdff3bfff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xdff3c000 - 0xdff3ffff (0x4000) MX[B]
	[10] -1	0	0xdff40000 - 0xdff7ffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d4c0 - 0x0000d4ff (0x40) IX[B]
	[16] -1	0	0x0000d4b8 - 0x0000d4bf (0x8) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[20] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[21] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[22] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[23] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[32] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[33] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[34] -1	0	0x0000ecd8 - 0x0000ecdf (0x8) IX[B](B)
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.1
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfcfdf00 - 0xdfcfdfff (0x100) MX[B]
	[6] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[7] -1	0	0xdff3bc00 - 0xdff3bfff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xdff3c000 - 0xdff3ffff (0x4000) MX[B]
	[10] -1	0	0xdff40000 - 0xdff7ffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d4c0 - 0x0000d4ff (0x40) IX[B]
	[16] -1	0	0x0000d4b8 - 0x0000d4bf (0x8) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[20] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[21] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[22] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[23] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[32] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[33] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[34] -1	0	0x0000ecd8 - 0x0000ecdf (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfcfdf00 - 0xdfcfdfff (0x100) MX[B]
	[6] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[7] -1	0	0xdff3bc00 - 0xdff3bfff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xdff3c000 - 0xdff3ffff (0x4000) MX[B]
	[10] -1	0	0xdff40000 - 0xdff7ffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d4c0 - 0x0000d4ff (0x40) IX[B]
	[19] -1	0	0x0000d4b8 - 0x0000d4bf (0x8) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[23] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[24] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[25] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[26] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[35] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[36] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[37] -1	0	0x0000ecd8 - 0x0000ecdf (0x8) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFF80000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section DELL E196FP
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: DEL  Model: a015  Serial#: 827011157
(II) intel(0): Year: 2005  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Serial No: HC7605CE1K0U
(II) intel(0): Monitor name: DELL E196FP
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0010ac15a055304b31
(II) intel(0): 	330f010368261e78eeee91a3544c9926
(II) intel(0): 	0f5054a54b00714f8180010101010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300782d1100001e000000ff00484337
(II) intel(0): 	3630354345314b30550a000000fc0044
(II) intel(0): 	454c4c204531393646500a20000000fd
(II) intel(0): 	00384b1f530e000a202020202020007c
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "DEL", prod id 40981
(II) intel(0): Not using mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (380, 300) mm
(**) intel(0): DPI set to (85, 108)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdff40000 - 0xdff7ffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xdff80000 - 0xdfffffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[8] -1	0	0xdfcfdf00 - 0xdfcfdfff (0x100) MX[B]
	[9] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[10] -1	0	0xdff3bc00 - 0xdff3bfff (0x400) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xdff3c000 - 0xdff3ffff (0x4000) MX[B]
	[13] -1	0	0xdff40000 - 0xdff7ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000ecd8 - 0x0000ecdf (0x8) IS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d4c0 - 0x0000d4ff (0x40) IX[B]
	[23] -1	0	0x0000d4b8 - 0x0000d4bf (0x8) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[38] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[39] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[40] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[41] -1	0	0x0000ecd8 - 0x0000ecdf (0x8) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 110080 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 440316 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 4860 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x        1f820000 physical)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x        1f832000 physical)
(II) intel(0): 0x00040000-0x03037fff: front buffer (49120 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x03038000-0x03047fff: xaa scratch (64 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB)
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB)
(II) intel(0): 0x06000000-0x07ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x08000000-0x09ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xe0446000
(II) intel(0): [drm] mapped SAREA 0xe0446000 to 0xb7b7b000
(II) intel(0): [drm] framebuffer handle = 0xc0040000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0xdff80000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] init sarea width,height = 1280 x 1280 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x28008000
(II) intel(0): [drm] Back Buffer = 0xc4000000
(II) intel(0): [drm] Depth Buffer = 0xc5000000
(II) intel(0): [drm] textures = 0xc8000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x03038000 (pgoffset 12344)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x08000000 (pgoffset 32768)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 376 x 301
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xe0446000 at 0xb7b7b000
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4
(II) Open ACPI successful (/var/run/acpid.socket)
(II) APM registered successfully
(II) intel(0): Kernel reported 110080 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 440316 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 4092 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x        1f820000 physical)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x        1f832000 physical)
(II) intel(0): 0x00040000-0x02a37fff: front buffer (42976 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x02a38000-0x02a47fff: xaa scratch (64 kB)
(II) intel(0): 0x03000000-0x037fffff: back buffer (8192 kB)
(II) intel(0): 0x03800000-0x03ffffff: depth buffer (8192 kB)
(II) intel(0): 0x04000000-0x05ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xe0435000
(II) intel(0): [drm] mapped SAREA 0xe0435000 to 0xb7f65000
(II) intel(0): [drm] framebuffer handle = 0xc0040000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): [drm] Registers = 0xdff80000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] init sarea width,height = 1280 x 1024 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x28008000
(II) intel(0): [drm] Back Buffer = 0xc3000000
(II) intel(0): [drm] Depth Buffer = 0xc3800000
(II) intel(0): [drm] textures = 0xc4000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02a38000 (pgoffset 10808)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x03000000 (pgoffset 12288)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x03800000 (pgoffset 14336)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x04000000 (pgoffset 16384)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 376 x 301
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xe0435000 at 0xb7f65000
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4
```


[Sandlst: Thanks, but it didn't work - nothing to comment out really.]

---

