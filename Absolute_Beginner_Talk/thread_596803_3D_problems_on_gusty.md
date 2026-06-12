---
title: "3D problems on gusty"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-10-29
im running gusty and everything runs fine. But when i try to run any 3d game they never work. they just simply crash with no error and the resolution goes down to 640x800.. and displayconfig-gtk also does not launch when i try to change the drivers to see is that would help. what can i do to solve this problem?

---

### Post by Crafty Kisses on 2007-10-29
> **Benifited said:**
> im running gusty and everything runs fine. But when i try to run any 3d game they never work. they just simply crash with no error and the resolution goes down to 640x800.. and displayconfig-gtk also does not launch when i try to change the drivers to see is that would help. what can i do to solve this problem?

Post the following output:
```
glxinfo
```

---

### Post by Benifited on 2007-10-29
name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x31 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x32 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x6d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by Crafty Kisses on 2007-10-29
> **Benifited said:**
> name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x31 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x32 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x6d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Do you know if direct rendering is enabled?

---

### Post by Benifited on 2007-10-29
yes it is

---

### Post by Benifited on 2007-10-29
can any1 plz help me with this problem

---

### Post by Benifited on 2007-10-29
i just got this error when i tryed to check tha direct rendering

Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

---

### Post by Benifited on 2007-10-30
can any1 give me a link to a web site that might be able to help me with this problem

---

### Post by rockinJack on 2007-11-06
I get the exact same problem. 

lspci relevant output:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

