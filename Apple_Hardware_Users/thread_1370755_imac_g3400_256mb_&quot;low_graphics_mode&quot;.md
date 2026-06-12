---
title: "imac g3/400 256mb &quot;low graphics mode&quot;"
date: 2010-01-02
forum: Apple Hardware Users
---

### Post by wriggary on 2010-01-02
Hello again, Ubuntu community!

Recently, while dropping off some aluminum at the local recycling center, a local school district van pulled up next to me and started to unload 20 or so used and retired Imacs.  Sensing an opportunity, I wandered over to the driver and asked him if there was anything wrong with these computers.  He responded that he had just cleaned them out of a lab being replaced with new intel Imacs.  As far as he knew, they all worked, but were old.  So I asked him if I could take one and fix it up for a friend that didn't have a computer.  He kindly obliged, and also took my email address in case the district had anything else that was just going to be thrown away or recycled.  Double score!

Later, back at the ranch, I snatch the power connect, usb keyboard, and mouse from another computer (PC) I had laying around. I fire the thing up, it chimes, and presents me with the smiling os8 face with the question mark.  Good.  Formatted.  I then zapped the PRAM and set the clock in open firmware.  This was my first foray into a mac based machine, and all seemed to be going well. I then downloaded the Xubuntu 8.10 alternate install powerpc disc image. (well, I accidentally downloaded the PS3 one first but found my mistake before I burned anything.)

So, I md5sum the iso, checks out against the md5 posted on the mirror, and I burn it using wodim on my (shh..) Arch Linux machine.  I then fire up the Imac, slide the disc in, and hold C on the keyboard.  Yaboot fires uo and presents me with a list of kernels from the disc.  I had never used an alternate install cd before, and was surprised at the amount of options available. (I'll never use a standard cd to install again!) 

I booted with the line: expert video=ofonly  based on advice I had read while googling around for installation tips.  The Debian installer comes up and I answer as sensibly as I could.  I did end up having to drop to a busybox prompt and *modprobe ide-scsi* to get it to mount the cd.  Otherwise I selected *xubuntu-desktop* and *OpenSSH server* so I could move stuff onto the Imac from my desktop or laptop if necessary.  Installed just fine.  I then installed yaboot onto the bootstrap partition, ejected the cd and went for the reboot option.

The imac chimes again, and boots through both stages of yaboot.  The initrd loads fine and progresses through the boot scripts.  At the end comes GDM.  I noticed that Uspash doesn't load, but I don't pay it much mind.  Besides.  I like console messages. 

While GDM is loading, the console flashes to a blank screen a few times, and comes up with the message:

Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) Unable to find a valid framebuffer device
(EE) r128(0); Failed to open framebuffer device, consult warning and/or errors above for possible reasons.
(EE) Screen(s) found, but none have a usable configuration.


Now, I have googled this extensively, and can't seem to find a resolution to this problem.   Here is what I have tried so far.

First, I ran dpkg-reconfigure xserver-xorg .  It asked me for the bus address, so I just used the device number from lspci: PCI:0:10:0 .  I restarted gdm from the terminal and waited for it to come back up again.  It came back with a failsafeX dialog saying that it could not find the video device at 0:10:0, so  I google that and find that one expresses itself in decimal, one in hex, so I convert 10h to 16d and use that for the device ID string in dpkg-reconfigure: PCI:0:16:0.  It comes back with the same error as when I started: unable to find a valid framebuffer device.

Next, I tried a few of the xorg.confs posted around on the internets.  One that just added the horiz and vert sync lines to the "Default configured device" ... another with all devices explicitly specified and different sync lines, but it still starts in failsafe under low graphics mode.

This is the model of imac i'm working with. [http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html]("http://http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html")

So now, I'm at a loss. What should I try next?

