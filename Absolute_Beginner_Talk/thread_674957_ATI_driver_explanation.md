---
title: "ATI driver explanation"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-01-22
Hello,

If anyone hasn't done it already, it would be really nice for noobs like myself to have a document somewhere that explains, in noob-friendly verbage the following items and how these interact with each other, in regard to ATI drivers (for myself, ATI Radeon 9700 Pro).


1) Mesa
2) xorg
3) xfree86
4) fglrx (open source)
5) fglrx (closed source)
6) .ko & .so, and why one is better than the other

I've spent 3 days trying to get my ATI Radeon 9700 Pro to work.  Any driver causes lock ups with 1600 x 1200 resolution (when I logout).  I find myself getting confused as I search Ubuntu forums and google, trying to get it to work properly.  One website went into detail about using module-assistant (being noobish, I did it and didn't know exactly what I was doing).  After getting errors with that and emailing the author of the website instructions, he said it was no longer necessary to use the module-assistant.  Thus, many tutorials are out of date (it would be nice if WIKI's had a required date somewhere on the page) :) :)

How many drivers for the ATI Radeon 9700 exist??

---

### Post by djbsteart1 on 2008-01-22
have you tried alberto milone's envy? there is, i think , a tutorial that should cover this under multimedia, on the sticky part at the top if you havnt tried that already. also, if your using 7.10 the driver should be autodetected. it was for my nvidea card.

---

### Post by chewit on 2008-01-22
Your lucky, ATi actully do drivers for the 9000seres. I havw to use an open source driver for my ATi 7000.

BTW, omg thats a pretty amazing pc djbsteart1. 2 Ultra cards!!!! Insane!!! You must be able to run crysis on Max!!!

---

### Post by OffAxis on 2008-01-22
have you tried this page?
[https://help.ubuntu.com/community/BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")
or this page?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

your best bet performance wise is the Restricted Driver if you're having an issue. 
Regardless of the driver, every time your machine errors out it should write something to the log file. 

Within the log folder **/var/log** there'll be a **syslog **and an **xorg.log** (this one may be in an 'X11' sub-folder, I don't remember at the moment) file that should have some sort of error message to help you track down the problem.

---

### Post by aBitLater on 2008-01-22
Thanks OffAxis,

I reinstalled the proprietary driver according to the instructions at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 

fglrxinfo now reveals that I'm using:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO
OpenGL version string: 2.1.7276 Release


but when I run glxgears I get a lot of flashing and blanking over the whole screen.  I looked at the syslog and nothing much of interest there (not related to the time I ran glxgears).  Only this:

Jan 22 13:29:28 mycomputer kernel: [  614.164352] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000003 not found in mutex list

Then, in the Xorg.0.log file there was all this!  If this doesn't mean much to you or anyone else, can you point me to a place on the unbuntu forums or elsewhere that I might get help interpreting the log file?

> 

(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f000217 bridge: 0x8086/0x2530
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000314
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [pcie] 0 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xff7c0000 - 0xff7dffff (0x20000) MX[B]
	[7] -1	0	0xff7fc000 - 0xff7fcfff (0x1000) MX[B]
	[8] -1	0	0xff600000 - 0xff6fffff (0x100000) MX[B]
	[9] -1	0	0xff7fd000 - 0xff7fdfff (0x1000) MX[B]
	[10] -1	0	0xff7fe000 - 0xff7fefff (0x1000) MX[B]
	[11] -1	0	0xff7ff800 - 0xff7ff8ff (0x100) MX[B]
	[12] -1	0	0xff7ffc00 - 0xff7ffcff (0x100) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xff9e0000 - 0xff9effff (0x10000) MX[B](B)
	[16] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[17] -1	0	0xff900000 - 0xff91ffff (0x20000) MX[B](B)
	[18] -1	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B](B)
	[19] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 0	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[27] -1	0	0x0000dc70 - 0x0000dc7f (0x10) IX[B]
	[28] -1	0	0x0000dc80 - 0x0000dc9f (0x20) IX[B]
	[29] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[30] -1	0	0x0000dcc0 - 0x0000dcdf (0x20) IX[B]
	[31] -1	0	0x0000dce0 - 0x0000dcff (0x20) IX[B]
	[32] -1	0	0x0000ccf0 - 0x0000ccff (0x10) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
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
drmOpenByBusid: Searching for BusID PCI:1:0:0
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
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7897000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.45.4
(II) fglrx(0):     Date: Jan 16 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 19.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf0140000 FBMappedSize: 0x00960000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,1536)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 336
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		24 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "MergedFB" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
Receive enable interrupt ret message
...irqEnableMask: 20008000
...dwIRQEnableId: 00000004
Receive enable interrupt ret message
...irqEnableMask: 10000000
...dwIRQEnableId: 00000005
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
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
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
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
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0



---

### Post by djbsteart1 on 2008-01-23
thanks, it is, i use it to model tons of wierd graphic things. and it acts as a server to the office aswell. havnt tried crysis, boss isnt too happy about gaming at work,l sadly something like that is out of my price range:(

---

### Post by aBitLater on 2008-01-24
ok, hopefully someone will look at this thread again :)

I've been enabling and disabling the proprietary driver and installing the prop. driver from the terminal, etc.  

After using the prop. driver for ATI Radeon 9700 Pro and seeing that it was successfully installed (with fglrxinfo), I haved disabled it and reboot

Now, after reboot, fglrxinfo no longer works.  Terminal says "command not found".  I guess I don't understand fglrxinfo - is that an ATI command that comes with the prop. driver?

I tried glxinfo | grep -i dri and got this:
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL

but when I go to Screen And Graphics (GUI program under System / Administration), I click the graphics card tab and it says 
Graphics Card (ATI Radeon (fglrx))
Driver: ati - ATI Mach8, Mach32, Mach64, and Rage

is it correct that fglrx is a 'driver' and there are opensource fglrx drivers and proprietary fglrx drivers?

If glxinfo says I have DRI R300 Project (Mesa), why won't fglrxinfo work in terminal.  I've had this driver installed before and fglrxinfo worked, reporting the same thing that glxinfo now reports.

corn-fused in the midwest, USA :~)

---

