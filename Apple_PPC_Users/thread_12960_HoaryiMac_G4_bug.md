---
title: "Hoary/iMac G4 bug?"
date: 2005-01-27
forum: Apple PPC Users
---

### Post by Michael Steinberg on 2005-01-27
The new Hoary Live CD loads beautifully on our Macs, except that the screen resolution on my G4 17-inch-LCD iMac is stuck at 640x480. What's odder is that the /etc/X11/xorg.conf file shows 1440x900 as the resolution, which happens to be correct. Is  there a way I can get the X server to pay attention to xorg.conf, can I fix this, or is this a bug? The Live CD has no problem getting the display right on our iBook G3 and PowerBook G4--the latter with a wide screen. 

Michael Steinberg
Rochester, NY

---

### Post by daniels on 2005-01-27
Could you please post your /var/log/Xorg.0.log and /etc/X11/xorg.conf so I can take a look?

---

### Post by Michael Steinberg on 2005-01-28
Happy to oblige with the files. BTW, the CD comes up fine on my wife's Mirror-Drive-doors dual-G4 with cinema display, but there are large patches of yellow (waxy yellow buildup?) on the screen where a menu had previously appeared, on buttons (as in the GIMP), and even on most of an image I opened in the GIMP.

But first things first:

/var/log/Xorg.o.log:


