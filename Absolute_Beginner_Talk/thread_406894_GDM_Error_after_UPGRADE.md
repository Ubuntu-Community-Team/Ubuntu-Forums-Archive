---
title: "GDM Error after UPGRADE"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by leep on 2007-04-11
Today I installed the automatic update from
Ubuntu, kernel 2.6.17-10-generic
to 
Ubuntu, kernel 2.6.17-11-generic

First problem: a grub error 15 "file not found", that i fixed manually editing /boot/grub/menu.lst (it's the second time this happens, why the hell everytime I upgrade my computer configuration I need to boot from live cd????)

Anyway, once edited the file, I rebooted my system. I obtained no startup error, but at the moment of starting GDM, I obtained an error "GDM could not start because of a configuration error" (or something like that).

How do I edit GDM configuration? How do I know where my config file is wrong?

Obviously, rebooting the pc with the old kernel, it works perfectly...

Thank you in advance,
S.

---

### Post by zvacet on 2007-04-11
```
gksudo gedit /etc/gdm/gdm.conf
```

---

### Post by leep on 2007-04-12
Thank you for your reply, but how do I know how to edit it, what to write inside it? And why it works with Ubuntu, kernel 2.6.17-10-generic and not with Ubuntu, kernel 2.6.17-11-generic?

---

### Post by leep on 2007-04-12
Any help?
I really don't know how to edit the file, nor to find what is my error...

---

### Post by Dual Cortex on 2007-04-12
Hmm... weird that GRUB isn't updated automatically, etc... Can't really help you out right now since I'm at school on a crippled-down XP computer :( Good luck for now!

---

### Post by leep on 2007-04-12
Dual Cortex: grub is updated, but with a new (wrong) version. It si configured to boot from hd3,3 instead od hd0,0, i don't know why.

I finally was able to find the X11 log file, but I'm unable to understand it:

X0rg.0.log

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux hs01 2.6.17-11-generic #2 SMP Tue Mar 13 23:32:38 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 12 22:45:41 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "PHILIPS M107"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 1043,0c11 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,006e card 1043,809a rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:04:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 01:0b:0: chip 1095,3112 card 1095,6112 rev 02 class 01,04,00 hdr 00
(II) PCI: 03:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000bfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdb000000 - 0xdcffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd9000000 - 0xdaffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(--) PCI:*(3:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xd9000000/24, 0xd0000000/27
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
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdc004000 - 0xdc0041ff (0x200) MX[B]
	[1] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[2] -1	0	0xdd085000 - 0xdd08503f (0x40) MX[B]
	[3] -1	0	0xdd084000 - 0xdd0847ff (0x800) MX[B]
	[4] -1	0	0xdd080000 - 0xdd080fff (0x1000) MX[B]
	[5] -1	0	0xdd000000 - 0xdd07ffff (0x80000) MX[B]
	[6] -1	0	0xdd086000 - 0xdd086fff (0x1000) MX[B]
	[7] -1	0	0xdd083000 - 0xdd0830ff (0x100) MX[B]
	[8] -1	0	0xdd082000 - 0xdd082fff (0x1000) MX[B]
	[9] -1	0	0xdd087000 - 0xdd087fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd9000000 - 0xd9ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[15] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdc004000 - 0xdc0041ff (0x200) MX[B]
	[1] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[2] -1	0	0xdd085000 - 0xdd08503f (0x40) MX[B]
	[3] -1	0	0xdd084000 - 0xdd0847ff (0x800) MX[B]
	[4] -1	0	0xdd080000 - 0xdd080fff (0x1000) MX[B]
	[5] -1	0	0xdd000000 - 0xdd07ffff (0x80000) MX[B]
	[6] -1	0	0xdd086000 - 0xdd086fff (0x1000) MX[B]
	[7] -1	0	0xdd083000 - 0xdd0830ff (0x100) MX[B]
	[8] -1	0	0xdd082000 - 0xdd082fff (0x1000) MX[B]
	[9] -1	0	0xdd087000 - 0xdd087fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd9000000 - 0xd9ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[15] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
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
	[4] -1	0	0xdc004000 - 0xdc0041ff (0x200) MX[B]
	[5] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[6] -1	0	0xdd085000 - 0xdd08503f (0x40) MX[B]
	[7] -1	0	0xdd084000 - 0xdd0847ff (0x800) MX[B]
	[8] -1	0	0xdd080000 - 0xdd080fff (0x1000) MX[B]
	[9] -1	0	0xdd000000 - 0xdd07ffff (0x80000) MX[B]
	[10] -1	0	0xdd086000 - 0xdd086fff (0x1000) MX[B]
	[11] -1	0	0xdd083000 - 0xdd0830ff (0x100) MX[B]
	[12] -1	0	0xdd082000 - 0xdd082fff (0x1000) MX[B]
	[13] -1	0	0xdd087000 - 0xdd087fff (0x1000) MX[B]
	[14] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd9000000 - 0xd9ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc004000 - 0xdc0041ff (0x200) MX[B]
	[5] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[6] -1	0	0xdd085000 - 0xdd08503f (0x40) MX[B]
	[7] -1	0	0xdd084000 - 0xdd0847ff (0x800) MX[B]
	[8] -1	0	0xdd080000 - 0xdd080fff (0x1000) MX[B]
	[9] -1	0	0xdd000000 - 0xdd07ffff (0x80000) MX[B]
	[10] -1	0	0xdd086000 - 0xdd086fff (0x1000) MX[B]
	[11] -1	0	0xdd083000 - 0xdd0830ff (0x100) MX[B]
	[12] -1	0	0xdd082000 - 0xdd082fff (0x1000) MX[B]
	[13] -1	0	0xdd087000 - 0xdd087fff (0x1000) MX[B]
	[14] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd9000000 - 0xd9ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc004000 - 0xdc0041ff (0x200) MX[B]
	[5] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[6] -1	0	0xdd085000 - 0xdd08503f (0x40) MX[B]
	[7] -1	0	0xdd084000 - 0xdd0847ff (0x800) MX[B]
	[8] -1	0	0xdd080000 - 0xdd080fff (0x1000) MX[B]
	[9] -1	0	0xdd000000 - 0xdd07ffff (0x80000) MX[B]
	[10] -1	0	0xdd086000 - 0xdd086fff (0x1000) MX[B]
	[11] -1	0	0xdd083000 - 0xdd0830ff (0x100) MX[B]
	[12] -1	0	0xdd082000 - 0xdd082fff (0x1000) MX[B]
	[13] -1	0	0xdd087000 - 0xdd087fff (0x1000) MX[B]
	[14] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd9000000 - 0xd9ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[26] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

And here is my xorg.conf file:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "it"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "PHILIPS M107"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "PHILIPS M107"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection


```

---

### Post by Dual Cortex on 2007-04-12
How did you install your nvidia driver?

---

### Post by leep on 2007-04-13
Thanks for replying. I cannot remember exactly, but I think  I did it with the apt-get software, I found a small tutorial on this forum with 3 or 4 different ways, and I choosed the simplest one.

---

### Post by Dual Cortex on 2007-04-13
Well, it seems the solution is to resintall the nvidia driver. 
To do this the easy way, do the following:>  
sudo dpkg-reconfigure -phigh xserver-xorg

then select vesa as the driver. Type startx and X will hopefully start. Then go here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Then download and install the current version of envy (0.9.1).
After installing, simply run the GUI and choose to install the nvidia drivers. Restart X, and everything should be fine.
[FONT=FreeSans]****[/FONT]

---

### Post by leep on 2007-04-16
I did what you wrote, it was not easy, but it finally works!
After I uninstalled nvidia drivers, I was able to boot the "new" kernel. Then I run nvidia drivers installation script, and rebooted, obtaining a Grub error. Then, I needed to fix this grub error before uninstalling and re-installing again nvidia drivers, but it seems it is working now.
Thank you very much Dual Cortex, without your help I would not be able to fix my pc.
S.

---

