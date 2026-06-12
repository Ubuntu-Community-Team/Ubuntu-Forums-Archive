---
title: "G4 Ubuntu 8.10 low graphics mode help!"
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by scottmorabito on 2008-12-03
[COLOR="Red"]
Hi there, thanks to anyone who can point me in the right direction.

I just tried installing 8.10 on my PowerPC G4 400 and have gotten pretty far.  I have Gnome running ok but I cannot get it to use anything other than the low graphics mode. 

Here's what I have for my xorg.conf after various attempts and research.

I had been using driver ati for a bunch of test until I discovered I should be using r128
[/COLOR]
--

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
#Driver "ati"
Driver "r128"
BusID		"PCI:0:10:0"
#BusID		"PCI:0:16:0"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

[COLOR="red"]First off, I'm not exactly sure which BusID to specify.When I set the BusID to 10, I get "EE Not devices detected" When I set it to 16, I get "your sceen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself"

I'm pretty sure it should be 10 but the default xorg.failsaife has it as 16.  whatever.

Here's why I think it should be 10.
[/COLOR]

user@ubuntu-g4:~$ [COLOR="red"]lspci[/COLOR]
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 VGA compatible controller: ATI Technologies
Inc Rage 128 PF/PRO AGP 4x TMDS
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:0d.0 PCI bridge: Digital Equipment Corporation
DECchip 21154 (rev 05)
0001:11:07.0 Class ff00: Apple Computer Inc. KeyLargo Mac
I/O (rev 02)
0001:11:08.0 USB Controller: Apple Computer Inc. KeyLargo
USB
0001:11:09.0 USB Controller: Apple Computer Inc. KeyLargo
USB
0001:11:0a.0 FireWire (IEEE 1394): Texas Instruments
TSB12LV23 IEEE-1394 Controller
0002:21:0b.0 Host bridge: Apple Computer Inc. UniNorth
Internal PCI
0002:21:0f.0 Ethernet controller: Apple Computer Inc.
UniNorth GMAC (Sun GEM)

-------

user@ubuntu-g4:~$ [COLOR="red"]lspci -vv[/COLOR]
(only relivant info shown below)
0000:00:10.0 VGA compatible controller: ATI Technologies
Inc Rage 128 PF/PRO AGP 4x TMDS
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV-
VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium
TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 255 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at 94000000 (32-bit, prefetchable)
[size=64M]
	Region 1: I/O ports at 0400 [disabled] [size=256]
	Region 2: Memory at 90000000 (32-bit, non-prefetchable)
[size=16K]
	Expansion ROM at f1000000 [disabled] [size=128K]
	Capabilities: <access denied>

----

[COLOR="red"]Further, [/COLOR]

user@ubuntu-g4:~$ [COLOR="red"]sudo lshw -C display[/COLOR]
[sudo] password for user:
 *-display UNCLAIMED
      description: VGA compatible controller
      product: Rage 128 PF/PRO AGP 4x TMDS
      vendor: ATI Technologies Inc
      physical id: 10
      bus info: pci@0000:00:10.0
      version: 00
      width: 32 bits
      clock: 66MHz

----

[COLOR="red"]Here is the startup log where I'm running into the problem when I've selected device 10. I am guessing that I need to specify one of the r128 driver names that it gives from the choice below. The one I have selected now in xorg.conf (Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR") is from a working solution on a G3 iMac. [http://ubuntuforums.org/showpost.php?p=2321892&postcount=8]("http://ubuntuforums.org/showpost.php?p=2321892&postcount=8")  How do I find the right one? Am I on the right track?




[/COLOR]

------------------------------------------------------------------------
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu-g4 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 24 October 2008  08:07:47AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@ross.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  3 10:16:54 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, I/O @ 0x0f9f0374/0, BIOS @ 0x????????/262079348
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
(EE) No devices detected.

------------------------------------------------------------------------

Fatal server error:
no screens found

---

### Post by MEMyers on 2008-12-03
You have got further than myself, I can't get past 'looking for cd-rom driver' but I have a dvd r/w running the Cd install disk?  What I want to know is do I have to have a Mac OS already installed on the HD to run this install and do I have to worry about drivers for CPU?  What I have seen else where is that there has been a problem with Rage Pro graphic card but I would have thought with this 8.10 that this had been surmounted?  No answers just questions, sorry.

---

### Post by scottmorabito on 2008-12-10
Wow.  NOBODY?????

Am I on the wrong planet?

---

### Post by Leslie Viljoen on 2008-12-10
> **scottmorabito said:**
> [COLOR=Red]
[/COLOR]
[COLOR=red]First off, I'm not exactly sure which BusID to specify.When I set the BusID to 10, I get "EE Not devices detected" When I set it to 16, I get "your sceen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself"

I'm pretty sure it should be 10 but the default xorg.failsaife has it as 16.  whatever.

Here's why I think it should be 10.
[/COLOR]

One thing: 16 is 10 in hexadecimal. It could be that xorg uses decimal and the lspci has hex numbers - that would make 16 the correct value.

Sorry I can't be of more assistance, I have a radeon but not the same one. By "low graphics mode", do you mean you only have low resolution? What resolution do you get? 

I have modes like this:

  ```
SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600"
  EndSubSection
```

..so I get 1280x1024. I changed my driver to "fbdev" so I could get SDL programs to work - otherwise they all crash on my system. Though fbdev makes 3d very slow.

I did it like so:
```
Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200]"
        Driver          "fbdev"
EndSection
```

You may want to try fbdev and see if it makes any difference.

---

### Post by tiresia on 2008-12-11
> **MEMyers said:**
> You have got further than myself, I can't get past 'looking for cd-rom driver' but I have a dvd r/w running the Cd install disk? [http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)
>  What I want to know is do I have to have a Mac OS already installed on the HD to run this install and do I have to worry about drivers for CPU?NO!
> What I have seen else where is that there has been a problem with Rage Pro graphic card but I would have thought with this 8.10 that this had been surmounted?  No answers just questions, sorry. 
Please, start a new Thread!

---

### Post by greenbalot on 2009-01-06
I recently got an ATI rage 128 vr PCI card... my question is, can it work on Ubuntu 8.10 and what exactly do I have to do in order for it to work.

Im not really sure where to post this... 

I am a complete newbie (FYI):D

Thank you...

---

### Post by stream303 on 2009-01-06
> **scottmorabito said:**
> [COLOR="Red"]
Hi there, thanks to anyone who can point me in the right direction.

Getting close.  The horizontal and vertical frequencies you are using are specific to the G3 iMac and not your G4.

I'm assuming that you are using a PowerMac G4, which needs an external monitor.  If that is the case, you'll need to know that monitor's own specific vertical and horizontal frequencies, and also the native resolution (if lcd).

Or are you using a G4 powerbook?  Those two are about the only models I know of that are G4/400's.

Maybe take a look here to help find exactly what you have:

[http://www.everymac.com/](http://www.everymac.com/)

That will help out a lot too, but we've got to find out just what you are running for a monitor.

---