```

driver package:

```
ii  xserver-xorg-video-ati    1:6.6.3-2ubuntu6          X.Org X server -- ATI display driver
```

xorg log follows:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux wasp 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov  6 22:47:56 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc RV350 AS [Radeon 9550]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
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
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0314 card 1106,0314 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1314 card 1106,1314 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2314 card 1106,2314 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3208 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4314 card 1106,4314 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7314 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,3349 card 1106,3349 rev 00 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1106,0571 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1106,3104 rev 90 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3287 card 1106,3287 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,81b9 rev 70 class 04,01,00 hdr 00
(II) PCI: 00:11:7: chip 1106,287e card 1106,287e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80a7 rev 7c class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,287b card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:13:1: chip 1106,287a card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 01:00:0: chip 1002,4153 card 174b,0190 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4173 card 174b,0191 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:00:0: chip 1106,287c card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 02:00:1: chip 1106,287d card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000cfff (0x3000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff500000 - 0xff5fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbff00000 - 0xdfefffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:19:0), (0,2,4), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:19:1), (0,5,5), BCTRL: 0x0007 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (2:0:0), (2,3,3), BCTRL: 0x0007 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (2:0:1), (2,4,4), BCTRL: 0x0007 (VGA_EN is cleared)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AS [Radeon 9550] rev 0, Mem @ 0xd0000000/27, 0xff5f0000/16, I/O @ 0xc000/8, BIOS @ 0xff5c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary) rev 0, Mem @ 0xc8000000/27, 0xff5e0000/16
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xff6ff400 - 0xff6ff4ff (0x100) MX[B]
	[1] -1	0	0xff6ff800 - 0xff6ff8ff (0x100) MX[B]
	[2] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[3] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[4] -1	0	0xff5e0000 - 0xff5effff (0x10000) MX[B](B)
	[5] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xff5c0000 - 0xff5dffff (0x20000) MX[B](B)
	[7] -1	0	0xff5f0000 - 0xff5fffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff6ff400 - 0xff6ff4ff (0x100) MX[B]
	[1] -1	0	0xff6ff800 - 0xff6ff8ff (0x100) MX[B]
	[2] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[3] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[4] -1	0	0xff5e0000 - 0xff5effff (0x10000) MX[B](B)
	[5] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xff5c0000 - 0xff5dffff (0x20000) MX[B](B)
	[7] -1	0	0xff5f0000 - 0xff5fffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
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
	[4] -1	0	0xff6ff400 - 0xff6ff4ff (0x100) MX[B]
	[5] -1	0	0xff6ff800 - 0xff6ff8ff (0x100) MX[B]
	[6] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xff5e0000 - 0xff5effff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xff5c0000 - 0xff5dffff (0x20000) MX[B](B)
	[11] -1	0	0xff5f0000 - 0xff5fffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[23] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[25] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
(II) ATI:  Candidate "Device" section "ATI Technologies Inc RV350 AS [Radeon 9550]".
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9600 AS (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff6ff400 - 0xff6ff4ff (0x100) MX[B]
	[5] -1	0	0xff6ff800 - 0xff6ff8ff (0x100) MX[B]
	[6] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xff5e0000 - 0xff5effff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xff5c0000 - 0xff5dffff (0x20000) MX[B](B)
	[11] -1	0	0xff5f0000 - 0xff5fffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[23] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[25] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
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
	[4] -1	0	0xff6ff400 - 0xff6ff4ff (0x100) MX[B]
	[5] -1	0	0xff6ff800 - 0xff6ff8ff (0x100) MX[B]
	[6] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xff5e0000 - 0xff5effff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xff5c0000 - 0xff5dffff (0x20000) MX[B](B)
	[11] -1	0	0xff5f0000 - 0xff5fffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[26] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xff5f0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "MergedFB" "true"
(**) RADEON(0): Option "CRT2HSync" "30-98"
(**) RADEON(0): Option "CRT2VRefresh" "50-160"
(**) RADEON(0): Option "CRT2Position" "RightOf"
(**) RADEON(0): Option "MetaModes" "1280x1024-1280x1024"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): Assuming overlay scaler buffer width is 1536
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9600 AS (AGP)" (ChipID = 0x4153)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(--) RADEON(0): BIOS at 0xff5c0000
(II) RADEON(0): AGP card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(II) RADEON(0): AGP Fast Write disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEON(0): Page flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 3
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 1 ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 4aed  Serial#: 16843009
(II) RADEON(0): Year: 2006  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.647 redY: 0.346   greenX: 0.292 greenY: 0.602
(II) RADEON(0): blueX: 0.149 blueY: 0.130   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 71 kHz, PixClock max 110 MHz
(II) RADEON(0): Monitor name: L1952H
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6ded4a01010101
(II) RADEON(0): 	01100103ea261e78eaec54a5584a9a26
(II) RADEON(0): 	215054a56a80314f454f614f81800101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000fd00384b1e
(II) RADEON(0): 	470b000a202020202020000000fc004c
(II) RADEON(0): 	31393532480a202020202020000000fc
(II) RADEON(0): 	000a2020202020202020202020200094
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 434c  Serial#: 16843009
(II) RADEON(0): Year: 2004  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Signal levels configurable
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 33  vert.: 25
(II) RADEON(0): Gamma: 2.72
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.630 redY: 0.328   greenX: 0.295 greenY: 0.600
(II) RADEON(0): blueX: 0.144 blueY: 0.070   whiteX: 0.282 whiteY: 0.298
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #5: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 70  vid: 19113
(II) RADEON(0): #7: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  310 x 230 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 98 kHz, PixClock max 230 MHz
(II) RADEON(0): Monitor name: F700P
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4c4301010101
(II) RADEON(0): 	010e01037c2119ace84ac5a1544b9924
(II) RADEON(0): 	12484cffff803159455961598180a940
(II) RADEON(0): 	d140a94aa94f863d00c05100304040a0
(II) RADEON(0): 	130036e61000001e000000fd0032a01e
(II) RADEON(0): 	6217000a202020202020000000fc0046
(II) RADEON(0): 	373030500a20202020202020000000fc
(II) RADEON(0): 	000a2020202020202020202020200049
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- TMDS
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Secondary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=30000
(II) RADEON(0): MergedFB mode forced on.
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): DFP table revision: 3
(II) RADEON(0): Panel infos found from DDC detailed: 1280x1024
(II) RADEON(0): Valid Mode from Detailed timing table: 1280x1024
(II) RADEON(0): Valid Mode from standard timing table: 640x480
(II) RADEON(0): Valid Mode from standard timing table: 800x600
(II) RADEON(0): Valid Mode from standard timing table: 1024x768
(II) RADEON(0): Valid Mode from standard timing table: 1280x1024
(II) RADEON(0): Valid Mode from established timing table: 1024x768
(II) RADEON(0): Valid Mode from established timing table: 1024x768
(II) RADEON(0): Valid Mode from established timing table: 832x624
(II) RADEON(0): Valid Mode from established timing table: 800x600
(II) RADEON(0): Valid Mode from established timing table: 800x600
(II) RADEON(0): Valid Mode from established timing table: 640x480
(II) RADEON(0): Valid Mode from established timing table: 640x480
(II) RADEON(0): Total of 12 mode(s) found.
(II) RADEON(0): Total number of valid DDC mode(s) found: 12
(II) RADEON(0): Validating CRTC2 modes for MergedFB ------------ 
(II) RADEON(0): CRT2 Monitor: Using hsync range of 30.00-98.00 kHz
(II) RADEON(0): CRT2 Monitor: Using vrefresh range of 50.00-160.00 Hz
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
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Total of 34 CRTC2 modes found for MergedFB------------ 
(II) RADEON(0): Modes for CRT1: ********************
(--) RADEON(0): Virtual size is 1280x1024 (pitch 1280)
(**) RADEON(0): *Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"  108.00  1024 1328 1440 1688  768 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"  108.00  1024 1328 1440 1688  768 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"  108.00  1024 1328 1440 1688  768 1025 1028 1066 -hsync -vsync
(**) RADEON(0):  Default mode "832x624": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"  108.00  832 1328 1440 1688  624 1025 1028 1066 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"  108.00  800 1328 1440 1688  600 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"  108.00  800 1328 1440 1688  600 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"  108.00  800 1328 1440 1688  600 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"  108.00  640 1328 1440 1688  480 1025 1028 1066 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"  108.00  640 1328 1440 1688  480 1025 1028 1066 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"  108.00  640 1328 1440 1688  480 1025 1028 1066 -hsync -vsync
(II) RADEON(0): Modes for CRT2: ********************
(--) RADEON(0): Virtual size is 1280x1024 (pitch 1280)
(**) RADEON(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
(**) RADEON(0):  Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x960"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
(**) RADEON(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) RADEON(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) RADEON(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) RADEON(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
(**) RADEON(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) RADEON(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) RADEON(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) RADEON(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
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
(**) RADEON(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RADEON(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RADEON(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) RADEON(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
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
(II) RADEON(0): Generating MergedFB mode list
(II) RADEON(0): Merged "1280x1024" (1280x1024) and "1280x1024" (1280x1024) to 2560x1024
(--) RADEON(0): MergedFB: Virtual width 2560
(--) RADEON(0): MergedFB: Virtual height 1024
(==) RADEON(0): MergedFB: DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xff5f0000 - 0xff5fffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xff6ff400 - 0xff6ff4ff (0x100) MX[B]
	[7] -1	0	0xff6ff800 - 0xff6ff8ff (0x100) MX[B]
	[8] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xff5e0000 - 0xff5effff (0x10000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xff5c0000 - 0xff5dffff (0x20000) MX[B](B)
	[13] -1	0	0xff5f0000 - 0xff5fffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[29] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[31] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit d0000000 0
(**) RADEON(0): Map: 0xd0000000, 0x08000000
(==) RADEON(0): Write-combining range (0xd0000000,0x8000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x8217ea0)
(**) RADEON(0): Read: 0x00080002 0x00040018 0x00000000
(**) RADEON(0): Read: rd=2, fd=24, pd=4
(**) RADEON(0): Read: 0x00000000 0x00000000 0x00000000
(**) RADEON(0): Read: rd=0, fd=0, pd=0
(**) RADEON(0): RADEONSaveMode returns 0x8217ea0
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
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf894e000
(II) RADEON(0): [drm] mapped SAREA 0xf894e000 to 0xb7c76000
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x07000a09 [AGP 0x1106/0x0314; Card 0x1002/0x4153]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xf0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7a3f000
(II) RADEON(0): [agp] ring read ptr handle = 0xf0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7a3e000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xf0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaf761000
(II) RADEON(0): [agp] GART texture map handle = 0xf0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xaf281000
(II) RADEON(0): [drm] register handle = 0xff5f0000
(II) RADEON(0): [dri] Visual configs initialized
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x1024    436502.80  2560 2608 2720 2968  1024 1025 1028 1066 (24,32) +H +V
1280x1024    436502.80  1280 1328 1440 1688  1024 1025 1028 1066 (24,32) +H +V
(**) RADEON(0): Pitch = 20971840 bytes (virtualX = 2560, displayWidth = 2560)
(**) RADEON(0): dc=10800, of=21600, fd=96, pd=2
(**) RADEON(0): Pitch = 20971840 bytes (virtualX = 2560, displayWidth = 2560)
(**) RADEON(0): dc=15750, of=31500, fd=140, pd=2
(**) RADEON(0): TMDS_PLL from 1fbb010f to 1fbb010f
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x8218850
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x8218850)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC2, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x0001008c 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=140, pd=1
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00010060 0x00000000 (0x0000bf00)
(**) RADEON(0): Wrote: rd=12, fd=96, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 201a7c7c
(**) RADEON(0): GRPH2_BUFFER_CNTL from 30004c4c to 20507c7c
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
(II) RADEON(0): Memory manager initialized to (0,0) (2560,8191)
(II) RADEON(0): Reserved area from (0,1024) to (2560,1026)
(II) RADEON(0): Largest offscreen area available: 2560 x 7165
(II) RADEON(0): Will use back buffer at offset 0x2800000
(II) RADEON(0): Will use depth buffer at offset 0x3200000
(II) RADEON(0): Will use 69632 kb for textures at offset 0x3c00000
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(**) RADEON(0): DRI Finishing init !
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 20
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xd7ffd000 is: 0xd7ffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf07ff000
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 201a7c7c
(**) RADEON(0): GRPH2_BUFFER_CNTL from 30004c4c to 20507c7c
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 320
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Option "XaaNoOffscreenPixmaps" "true"
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
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
(II) RADEON(0): Using hardware cursor (scanline 1026)
(II) RADEON(0): Largest offscreen area available: 2560 x 7163
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(II) RADEON(0): Initialized Radeon Pseudo-Xinerama extension
(II) RADEON(0): Pseudo-Xinerama: CRT1 (Screen 0) (0,0)-(1279,1023)
(II) RADEON(0): Pseudo-Xinerama: CRT2 (Screen 1) (1280,0)-(2559,1023)
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "abnt2"
(**) Generic Keyboard: XkbModel: "abnt2"
(**) Option "XkbLayout" "br"
(**) Generic Keyboard: XkbLayout: "br"
(**) Option "XkbVariant" "nodeadkeys"
(**) Generic Keyboard: XkbVariant: "nodeadkeys"
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
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
(II) AIGLX: Suspending AIGLX clients for VT switch
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x8217ea0)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC2, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00000000 0x00000000 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=0, fd=0, pd=0
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00080002 0x00040018 0x00000000 (0x0000bf00)
(**) RADEON(0): Wrote: rd=2, fd=24, pd=4
(**) RADEON(0): Ok, leaving now...
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(**) RADEON(0): RADEONEnterVT
(**) RADEON(0): RADEONModeInit()
1280x1024    436502.80  2560 2608 2720 2968  1024 1025 1028 1066 (24,32) +H +V
1280x1024    436502.80  1280 1328 1440 1688  1024 1025 1028 1066 (24,32) +H +V
(**) RADEON(0): Pitch = 20971840 bytes (virtualX = 2560, displayWidth = 2560)
(**) RADEON(0): dc=10800, of=21600, fd=96, pd=2
(**) RADEON(0): Pitch = 20971840 bytes (virtualX = 2560, displayWidth = 2560)
(**) RADEON(0): dc=15750, of=31500, fd=140, pd=2
(**) RADEON(0): TMDS_PLL from 1fbb010f to 1fbb010f
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x8218850
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x8218850)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xf07ff000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC2, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x0001008c 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=140, pd=1
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00010060 0x00000000 (0x0000bf00)
(**) RADEON(0): Wrote: rd=12, fd=96, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 201a7c7c
(**) RADEON(0): GRPH2_BUFFER_CNTL from 30004c4c to 20507c7c
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) RADEON(0): [agp] Mode 0x07000a09 [AGP 0x1106/0x0314; Card 0x1002/0x4153]
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSaveScreen(2)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```
xorg.conf follows:

```
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		 #Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		 #Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		 #Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
    Option      "MergedFB"	"true"
    Option      "CRT2Position" "RightOf"
	Option		"CRT2HSync"	"30-98"
	Option		"CRT2VRefresh"	"50-160"
    Option  "XAANoOffscreenPixmaps"	"true"
	Option		"MetaModes" "1280x1024-1280x1024"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	57-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
#    Option "Composite" "Enable"
EndSection


```

---