This is a pre-release version of the The X.Org Foundation X11.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the The X.Org Foundation "monolithic tree" CVS
repository hosted at [http://www.freedesktop.org/Software/xorg/](http://www.freedesktop.org/Software/xorg/)
X Window System Version 6.8.1.99 (Ubuntu 6.8.1-1ubuntu11 20050119010807 root@)
Release Date: 2 October 2004 + 6.8.x branch CVS
X Protocol Version 11, Revision 0, Release 6.8.1.99
Build Operating System: Linux 2.6.8.1 ppc [ELF] 
Current Operating System: Linux ubuntu 2.6.10-2-powerpc #1 Mon Jan 24 16:21:11 UTC 2005 ppc
Build Date: 19 January 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-2-powerpc (buildd@royal) (gcc version 3.3.5 (Debian 1:3.3.5-6ubuntu1)) #1 Mon Jan 24 16:21:11 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 28 14:42:27 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX AGP 8x (Mac)]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "UNKNOWN"
(**) XKB: layout: "UNKNOWN"
(**) Option "XkbOptions" "lv3:lwin_switch"
(**) XKB: options: "lv3:lwin_switch"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/Speedo,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(II) Open APM successful
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
	compiled for 6.8.1.99, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:0b:0: chip 106b,0034 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:10:0: chip 10de,0189 card 10de,0010 rev a2 class 03,00,00 hdr 00
(II) PCI: 10:0b:0: chip 106b,0035 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 10:17:0: chip 106b,003e card 0000,0000 rev 00 class ff,00,00 hdr 00
(II) PCI: 10:18:0: chip 106b,003f card 0000,0000 rev 00 class 0c,03,10 hdr 00
(II) PCI: 10:19:0: chip 106b,003f card 0000,0000 rev 00 class 0c,03,10 hdr 00
(II) PCI: 10:1a:0: chip 106b,003f card 0000,0000 rev 00 class 0c,03,10 hdr 00
(II) PCI: 20:0b:0: chip 106b,0036 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 20:0d:0: chip 106b,003b card 0000,0000 rev 00 class ff,00,00 hdr 00
(II) PCI: 20:0e:0: chip 106b,0031 card 106b,5811 rev 81 class 0c,00,10 hdr 00
(II) PCI: 20:0f:0: chip 106b,0032 card 0000,0000 rev 80 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,32), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 16: bridge is at (16:11:0), (16,16,32), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 16 I/O range:
	[0] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 16 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 16 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 32: bridge is at (32:11:0), (32,32,32), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 32 I/O range:
	[0] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 32 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 32 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:16:0) nVidia Corporation unknown chipset (0x0189) rev 162, Mem @ 0x91000000/24, 0x98000000/27, BIOS @ 0x90000000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[1] -1	0	0xf5000000 - 0xf5000fff (0x1000) MX[B]
	[2] -1	0	0xf5004000 - 0xf5007fff (0x4000) MX[B]
	[3] -1	0	0x80080000 - 0x80080fff (0x1000) MX[B]
	[4] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[5] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[6] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[7] -1	0	0x90000000 - 0x9001ffff (0x20000) MX[B](B)
	[8] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[9] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[1] -1	0	0xf5000000 - 0xf5000fff (0x1000) MX[B]
	[2] -1	0	0xf5004000 - 0xf5007fff (0x4000) MX[B]
	[3] -1	0	0x80080000 - 0x80080fff (0x1000) MX[B]
	[4] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[5] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[6] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[7] -1	0	0x90000000 - 0x9001ffff (0x20000) MX[B](B)
	[8] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[9] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0xf5000000 - 0xf5000fff (0x1000) MX[B]
	[4] -1	0	0xf5004000 - 0xf5007fff (0x4000) MX[B]
	[5] -1	0	0x80080000 - 0x80080fff (0x1000) MX[B]
	[6] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[7] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[8] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[9] -1	0	0x90000000 - 0x9001ffff (0x20000) MX[B](B)
	[10] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[11] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
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
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.1.99, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Reloading /usr/X11R6/lib/modules/extensions/libGLcore.a
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "speedo"
(II) Loading /usr/X11R6/lib/modules/fonts/libspeedo.a
Skipping "/usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o":  No symbols found
(II) Module speedo: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.1
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Speedo
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "v4l"
(II) Loading /usr/X11R6/lib/modules/drivers/linux/v4l_drv.o
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 0.0.1
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nv"
(II) Loading /usr/X11R6/lib/modules/drivers/nv_drv.o
(II) Module nv: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) v4l driver for Video4Linux
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 MX (Mac), Quadro4 NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	GeForce4 MX with AGP8X (Mac), Quadro4 280 NVS, Quadro4 380 XGL,
	Quadro NVS 50 PCI, GeForce4 448 Go, GeForce4 MX Integrated GPU,
	GeForce3, GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC,
	GeForce4 Ti 4600, GeForce4 Ti 4400, 0x0252, GeForce4 Ti 4200,
	Quadro4 900 XGL, Quadro4 750 XGL, Quadro4 700 XGL, GeForce4 Ti 4800,
	GeForce4 Ti 4200 with AGP8X, GeForce4 Ti 4800 SE, GeForce4 4200 Go,
	Quadro4 700 GoGL, Quadro4 980 XGL, Quadro4 780 XGL,
	GeForce FX 5800 Ultra, GeForce FX 5800, Quadro FX 2000,
	Quadro FX 1000, GeForce FX 5600 Ultra, GeForce FX 5600, 0x0313,
	GeForce FX 5600SE, 0x0316, 0x0317, GeForce FX Go5600,
	GeForce FX Go5650, Quadro FX Go700, 0x031D, 0x031E, 0x031F,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200SE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	GeForce FX 5200 (Mac), Quadro NVS 280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, 0x032F,
	GeForce FX 5900 Ultra, GeForce FX 5900, GeForce FX 5900XT,
	GeForce FX 5950 Ultra, Quadro FX 700, GeForce FX 5900ZT,
	Quadro FX 3000, GeForce FX 5700 Ultra, GeForce FX 5700,
	GeForce FX 5700LE, GeForce FX 5700VE, 0x0345, GeForce FX Go5700,
	GeForce FX Go5700, 0x0349, 0x034B, Quadro FX Go1000, Quadro FX 1100,
	0x034F, GeForce 6800 Ultra, GeForce 6800, GeForce 6800 LE, 0x0043,
	GeForce 6800 GT, 0x0049, Quadro FX 4000, Quadro FX 4400, 0x00C0,
	0x00C1, GeForce 6800 LE, 0x00C8, 0x00C9, 0x00CC, 0x00CE,
	GeForce 6600 GT, GeForce 6600, 0x0142, 0x0143, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, 0x0147, GeForce Go 6600,
	0x0149, 0x014B, 0x014C, 0x014D, Quadro FX 540, GeForce 6200, 0x0160,
	0x0166, 0x0210, 0x0211, 0x021D, 0x021E
