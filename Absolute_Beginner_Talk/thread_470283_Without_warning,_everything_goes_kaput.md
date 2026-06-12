---
title: "Without warning, everything goes kaput"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by sdrawkcab on 2007-06-10
I just recently installed Ubuntu onto my external hard drive (with a lot of problems still, for the love of God read my other threads and help me! ](*,)  ) . But there is one problem that occasionally arises that gives me no choice but to force shutdown the computer. I think it must be from the mouse that I'm using, 'cause I don't seem to have the problem unless I am using my wireless USB mouse. 

The problem is this: Ubuntu stops everything that's happening and seems to be thinking very hard. After a couple of minutes it allows me to do stuff. The catch is, NOTHING WORKS! There are no icons to be seen, just the    [x]    image. And when I try to restart by going to the power menu, restart and shutdown are not displayed. 

Also, I tried opening a command line through the applications bar, but any sort of file that I try always tells me that it can't be used because it's not there. I haven't tried opening a command line with my keyboard shortcut though...

The mouse is one of those Microsoft mouses of which on the box it says it's the #1 best selling wireless mouse, blah blah, blah... Sorry I can't describe it better than that though.

One more thing. Ubuntu does not immediately freak out when the mouse is plugged in. Just suddenly without warning. As the title implies. 

THANKS IF YOU HELP!

---

### Post by pontifex3 on 2007-06-10
could you post the output from /var/log/Xorg.0.log

---

### Post by sdrawkcab on 2007-06-12
Thanks for replying!

It just said the following:

"bash: /var/log/Xorg.0.log : Permission Denied"

If I may, can I ask what you think is going on here?

---

### Post by w4ett on 2007-06-12
try using:

sudo gedit  /var/log/Xorg.0.log

Copy and past the contents here.

---

### Post by sdrawkcab on 2007-06-13
> 
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux john-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 12 23:38:45 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc RC410 [Radeon Xpress 200M]"
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
(II) PCI: 00:00:0: chip 1002,5a31 card 1179,ff10 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 1179,ff10 rev 80 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 1179,ff10 rev 80 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1179,ff10 rev 80 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1179,ff10 rev 80 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 1179,ff10 rev 81 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 1179,ff10 rev 80 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,437b card 1179,ff10 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 1179,ff10 rev 80 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 80 class 06,04,01 hdr 81
(II) PCI: 01:05:0: chip 1002,5a62 card 1179,ff10 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:04:0: chip 168c,001a card 144f,7094 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:06:0: chip 1524,1410 card a400,0000 rev 01 class 06,07,00 hdr 02
(II) PCI: 02:07:0: chip 10ec,8139 card 1179,ff10 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc02fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:6:0), (2,3,3), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[1] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc RC410 [Radeon Xpress 200M] rev 0, Mem @ 0xd0000000/28, 0xc0100000/16, I/O @ 0x9000/8
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
	[0] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[2] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[3] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[4] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[5] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[6] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[7] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[17] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[18] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[19] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[20] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[21] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[2] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[3] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[4] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[5] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[6] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[7] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[17] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[18] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[19] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[20] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[21] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
	[4] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[8] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[9] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[10] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[11] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[23] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[24] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[25] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[26] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[27] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
(==) AIGLX enabled
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
	compiled for 7.1.0, module version = 8.34.8
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
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(--) Chipset Supported AMD Graphics Processor (0x5A62) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[8] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[9] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[10] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[11] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[23] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[24] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[25] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[26] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[27] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6820
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[8] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[9] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[10] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[11] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[26] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[27] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[28] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[29] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[30] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[31] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
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
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5a62)
(--) fglrx(0): (PciSubVendor = 0x1179, PciSubDevice = 0xff10)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200M Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS4 
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
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) fglrx(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  LGPhilipsLCD
(II) fglrx(0):  LP154W01-TLA2
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00320c000000000000
(II) fglrx(0): 	000f0102802115780a0f109758528828
(II) fglrx(0): 	23505400000001010101010101010101
(II) fglrx(0): 	010101010101d51b00a0502017303020
(II) fglrx(0): 	26002115100000190000000000000000
(II) fglrx(0): 	00000000000000000000000000fe004c
(II) fglrx(0): 	475068696c6970734c43440a000000fe
(II) fglrx(0): 	004c503135345730312d544c41320008
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 301/266MHz @ 60Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.25  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0):  Default mode "1024x768": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.25  1024 1200 1232 1440  768 786 792 823
(**) fglrx(0):  Default mode "848x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.25  848 1112 1144 1440  480 642 648 823
(**) fglrx(0):  Default mode "800x600": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "720x576": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   71.25  720 1048 1080 1440  576 690 696 823
(**) fglrx(0):  Default mode "720x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.25  720 1048 1080 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.25  640 1008 1040 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x400": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.25  640 1008 1040 1440  400 602 608 823
(**) fglrx(0):  Default mode "640x350": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.25  640 1008 1040 1440  350 577 583 823
(**) fglrx(0):  Default mode "512x384": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.25  512 944 976 1440  384 594 600 823
(**) fglrx(0):  Default mode "400x300": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.25  400 888 920 1440  300 702 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.25  320 848 880 1440  240 642 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.25  320 848 880 1440  200 602 608 823 doublescan
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.25  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0):  Default mode "1024x768": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.25  1024 1200 1232 1440  768 786 792 823
(**) fglrx(0):  Default mode "848x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.25  848 1112 1144 1440  480 642 648 823
(**) fglrx(0):  Default mode "800x600": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "720x576": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   71.25  720 1048 1080 1440  576 690 696 823
(**) fglrx(0):  Default mode "720x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.25  720 1048 1080 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.25  640 1008 1040 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x400": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.25  640 1008 1040 1440  400 602 608 823
(**) fglrx(0):  Default mode "640x350": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.25  640 1008 1040 1440  350 577 583 823
(**) fglrx(0):  Default mode "512x384": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.25  512 944 976 1440  384 594 600 823
(**) fglrx(0):  Default mode "400x300": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.25  400 888 920 1440  300 702 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.25  320 848 880 1440  240 642 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.25  320 848 880 1440  200 602 608 823 doublescan
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[7] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[8] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[9] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[10] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[11] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[12] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[13] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[14] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[29] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[30] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[31] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[32] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[33] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[34] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
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
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7c04000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x1c000000 FBMappedSize: 0x005e9000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots




Sorry, the stuff exceeded the amount of characters allowed for one post.

---

### Post by sdrawkcab on 2007-06-13
Here's the rest of it.

> (II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Interrupt handler installed at IRQ 22.
(II) fglrx(0): Exposed events to the /proc interface
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
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
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

---