lspci -vv
```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes
	Capabilities: <access denied>
	Kernel driver in use: agpgart-uninorth
	Kernel modules: uninorth-agp

0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 RL/VR AGP
	Subsystem: ATI Technologies Inc Rage 128 RL/VR AGP
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 255 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at 94000000 (32-bit, prefetchable) [size=64M]
	Region 1: I/O ports at 0400 [disabled] [size=256]
	Region 2: Memory at 90000000 (32-bit, non-prefetchable) [size=16K]
	Expansion ROM at f1000000 [disabled] [size=128K]
	Capabilities: <access denied>

0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes
	Kernel modules: uninorth-agp

0001:10:12.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller (prog-if 10)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16 (500ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 52
	Region 0: Memory at 80082000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at 80084000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 02)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes
	Region 0: Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
	Kernel driver in use: macio

0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB (prog-if 10)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16 (750ns min, 21500ns max)
	Interrupt: pin A routed to IRQ 27
	Region 0: Memory at 80081000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB (prog-if 10)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16 (750ns min, 21500ns max)
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at 80080000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 16, Cache Line Size: 32 bytes
	Kernel modules: uninorth-agp

0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 16 (16000ns min, 16000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 41
	Region 0: Memory at f5200000 (32-bit, non-prefetchable) [size=2M]
	Expansion ROM at f5000000 [disabled] [size=1M]
	Kernel driver in use: gem
	Kernel modules: sungem

```

current xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Xorg.0.log

```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu-imac 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 09 March 2009  11:56:19AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  2 13:40:07 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open APM successful
(II) Loader magic: 0x101d55e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 RL/VR AGP rev 0, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, I/O @ 0x0f9f0374/0, BIOS @ 0x????????/262079348
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched r128 from file name r128.ids
(==) Matched r128 for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "r128"

(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] 0	0	0xffffffff - 0x00000000 (0xa0000) MS[B]
	[13] 0	0	0xffffffff - 0x00000000 (0xb0000) MS[B]
	[14] 0	0	0xffffffff - 0x00000000 (0xb8000) MS[B]
	[15] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[16] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[17] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[18] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[19] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[20] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
	[21] 0	0	0xffffffff - 0x00000000 (0xf00003b0) IS[B]
	[22] 0	0	0xffffffff - 0x00000000 (0xf00003c0) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(II) R128(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (==) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "UseFBDev" "true"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"

(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 4.1
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

If anyone has experience getting ubuntu to run on this machine or a similar, I'd love your help.

Gary

---

### Post by tiresia on 2010-01-02
Most probably you must edit your xorg.conf For imac/emac you should have a look on oswaldkelso's [blog]("http://oswaldkelso.blogspot.com/") and/or to his [howto]("http://forums.debian.net/viewtopic.php?f=16&t=20481") on the debian forum

Maybe you want to try Ubuntu, but for those old machines, debian is better suited (running xfce or better lxde)

---

### Post by wriggary on 2010-01-02
Well, tried this one from his [blog]("http://oswaldkelso.blogspot.com/2009_11_01_archive.html") for the 400-450 imac.  In addition to the type0 module not being found, (which i then commented out and restarted gdm && killall Xorg) still gives me the same "unable to find valid framebuffer device" error.  

Here is the Xorg.0.log from this attempt:

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu-imac 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 09 March 2009  11:56:19AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  2 20:07:50 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "iMac"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID").
(WW) FontPath is completely invalid.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open APM successful
(II) Loader magic: 0x101d55e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 RL/VR AGP rev 0, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, I/O @ 0x0f9f0374/0, BIOS @ 0x????????/262079348
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "r128"

(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] 0	0	0xffffffff - 0x00000000 (0xa0000) MS[B]
	[13] 0	0	0xffffffff - 0x00000000 (0xb0000) MS[B]
	[14] 0	0	0xffffffff - 0x00000000 (0xb8000) MS[B]
	[15] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[16] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[17] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[18] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[19] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[20] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
	[21] 0	0	0xffffffff - 0x00000000 (0xf00003b0) IS[B]
	[22] 0	0	0xffffffff - 0x00000000 (0xf00003c0) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "UseFBDev" "true"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"

(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 4.1
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

So next I try the one above it, listed for IMac 350.  Still get the "unable to find valid framebuffer device" list of errors/

Xorg.0.log:

```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu-imac 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 09 March 2009  11:56:19AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  2 20:20:06 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) No Layout section. Using the first mouse device.
(==) No Layout section. Using the first keyboard device.
(II) Open APM successful
(II) Loader magic: 0x101d55e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 RL/VR AGP rev 0, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, I/O @ 0x0f9f0374/0, BIOS @ 0x????????/262079348
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded even though the default is to disable it.
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched r128 from file name r128.ids
(==) Matched r128 for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "r128"

