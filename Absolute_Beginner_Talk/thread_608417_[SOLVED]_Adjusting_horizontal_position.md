---
title: "[SOLVED] Adjusting horizontal position"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Jeff78 on 2007-11-10
Does anyone know how you can adjust the horizontal position of a screen in Kubuntu? I have an nVidia go5200 on this laptop and a VGA out to a Samsung TV. The horizontal position of the image on the TV is about 20 pixels off and I cannot auto adjust or correct the position on the TV itself. I fixed this problem in Windows when I first got the TV by adjusting the settings in the nVidia control panel, but I cannot find those settings in nvidia-settings.

---

### Post by thingy on 2007-11-10
For VGA displays, if the display is slightly offest then you can use xvidtune to tweak the current mode and tell it to output the tweaked modeline.

Enter the tweaked modeline entry into your /etc/X11/xorg.conf file to use that mode for the tv.

Is it a HDTV? In which case, see if this helps:

[http://gentoo-wiki.com/HOWTO_Xorg_HDTV](http://gentoo-wiki.com/HOWTO_Xorg_HDTV)

oh...messing with xvidtune can be dangerous if you try and force the display to use modes its not capable off. This use to be true for CRT monitors in the old days at least...

jinesh

---

### Post by Jeff78 on 2007-11-10
When I try to adjust it in xvidtune it gives me the following after I hit "Left" twice, then "Test":

"Sorry: you have requested a mode-line That is not possible, or not supported by your hardware configuration"

It is a HDTV, 1360x768 resolution, but as for that guide, I really don't even know where to begin on that, which is why I posted this in this forum.

---

### Post by thingy on 2007-11-10
hmm

[http://www.nvnews.net/vbulletin/showthread.php?t=69539](http://www.nvnews.net/vbulletin/showthread.php?t=69539)

mentions that someone else also could not "test" a mode but they were able to see the modeline that would have been generated and when they added that modeline to the xorg.conf file, they saw the difference.

kinda a long winded way of doing this

---

### Post by thingy on 2007-11-10
btw, whats the model of the samsung hdtv?

does this modeline from the gentoo howto url i posted ealier apply to you?

```

#Modeline "Samsung-LE26-1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync # should work for LE32R51B / LE26Rx / LE26M5 / LE37R4 / LE40R5 (also works for Viewsonic N3760W !!!)
```

---

### Post by Jeff78 on 2007-11-10
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
EndSection
```

---

### Post by Jeff78 on 2007-11-10
Also, on the book that came with my TV it says it is an LN-T3242H TFT-LCD TV. That's all

---

### Post by thingy on 2007-11-10
Can you paste here or pastebin the xorg log file in /var/log... + the full xorg.conf

---

### Post by Jeff78 on 2007-11-10
Here is the log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux jeff-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 10 00:09:30 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
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
(II) PCI: 00:00:0: chip 8086,2570 card 1179,ff00 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1179,ff00 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1179,ff00 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1179,ff00 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1179,ff00 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1179,ff00 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24d6 card 1179,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0324 card 1179,ff00 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 104c,8026 card 1179,ff00 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:01:0: chip 10ec,8139 card 1179,ff00 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 168c,0013 card 144f,7057 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1179,0617 card 3400,0000 rev 33 class 06,07,00 hdr 02
(II) PCI: 02:06:0: chip 1179,0805 card 1179,ff00 rev 05 class 08,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc2000000 - 0xc20fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[1] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34M [GeForce FX Go5200] rev 161, Mem @ 0xc1000000/24, 0xe0000000/27
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[1] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[2] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[3] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[4] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[5] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[6] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[7] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[8] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[13] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[14] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[15] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[17] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[1] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[2] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[3] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[4] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[5] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[6] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[7] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[8] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[13] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[14] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[15] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[17] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
	[4] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[5] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[6] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[7] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[8] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[9] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[10] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[11] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[20] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[21] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[23] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[5] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[6] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[7] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[8] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[9] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[10] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[11] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[20] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[21] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[23] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[5] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[6] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[7] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[8] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[9] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[10] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[11] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[27] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.33.a4
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5200 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     SAMSUNG (CRT-0)
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): SAMSUNG (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 270.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):    
(II) NVIDIA(0):     "CRT:nvidia-auto-select+1280+0,DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2640 x 800
(--) NVIDIA(0): DPI set to (38, 39); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[1] 0	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[7] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[8] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[9] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[10] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[11] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[12] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[13] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[14] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[15] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[24] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[25] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[26] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[27] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[28] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[29] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[35] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[36] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[37] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "CRT:nvidia-auto-select+1280+0,DFP:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

Here is the xorg conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 50.0
    VertRefresh     43.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1280+0; DFP: 1280x720@60 +0+0, CRT: nvidia-auto-select +1280+0; DFP: 800x600@60 +0+0, CRT: nvidia-auto-select +800+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0; CRT: NULL, DFP: 1280x720@60 +0+0; CRT: NULL, DFP: 800x600@60 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1385+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
EndSection

```

---

### Post by thingy on 2007-11-11
Its hard to list out the exact steps that you need to carry out to resolve this since I don't have a similar setup of dual monitors using nVidia's TwinView. I used have such a setup but my secondary screen was a tiny 15" monitor and so I gave up using it.

I can however give you an overview of what is involved to resolve this:


0. Make a copy of your /etc/X11/xorg.conf file and keep it safe somewhere


1. Using nvidia-settings, setup the Samsung HDTV to be your one and only monitor (temporarily). The utility modifies your xorg.conf file and so we will revert back to the original file in later steps. It may ask you to log out and log back in again or reboot the machine for the changes to take effect.


2. Once the Samsung HDTV is your only default monitor, launch a terminal and type in "xvidtune"


3. Click the "Left" or "Right" button twice depending on whether you want the picture to shift left or right


4. Click the "Show" button in xvidtune window and make a copy of the line it outputs in the terminal window. E.g.

```

"1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync

```


5. Quit xvidtune and copy back your original xorg.conf file to /etc/X11/ overwriting the current one. This will restore your setup to how it was.


6. Reboot or log out and back in again. Confirm that you have both monitors working.


7. Edit your /etc/X11/xorg.conf file and in the following section:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
EndSection

```

add a line (from Step 4) such that it looks like this:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync      30.0 - 61.0
    VertRefresh    60.0 - 75.0
    # Samsung HDTV Modeline
    ModeLine       "1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
EndSection

```


8. Also, in the following section change the metamodes line as shown:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    # Old line -
    #Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    # New line -
    Option         "metamodes" "CRT: 1360x768 +1280+0, DFP: nvidia-auto-select +0+0"
EndSection

```


9. Save the xorg.conf file and test by rebooting X. IF you get any problems like X doesn't start, switch to a console window (CTRL + ALT + F1) and copy the original backed up xorg.conf back to /etc/X11/xorg.conf. Also make a copy of the Xorg.0.log file and paste it to this thread so that we can see what went wrong. Most probably it will be a syntax issue...

---

### Post by Jeff78 on 2007-11-11
Okay I got all the way through it and played around with it for almost an hour. The black bar on the left has been reduced to about 1/4 of its previous size, but pretty much no matter how much I adjust it to the left on xvidtune, it will not shrink any more than this.

Here is the log file:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux jeff-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 11 21:42:06 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
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
(II) PCI: 00:00:0: chip 8086,2570 card 1179,ff00 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1179,ff00 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1179,ff00 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1179,ff00 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1179,ff00 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1179,ff00 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24d6 card 1179,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0324 card 1179,ff00 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 104c,8026 card 1179,ff00 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:01:0: chip 10ec,8139 card 1179,ff00 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 168c,0013 card 144f,7057 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1179,0617 card 3400,0000 rev 33 class 06,07,00 hdr 02
(II) PCI: 02:06:0: chip 1179,0805 card 1179,ff00 rev 05 class 08,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc2000000 - 0xc20fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[1] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34M [GeForce FX Go5200] rev 161, Mem @ 0xc1000000/24, 0xe0000000/27
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[1] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[2] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[3] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[4] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[5] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[6] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[7] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[8] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[13] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[14] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[15] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[17] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[1] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[2] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[3] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[4] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[5] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[6] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[7] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[8] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[13] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[14] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[15] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[17] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
	[4] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[5] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[6] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[7] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[8] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[9] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[10] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[11] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[20] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[21] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[23] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[5] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[6] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[7] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[8] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[9] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[10] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[11] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[20] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[21] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[23] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[5] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[6] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[7] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[8] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[9] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[10] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[11] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[27] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1360x768 +1280+0, DFP: nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.33.a4
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5200 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     SAMSUNG (CRT-0)
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): SAMSUNG (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 270.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:1360x768+1280+0,DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2640 x 800
(--) NVIDIA(0): DPI set to (38, 39); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[1] 0	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc2014c00 - 0xc2014dff (0x200) MX[B]
	[7] -1	0	0xc2000000 - 0xc200ffff (0x10000) MX[B]
	[8] -1	0	0xc2014800 - 0xc20148ff (0x100) MX[B]
	[9] -1	0	0xc2010000 - 0xc2013fff (0x4000) MX[B]
	[10] -1	0	0xc2014000 - 0xc20147ff (0x800) MX[B]
	[11] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[12] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[13] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[14] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[15] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[24] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[25] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[26] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[27] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[28] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[29] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[35] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[36] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[37] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "CRT:1360x768+1280+0,DFP:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found

```

---

### Post by thingy on 2007-11-12
umm..Can you double check in Windows whether the resolution for the Samsung HDTV *is* 1360x768?

Also, if possible, find out what refresh rate Windows is running the display at.

Its good to know that the modeline did have an effect! :-)

---

### Post by Jeff78 on 2007-11-12
I won't be able to find out what refresh rate windows ran the display at , since I formatted the hard drive when I installed Kubuntu. As for the resolution.

Also, interesting, it says the resolution is 1366x768 and not 1360x768 according to several sites.

---

### Post by Jeff78 on 2007-11-12
Okay, it looks like changing the modeline to 1366x768 both in the monitor and screen sections allow me to move it past the previous point where it stopped. I believe all that is left now is to mess around with the positioning until I get it centered. Unfortunately I have to return to college in a few minutes, so I won't be able to play around with it until this weekend. Thanks for your help, thingy. I'll mark this as solved for now and send you a PM this weekend if everything goes right. Otherwise I'll reopen this.

---

### Post by sjcundy on 2008-03-01
I know this is an old post but in case someone else comes across the same issue.  I believe, if I understand your problem, the orientation of the display can actually be adjusted by the tv.  I have the same model and going into the menu under Setup->PC->AutoAdjust centered my display - no black bars.

---