(II) Primary Device is: PCI 00:10:0
(--) Chipset GeForce4 MX with AGP8X (Mac) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0xf5000000 - 0xf5000fff (0x1000) MX[B]
	[4] -1	0	0xf5004000 - 0xf5007fff (0x4000) MX[B]
	[5] -1	0	0x80080000 - 0x80080fff (0x1000) MX[B]
	[6] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[7] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[8] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[9] -1	0	0x90000000 - 0x9001ffff (0x20000) MX[B](B)
	[10] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[11] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0xf5000000 - 0xf5000fff (0x1000) MX[B]
	[4] -1	0	0xf5004000 - 0xf5007fff (0x4000) MX[B]
	[5] -1	0	0x80080000 - 0x80080fff (0x1000) MX[B]
	[6] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[7] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[8] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[9] -1	0	0x90000000 - 0x9001ffff (0x20000) MX[B](B)
	[10] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[11] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[18] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/libint10.a
(--) NV(0): Chipset: "GeForce4 MX with AGP8X (Mac)"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0x98000000
(--) NV(0): MMIO registers at 0x91000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1440 x 900
(--) NV(0): VideoRAM: 65536 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using default hsync range of 28.00-33.00 kHz
(II) NV(0): Generic Monitor: Using default vrefresh range of 43.00-72.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz


(continued in next post, where I think I see the problem: "no mode of the name "1440x900")

---

### Post by Michael Steinberg on 2005-01-28
Here's (perhaps) the good part, in the continuation of /var/log/Xorg.o.log. And thanks very much. BTW, I use Ubuntu exclusively on my work machine, for legal writing and research; it's a self-assembled barebones kit and I'm very very pleased with Ubuntu's performance and aesthetic appeal:

(II) NV(0): Not using default mode "640x350" (hsync out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (hsync out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1280x960" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1280x960" (unknown reason)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1280x960" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1280x960" (unknown reason)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1280x1024" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1280x1024" (unknown reason)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1280x1024" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1280x1024" (unknown reason)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1280x1024" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1280x1024" (unknown reason)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1792x1344" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1792x1344" (unknown reason)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1792x1344" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1792x1344" (unknown reason)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1856x1392" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1856x1392" (unknown reason)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1856x1392" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1856x1392" (unknown reason)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x768" (hsync out of range)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1400x1050" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1400x1050" (unknown reason)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1024" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1600x1024" (unknown reason)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1200" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1920x1200" (unknown reason)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1440 x 900.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using mode "1440x900" (no mode of this name)
(--) NV(0): Virtual size is 640x480 (pitch 640)
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(==) NV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.1.99, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x98000000 - 0x9fffffff (0x8000000) MX[B]
	[1] 0	0	0x91000000 - 0x91ffffff (0x1000000) MX[B]
	[2] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[4] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[5] -1	0	0xf5000000 - 0xf5000fff (0x1000) MX[B]
	[6] -1	0	0xf5004000 - 0xf5007fff (0x4000) MX[B]
	[7] -1	0	0x80080000 - 0x80080fff (0x1000) MX[B]
	[8] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[9] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[10] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[11] -1	0	0x90000000 - 0x9001ffff (0x20000) MX[B](B)
	[12] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[13] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[20] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
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
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "UNKNOWN"
(**) Generic Keyboard: XkbLayout: "UNKNOWN"
(**) Option "XkbOptions" "lv3:lwin_switch"
(**) Generic Keyboard: XkbOptions: "lv3:lwin_switch"
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
Could not init font path element unix/:7100, removing from list!




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
# again, run the following commands as root:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   md5sum /etc/X11/xorg.conf >/var/lib/xorg//etc/X11/xorg.conf.md5sum
#   dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"UNKNOWN"
	Option		"XkbOptions"	"lv3:lwin_switch"
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
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX AGP 8x (Mac)]"
	Driver		"nv"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX AGP 8x (Mac)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
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

---

### Post by daniels on 2005-01-28
Ah, so you have *that* bug ... fixed locally, will be in the next xorg upload.  Cheers for the files.

---