(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] 0	0	0xffffffff - 0x00000000 (0xa0000) MS[B]
	[13] 0	0	0xffffffff - 0x00000000 (0xb0000) MS[B]
	[14] 0	0	0xffffffff - 0x00000000 (0xb8000) MS[B]
	[15] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[16] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[17] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[18] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[19] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[20] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
	[21] 0	0	0xffffffff - 0x00000000 (0xf00003b0) IS[B]
	[22] 0	0	0xffffffff - 0x00000000 (0xf00003c0) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "CCEusecTimeout" "100000"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"

(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 4.1
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Just for fun, I tried the last one on that page, for the 500+ imacs, minus the wacom stuff, since I don't own a tablet.  Xorg starts with failsafe message about could not autodetect settings, please configure these yourself.

Xorg.0.log
```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu-imac 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 09 March 2009  11:56:19AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  2 20:29:27 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "AIGLX" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open APM successful
(II) Loader magic: 0x101d55e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 RL/VR AGP rev 0, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, I/O @ 0x0f9f0374/0, BIOS @ 0x????????/262079348
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(**) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "r128"

(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] 0	0	0xffffffff - 0x00000000 (0xa0000) MS[B]
	[13] 0	0	0xffffffff - 0x00000000 (0xb0000) MS[B]
	[14] 0	0	0xffffffff - 0x00000000 (0xb8000) MS[B]
	[15] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[16] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[17] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[18] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[19] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[20] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
	[21] 0	0	0xffffffff - 0x00000000 (0xf00003b0) IS[B]
	[22] 0	0	0xffffffff - 0x00000000 (0xf00003c0) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "SWcursor" "true"
(**) R128(0): Option "ForcePCIMode" "true"
(**) R128(0): Option "UseFBDev" "false"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) R128(0): initializing int10
(II) R128(0): No legacy BIOS found -- trying PCI

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x98) [0x100894a8]
1: [0x100344]
2: /usr/lib/xorg/modules//libint10.so(LockLegacyVGA+0x50) [0xf5faf70]
3: /usr/lib/xorg/modules//libint10.so(xf86ExtendedInitInt10+0x1e4) [0xf5ff254]
4: /usr/lib/xorg/modules//libint10.so(xf86InitInt10+0x28) [0xf5fade8]
5: /usr/lib/xorg/modules/drivers//r128_drv.so(R128PreInit+0x65c) [0xf6a8cec]
6: /usr/X11R6/bin/X(InitOutput+0xa90) [0x1006d320]
7: /usr/X11R6/bin/X(main+0x288) [0x10028c08]
8: /lib/libc.so.6 [0xf993b24]
9: /lib/libc.so.6 [0xf993ce0]
Saw signal 7.  Server aborting.

```

Hmm, thats different.  Anyway, I'll go through the Debian forums post and see if there is anything different in there.

---

### Post by wriggary on 2010-01-06
hmm, I feel such a fool. I guess I got too used to GRUB, and not having to update the boot sector to change kernel options.  

Anyway, I now have XFCE running at 1024x768 and either 16 or 24 bit color, under debian lenny.  The key to getting it to run X was to append nofb to the kernel line. 

```

# sudo vim /etc/yaboot.conf

```

And then add "nofb" to the append section on both kernels.  On my regular kernel start line, the installer had left the video=ofonly statement, so I removed that and added nofb in its place.  I did leave it on the backup kernel just in case I broke something by changing it. 

Then update yaboot.  use the -v switch for a giggle.
```

sudo ybin -v

```

Then a sudo reboot, and a startx or however you choose to start Xorg, and it works.  I assume at least 8.10 should run with that added to the kernel line.  This is the xorg.conf I am using on this machine:

```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
#	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	59-61
 	VertRefresh	75-117
EndSection

Section "Screen"
	Identifier	"Default Ssdudcreen"
	Monitor		"Configured Monitor"
EndSection

```

notice that fbdev is commented out.  You can just as well leave it out since it is commented and disregarded anyway.  Also notice that I am using a regular PC keyboard and mouse.  Some adjustments may be necessary if one uses a mac keyboard and mouse.

So to wrap up, use "nofb" in the kernel options and a good xorg.conf, and you're all set.

---

