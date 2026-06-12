---
title: "Power Macintosh G4 X fails on boot"
date: 2005-01-31
forum: Apple PPC Users
---

### Post by kyle.harms on 2005-01-31
I'm rather new to GNU/Linux but I really want to make it work.  I have a power macintosh G4 that I wiped and installed Ubuntu Warty on.  The installation went fine, however when booting X it will try and start 3 times.  The screen turns black and then comes back to the command prompt, then goes black again etc. 3 times.  Then I get a blue screen telling me that X couldn't be started.  I've searched the forums, googled, I cannot figure out what I need to do to get X working.  Does anyone have any ideas what could be wrong.

I'm not sure the exact specs of my particular Mac, but I know it is similar to this model:
[http://www.apple-history.com/frames/body.php?page=gallery&model=g4agp](http://www.apple-history.com/frames/body.php?page=gallery&model=g4agp)

I appreciate any pointers anyone may be able to give.

~Kyle

---

### Post by kyle.harms on 2005-02-01
I thought I should mention I also have a 17" Apple Studio Display.  I also saw in other posts that people were posting their log files and config files.  I'm not sure though what the error log is trying to tell me.


my XFree86.0.log file:
> This is a pre-release version of XFree86, and is not supported in any
way.  Bugs may be reported to [email]XFree86@XFree86.Org[/email] and patches submitted
to [email]fixes@XFree86.Org[/email].  Before reporting bugs in pre-release versions,
please check the latest version in the XFree86 CVS repository
([http://www.XFree86.Org/cvs](http://www.XFree86.Org/cvs)).

XFree86 Version 4.3.0.1 (Ubuntu 4.3.0.dfsg.1-6ubuntu25.1 20041117134317 root@)
Release Date: 15 August 2003
X Protocol Version 11, Revision 0, Release 6.6
Build Operating System: Linux 2.6.8.1 ppc [ELF] 
Build Date: 17 November 2004
	Before reporting problems, check [http://www.XFree86.Org/](http://www.XFree86.Org/)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.8.1-3-powerpc (buildd@royal) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 13:15:29 BST 2004 
Markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/XFree86.0.log", Time: Mon Jan 31 21:50:44 2005
(==) Using config file: "/etc/X11/XF86Config-4"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "StudioDispla"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xfree86"
(**) XKB: rules: "xfree86"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
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
(++) using VT number 7

(II) Open APM successful
(II) Module ABI versions:
	XFree86 ANSI C Emulation: 0.2
	XFree86 Video Driver: 0.6
	XFree86 XInput driver : 0.4
	XFree86 Server Extension : 0.2
	XFree86 Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:0b:0: chip 106b,0020 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:10:0: chip 1002,5046 card 0000,0000 rev 00 class 03,00,00 hdr 00
(II) PCI: 01:0b:0: chip 106b,001f card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 01:0d:0: chip 1011,0026 card 0000,0000 rev 05 class 06,04,00 hdr 01
(II) PCI: 02:07:0: chip 106b,0022 card 0000,0000 rev 03 class ff,00,00 hdr 00
(II) PCI: 02:08:0: chip 106b,0019 card 0000,0000 rev 00 class 0c,03,10 hdr 00
(II) PCI: 02:09:0: chip 106b,0019 card 0000,0000 rev 00 class 0c,03,10 hdr 00
(II) PCI: 02:0a:0: chip 104c,8020 card 0000,0000 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:0b:0: chip 106b,001e card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 03:0f:0: chip 106b,0021 card 0000,0000 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 1: bridge is at (1:11:0), (1,1,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (1:13:0), (1,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 3: bridge is at (3:11:0), (3,3,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:16:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/26, 0x90000000/14, I/O @ 0x0400/8, BIOS @ 0x90020000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[1] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[2] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[3] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[4] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[5] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[6] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[7] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[8] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[9] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[1] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[2] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[3] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[4] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[5] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[6] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[7] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[8] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[9] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[4] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[5] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[6] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[7] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[8] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[9] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[10] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[13] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_vertex.o":  No symbols found
(II) Module GLcore: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.2
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
(II) Module freetype: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 2.0.2
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Reloading /usr/X11R6/lib/modules/extensions/libGLcore.a
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/libint10.a
(II) Module int10: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.13.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "speedo"
(II) Loading /usr/X11R6/lib/modules/fonts/libspeedo.a
Skipping "/usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o":  No symbols found
(II) Module speedo: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.1
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Speedo
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.2
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "v4l"
(II) Loading /usr/X11R6/lib/modules/drivers/linux/v4l_drv.o
(II) Module v4l: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.0.1
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.1.0
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "xtt"
(II) Loading /usr/X11R6/lib/modules/fonts/libxtt.a
(II) Module xtt: vendor="X-TrueType Server Project & After X-TT Project"
	compiled for 4.3.0.1, module version = 1.4.1
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font xtt
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 6.5.5
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.4
(II) v4l driver for Video4Linux
(II) ATI: ATI driver (version 6.5.5) for chipset: ati
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
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon 9200PRO 5960 (AGP), ATI Radeon 9200 5961 (AGP),
	ATI Radeon 9200 5962 (AGP), ATI Radeon 9200SE 5964 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP), ATI Radeon Mobility 9600 (M10) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2 (M11) NV (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP)
(II) Primary Device is: PCI 00:10:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)".
(--) Chipset ATI Rage 128 Pro GL PF (AGP) found
(II) Loading sub module "r128"
(II) LoadModule: "r128"
(II) Loading /usr/X11R6/lib/modules/drivers/r128_drv.o
(II) Module r128: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 4.0.1
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[4] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[5] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[6] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[7] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[8] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[9] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[10] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[13] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[4] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[5] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[6] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[7] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[8] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[9] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[10] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
	[17] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[18] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.1.0
	ABI class: XFree86 Video Driver, version 0.6
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/libint10.a
(II) R128(0): initializing int10
(II) R128(0): No legacy BIOS found -- trying PCI
(EE) R128(0): Cannot read V_BIOS (5)
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID = 0x5046)
(--) R128(0): Linear framebuffer at 0x94000000
(--) R128(0): MMIO registers at 0x90000000
(--) R128(0): BIOS at 0x90020000
(--) R128(0): VideoRAM: 16384 kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(WW) R128(0): Video BIOS not detected in PCI space!
(WW) R128(0): Attempting to read Video BIOS from legacy ISA space!
(WW) R128(0): Video BIOS not found!
(WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=33 min=12500 max=25000; xclk=14000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.2.0
	ABI class: XFree86 Video Driver, version 0.6
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) R128(0): I2C device "DDC:ddc2" removed.
(EE) R128(0): No DFP detected
(II) R128(0): StudioDispla: Using hsync range of 78.00-82.00 kHz
(II) R128(0): StudioDispla: Using vrefresh range of 60.00-180.00 Hz
(II) R128(0): Clock range:  12.50 to 250.00 MHz
(II) R128(0): Not using default mode "640x350" (hsync out of range)
(II) R128(0): Not using default mode "320x175" (hsync out of range)
(II) R128(0): Not using default mode "640x400" (hsync out of range)
(II) R128(0): Not using default mode "320x200" (hsync out of range)
(II) R128(0): Not using default mode "720x400" (hsync out of range)
(II) R128(0): Not using default mode "360x200" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "320x240" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "320x240" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "320x240" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "320x240" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "832x624" (hsync out of range)
(II) R128(0): Not using default mode "416x312" (hsync out of range)
(II) R128(0): Not using default mode "1152x768" (hsync out of range)
(II) R128(0): Not using default mode "576x384" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1600x1024" (hsync out of range)
(II) R128(0): Not using default mode "800x512" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) R128(0): Virtual size is 1280x1024 (pitch 1280)
(**) R128(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) R128(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) R128(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
(**) R128(0):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) R128(0): Modeline "800x600"   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) R128(0):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) R128(0): Modeline "700x525"   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "640x512"   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync
(**) R128(0):  Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(II) R128(0): Modeline "576x432"   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync
(==) R128(0): DPI set to (75, 75)

---

### Post by kyle.harms on 2005-02-01
The end of the file:

> (II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
(II) Module fb: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.1.0
	ABI class: XFree86 Video Driver, version 0.6
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.1.0
	ABI class: XFree86 Video Driver, version 0.6
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 ANSI C Emulation, version 0.2
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x90000000 - 0x90003fff (0x4000) MS[B]
	[1] 0	0	0x94000000 - 0x97ffffff (0x4000000) MS[B]
	[2] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[4] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[5] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[6] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[7] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[8] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[9] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[10] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[11] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[12] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[16] 0	0	0x00000400 - 0x000004ff (0x100) IS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 7.  Server aborting


When reporting a problem related to a server crash, please send
the full server output, not just the last messages.
This can be found in the log file "/var/log/XFree86.0.log".
Please report problems to [email]debian-x@lists.debian.org[/email].


My XF86Config-4 file:
> # XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

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
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	Identifier	"StudioDispla"
	HorizSync	78-82
	VertRefresh	60-180
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Monitor		"StudioDispla"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by kyle.harms on 2005-02-11
Nevermind.  I reinstalled OS X.

I guess PPC linux has a small way to go yet.

---

### Post by trash on 2005-02-11
sorry i missed this post... I had the same problem...

are your horizsyn and vertrefresh rates correct for your monitor?
also change the default depth to 16

Section "Monitor"
Identifier "StudioDispla"
HorizSync 78-82
VertRefresh 60-180
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
Monitor "StudioDispla"
DefaultDepth 24


Partition your drive and install OSx and Warty, you won't regret it;)

---

### Post by kyle.harms on 2005-02-20
I'm using a 17" Apple Studio Display model number M7768.  This is a CRT monitor, not the LCD.

I saw other posts about changing the default depth, I did try that and it did not work.

I saw other posts about changing the refresh rates, I fooled with those, but I don't know how to find out the correct rates for my monitor.  It did not work.

If you have any other tips, I would glady re-install Ubuntu if I knew X would work.

I read some posts about frame buffers, is this a problem?  How do I figure out exactly why X is failing?  There seems to be no precise error message to tell me what is really wrong.

Thanks for your help.

Kyle

---

### Post by LususX on 2006-07-29
I have the same monitor with the same exact problem. I can't boot live with Drapper, but I can install with Breezy. X Windows doesn not start, with the same error as listed above.

---

