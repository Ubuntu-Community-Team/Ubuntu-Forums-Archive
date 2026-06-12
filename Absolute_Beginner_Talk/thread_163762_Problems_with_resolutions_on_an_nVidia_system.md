---
title: "Problems with resolutions on an nVidia system"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-04-21
Hello,

I've recently put together a new system, and am having problems selecting the resolution I want. Installation went great, apart from this issue.

Once the system was installed, I couldn't select 1280x1024. So I installed nVidias drivers via apt-get. This didn't improve the situation much. I finally edited xorg.conf and removed all entries and only added a "1280x1024" entry in it. Then all I got was 1280x800, which looks kind of funky.

Ubuntu/amd64 5.10
Asus V9400 (Actually a GeForce MX4000)

Does anyone know how I can get 1280x1024?

---

### Post by Jason_25 on 2006-04-21
Are you connected with dvi or analog?

Anyway, comment out DDC in your module section and add

```

Option		"NoDDC"		"true"
Option		"IgnoreEDID"	"true"

```

to your monitor section.

---

### Post by Iesos on 2006-04-21
Well, now I have. :-)

But it didn't work, unfortunately. No difference.

Any other ideas?

---

### Post by Jason_25 on 2006-04-21
Please post your Xorg.0.log and your xorg.conf

---

### Post by Iesos on 2006-04-21
This is my Xorg.0.log file


```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux johan 2.6.12-10-amd64-k8 #1 Sat Mar 11 16:23:07 UTC 2006 x86_64
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-amd64-k8 (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:23:07 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 21 21:51:11 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 1849,00e1 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1849,00e0 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1849,00e4 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1849,00e7 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1849,00e7 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1849,00e8 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1849,00df rev a2 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1849,00e5 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0185 card 1043,8193 rev c1 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 1102,0002 card 1102,8026 rev 07 class 04,01,00 hdr 80
(II) PCI: 02:08:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfca00000 - 0xfeafffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4900000 - 0xf48fffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0203 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0185) rev 193, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfeae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[1] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[6] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[9] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[10] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[12] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[13] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[14] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[1] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[6] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[9] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[10] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[12] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[13] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[14] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[19] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[20] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[21] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:16:27 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[19] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[20] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[21] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[22] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[23] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[24] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xE8000000
(--) NVIDIA(0): MMIO registers at 0xFD000000


(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 4000
(--) NVIDIA(0): VideoBIOS: 04.18.20.47.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(WW) NVIDIA(0): The user specified HorizSync "28.000-51.000" has been adjusted
(WW) NVIDIA(0):      to "30.000-51.000" (the intersection with EDID-specified
(WW) NVIDIA(0):      HorizSync "30.000-70.000")
(WW) NVIDIA(0): The user specified VertRefresh "43.000-60.000" has been
(WW) NVIDIA(0):      adjusted to "50.000-60.000" (the intersection with
(WW) NVIDIA(0):      EDID-specified VertRefresh "50.000-120.000"
(II) NVIDIA(0): Generic Monitor: Using hsync range of 30.00-51.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 50.00-60.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(0): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using mode "1280x1024" (no mode of this name)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): Display dimensions: (330, 250) mm
(--) NVIDIA(0): DPI set to (98, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[8] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[9] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[10] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[21] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[24] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[25] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[26] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x800"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
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

```

---

### Post by Iesos on 2006-04-21
continued:

```
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
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
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) NVIDIA(0): Setting mode "1024x768"
```

and my xorg.conf

```
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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
#	Option		"NoDDC"		"true"
#	Option		"IgnoreEDID"	"true"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
#	Driver		"nv"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
#		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Jason_25 on 2006-04-21
Ok there are errors in your xorg file.

Uncomment DRI and GLcore.  Comment DDC.

Option		"NoDDC"		"true"
Option		"IgnoreEDID"	"true"

Should be in the monitor section, uncommented.  Comment out DPMS.

If it still doesn't work, post the same thing again.

---

### Post by Iesos on 2006-04-21
Ok. I changed it, and it starts, but I still can't change my resolution. This is my present xorg.conf:

```
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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
#	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
#	Driver		"nv"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
#	Option		"DPMS"
	Option		"NoDDC"		"true"
	Option		"IgnoreEDID"	"true"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
#		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Jason_25 on 2006-04-21
Heh, sorry I overlooked it the first time, but I believe your horizsync and vertfrefresh are too low to allow for 1280x1024.  You might want to google for the right rates for your monitor.  For instance, mine is 

HorizSync	28-120
VertRefresh	20-85

Be careful, If you have a CRT, then the wrong rates may damage it.

---

### Post by Iesos on 2006-04-21
Thank you so much! It worked, just googled for my screen and changed the refresh rates. Thanks!

---

