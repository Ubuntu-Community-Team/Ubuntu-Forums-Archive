---
title: "Kubuntu - Max Resolution stuck on 800x600"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by moallen on 2007-07-20
Hello all,

These forums are fantastic and have already got me out of jail a few times.  I'll cross my fingers and hope I am as lucky this time.

I have been trying to follow instructions on these forums to increase my screen resolution.  I am using an ati technologies inc 3d rage IIc AGP video card with a Dell D1028LR screen.

So far I have tried 

sudo dpkg-reconfigure xserver-xorg - and made sure the higher resolutions are selected.

Also editing xorg.cong using sudo nano /etc/X11/xorg.conf

I have a driver called ati and the mode elements all show the higher resolutions as well.

However, even after a reboot, I go back to System Settings, Monitor and Display and I still see the max 800x600.

I have tried something called envy, but it seemd not to make any difference.

Any advice would be greatly appreciated.

Thanks

Mo

---

### Post by dougfractal on 2007-07-20
You need to set the HorizSync and VertRefresh in your xorg.conf for you moniter.

visit [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

see: How to edit or add HorizSync and VertRefresh lines

---

### Post by Mornedhel on 2007-07-20
God, we so need a GUI for xorg.conf .

---

### Post by Raineer on 2007-07-20
> **Mornedhel said:**
> God, we so need a GUI for xorg.conf .

True, but...most of the time if you're editing xorg you can't get to a gui :)

---

### Post by moallen on 2007-07-20
Thanks dougfractal,

Your suggestion has resulted in some progress, but I am still not quite there.  I have put in the settings for my screen as below

           HorizSync     31.0 - 70.0
           VertRefresh   50.0 - 120.0

After this, I do indeed get a choice of the higher resolutions.   I select a higher resolution and after a reboot, the part of the screen that is used is smaller and the resolution is now restricted to a max size of 832 x  624.

I have rechecked the spec on my monitor and found someone who specifies a HorizSynch of 30 to 69.  I tried this as well, but it made no difference.

Thanks again for your help

Mo

---

### Post by dougfractal on 2007-07-20
what resolution did you get from the live CD.

you could cp the live CD xorg.conf to your installed one.


from [http://forum.ubuntu.ru/index.php?topic=4572.msg35067](http://forum.ubuntu.ru/index.php?topic=4572.msg35067)
```
Section "Monitor"
   Identifier   "DELL D1028LR"
   HorizSync    30.0 - 69.0
   VertRefresh  48.0 - 120.0
   Option       "DPMS"
EndSection
```

---

### Post by moallen on 2007-07-20
Before I started mucking around, I copied the xorg.conf file so I can reliable get back to where I started.  I have then tried to edit it a few times, but every time, I get back to the strange 832 x 624 resolution.

I'm still stuck as to how to get the resolution up higher though.

Thanks again for your help so far

---

### Post by dougfractal on 2007-07-20
gedit /var/log/Xorg.0.log
then find "Validated modes" to get a list of device and moniter compatible modes. 

cat /etc/X11/xorg.conf and I'll have a look.
so did you ever have 1024x768? And you want 1280x1024?

---

### Post by moallen on 2007-07-20
Hi Doug,

At one point it looked as if I could get 1028 x 768.  I selected it, and a reboot was prompted which I did only to get the maximum of 832 x 624 when it came back up.

The contents of Xorg.0.log is copied below (split over two postings).  I'm not sure if it is relevant, but there was also a file called Xorg.1.log and Xorg.9.log.


Thanks again for your perserverance with this


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux apropos 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 20 18:05:14 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "DELL D1028LR" (0)
(**) |   |-->Monitor "DELL D1028LR"
(**) |   |-->Device "ATI Technologies Inc 3D Rage IIC AGP"
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
(II) PCI: 00:00:0: chip 8086,7190 card 1028,008e rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1011,0024 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0d:0: chip 9005,0010 card 9005,a180 rev 00 class 01,00,00 hdr 00
(II) PCI: 00:0e:0: chip 8086,1229 card 8086,100c rev 08 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 1102,0002 card 1102,8040 rev 05 class 04,01,00 hdr 80
(II) PCI: 00:11:1: chip 1102,7002 card 1102,0020 rev 05 class 09,80,00 hdr 80
(II) PCI: 01:00:0: chip 1002,4757 card 1028,008e rev 7a class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 1244,0a00 card 1244,0a00 rev 02 class 02,80,00 hdr 00
(II) PCI: 02:0b:0: chip 9005,001f card 9005,000f rev 01 class 01,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0088 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfb000000 - 0xfdffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xfaffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc 3D Rage IIC AGP rev 122, Mem @ 0xfc000000/24, 0xfbfff000/12, I/O @ 0xec00/8
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf3ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[1] -1	0	0xf9fffc00 - 0xf9fffc1f (0x20) MX[B]
	[2] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
	[3] -1	0	0xfe100000 - 0xfe100fff (0x1000) MX[B]
	[4] -1	0	0xfe101000 - 0xfe101fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000dce0 - 0x0000dcff (0x20) IX[B]
	[9] -1	0	0x0000cc78 - 0x0000cc7f (0x8) IX[B]
	[10] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[11] -1	0	0x0000cc80 - 0x0000ccbf (0x40) IX[B]
	[12] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[1] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[1] -1	0	0xf9fffc00 - 0xf9fffc1f (0x20) MX[B]
	[2] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
	[3] -1	0	0xfe100000 - 0xfe100fff (0x1000) MX[B]
	[4] -1	0	0xfe101000 - 0xfe101fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000dce0 - 0x0000dcff (0x20) IX[B]
	[9] -1	0	0x0000cc78 - 0x0000cc7f (0x8) IX[B]
	[10] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[11] -1	0	0x0000cc80 - 0x0000ccbf (0x40) IX[B]
	[12] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[1] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
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
	[4] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[5] -1	0	0xf9fffc00 - 0xf9fffc1f (0x20) MX[B]
	[6] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
	[7] -1	0	0xfe100000 - 0xfe100fff (0x1000) MX[B]
	[8] -1	0	0xfe101000 - 0xfe101fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dce0 - 0x0000dcff (0x20) IX[B]
	[15] -1	0	0x0000cc78 - 0x0000cc7f (0x8) IX[B]
	[16] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[17] -1	0	0x0000cc80 - 0x0000ccbf (0x40) IX[B]
	[18] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "glx"
	ABI class: X.Org Video Driver, version 1.1

---

### Post by moallen on 2007-07-20
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
(II) v4l driver for Video4Linux
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
(II) ATI:  Candidate "Device" section "ATI Technologies Inc 3D Rage IIC AGP".
(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 detected.
(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 assigned to active "Device" section "ATI Technologies Inc 3D Rage IIC AGP".
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[5] -1	0	0xf9fffc00 - 0xf9fffc1f (0x20) MX[B]
	[6] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
	[7] -1	0	0xfe100000 - 0xfe100fff (0x1000) MX[B]
	[8] -1	0	0xfe101000 - 0xfe101fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dce0 - 0x0000dcff (0x20) IX[B]
	[15] -1	0	0x0000cc78 - 0x0000cc7f (0x8) IX[B]
	[16] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[17] -1	0	0x0000cc80 - 0x0000ccbf (0x40) IX[B]
	[18] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
(II) Loading sub module "atimisc"
(II) LoadModule: "atimisc"
(II) Loading /usr/lib/xorg/modules/drivers//atimisc_drv.so
(II) Module atimisc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[5] -1	0	0xf9fffc00 - 0xf9fffc1f (0x20) MX[B]
	[6] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
	[7] -1	0	0xfe100000 - 0xfe100fff (0x1000) MX[B]
	[8] -1	0	0xfe101000 - 0xfe101fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dce0 - 0x0000dcff (0x20) IX[B]
	[18] -1	0	0x0000cc78 - 0x0000cc7f (0x8) IX[B]
	[19] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[20] -1	0	0x0000cc80 - 0x0000ccbf (0x40) IX[B]
	[21] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(==) ATI(0): Chipset:  "ati".
(**) ATI(0): Depth 24, (--) framebuffer bpp 32
(==) ATI(0): Using XAA acceleration architecture
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
(II) ATI(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) ATI(0): VESA BIOS detected
(II) ATI(0): VESA VBE Version 2.0
(II) ATI(0): VESA VBE Total Mem: 2048 kB
(II) ATI(0): VESA VBE OEM: ATI MACH64
(II) ATI(0): VESA VBE OEM Software Rev: 1.0
(II) ATI(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) ATI(0): VESA VBE OEM Product: MACH64GT
(II) ATI(0): VESA VBE OEM Product Rev: 01.00
(II) ATI(0): VESA VBE DDC supported
(II) ATI(0): VESA VBE DDC Level 2
(II) ATI(0): VESA VBE DDC transfer in appr. 2 sec.
(II) ATI(0): VESA VBE DDC read successfully
(II) ATI(0): Manufacturer: DEL  Model: 730b  Serial#: 827021124
(II) ATI(0): Year: 1998  Week: 8
(II) ATI(0): EDID Version: 1.1
(II) ATI(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) ATI(0): Sync:  Separate
(II) ATI(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) ATI(0): Gamma: 2.50
(II) ATI(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) ATI(0): redX: 0.620 redY: 0.345   greenX: 0.290 greenY: 0.610
(II) ATI(0): blueX: 0.155 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) ATI(0): Supported VESA Video Modes:
(II) ATI(0): 720x400@70Hz
(II) ATI(0): 640x480@60Hz
(II) ATI(0): 640x480@75Hz
(II) ATI(0): 800x600@60Hz
(II) ATI(0): 800x600@75Hz
(II) ATI(0): 1024x768@60Hz
(II) ATI(0): 1024x768@75Hz
(II) ATI(0): Manufacturer's mask: 0
(II) ATI(0): Supported Future Video Modes:
(II) ATI(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) ATI(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) ATI(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) ATI(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) ATI(0): Supported additional Video Mode:
(II) ATI(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) ATI(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) ATI(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) ATI(0): Serial No: 85270Z1KWD28
(II) ATI(0): Monitor name: DELL D1028LR
(II) ATI(0): Ranges: V min: 48  V max: 120 Hz, H min: 30  H max: 69 kHz,
(II) ATI(0): EDID (in hex):
(II) ATI(0): 	00ffffffffffff0010ac0b7344574b31
(II) ATI(0): 	08080101081e1796e8d5f29e584a9c27
(II) ATI(0): 	10484fa54a0061594559818031590101
(II) ATI(0): 	010101010101100bd0b4205e6310126c
(II) ATI(0): 	6208fab80000001a000000ff00383532
(II) ATI(0): 	37305a314b574432380a000000fc0044
(II) ATI(0): 	454c4c2044313032384c520a000000fd
(II) ATI(0): 	0030781e45ff000a20202020202000aa
(II) ATI(0): Using EDID range info for horizontal sync
(II) ATI(0): Using EDID range info for vertical refresh
(II) ATI(0): Printing DDC gathered Modelines:
(II) ATI(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) ATI(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) ATI(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) ATI(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) ATI(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) ATI(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) ATI(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) ATI(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) ATI(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) ATI(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) ATI(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) ATI(0): Modeline "720x350"   28.32  720 738 846 900  350 388 390 449 -hsync +vsync
(II) ATI(0): BIOS Data:  BIOSSize=0x8000, ROMTable=0x00E0.
(II) ATI(0): BIOS Data:  ClockTable=0x0758, FrequencyTable=0x0732.
(II) ATI(0): BIOS Data:  LCDTable=0x0000, LCDPanelInfo=0x0000.
(II) ATI(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x012A.
(II) ATI(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) ATI(0): ATI 3D Rage IIc graphics controller detected.
(--) ATI(0): Chip type 4757 "GW", version 2, foundry UMC, class 0, revision 0x01.
(--) ATI(0): AGP bus interface detected;  block I/O base is 0xEC00.
(--) ATI(0): ATI Mach64 adapter detected.
(!!) ATI(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) ATI(0): Internal RAMDAC (subtype 1) detected.
(==) ATI(0): RGB weight 888
(==) ATI(0): Default visual is TrueColor
(**) ATI(0): Using gamma correction (1.0, 1.0, 1.0)
(II) ATI(0): Using Mach64 accelerator CRTC.
(II) ATI(0): Storing hardware cursor image at 0xFC1FFC00.
(II) ATI(0): Using 8 MB linear aperture at 0xFC000000.
(!!) ATI(0): Virtual resolutions will be limited to 2047 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) ATI(0): Using Block 0 MMIO aperture at 0xFBFFF400.
(II) ATI(0): Using Block 1 MMIO aperture at 0xFBFFF000.
(==) ATI(0): Write-combining range (0xfc000000,0x200000)
(II) ATI(0): MMIO write caching enabled.
(--) ATI(0): 2048 kB of SGRAM (1:1) detected (using 2047 kB).
(WW) ATI(0): Cannot shadow an accelerated frame buffer.
(II) ATI(0): Engine XCLK 83.138 MHz;  Refresh rate code 6.
(--) ATI(0): Internal programmable clock generator detected.
(--) ATI(0): Reference clock 157.5/11 (14.318) MHz.
(II) ATI(0): DELL D1028LR: Using hsync range of 30.00-69.00 kHz
(II) ATI(0): DELL D1028LR: Using vrefresh range of 48.00-120.00 Hz
(II) ATI(0): Maximum clock: 166.00 MHz
(II) ATI(0): Not using mode "1024x768@85" (insufficient memory for mode)
(II) ATI(0): Not using mode "1024x768@75" (insufficient memory for mode)
(II) ATI(0): Not using mode "1024x768@70" (insufficient memory for mode)
(II) ATI(0): Not using mode "1024x768@60" (insufficient memory for mode)
(II) ATI(0): Not using mode "1024x768@43" (insufficient memory for mode)
(II) ATI(0): Not using mode "1152x864@75" (insufficient memory for mode)
(II) ATI(0): Not using mode "1280x960@60" (insufficient memory for mode)
(II) ATI(0): Not using mode "1280x1024@60" (insufficient memory for mode)
(II) ATI(0): Not using mode "1400x1050@60" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x480" (hsync out of range)
(II) ATI(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x512" (hsync out of range)
(II) ATI(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x512" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1280x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1280x800" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1152x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) ATI(0): Not using default mode "576x432" (hsync out of range)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "700x525" (hsync out of range)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "700x525" (hsync out of range)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "700x525" (hsync out of range)
(II) ATI(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (insufficient memory for mode)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) ATI(0): Not using driver mode "1280x1024" (insufficient memory for mode)
(II) ATI(0): Not using mode "1152x864@75" (no mode of this name)
(II) ATI(0): Not using mode "1280x960@60" (no mode of this name)
(II) ATI(0): Not using mode "1024x768@43" (no mode of this name)
(II) ATI(0): Not using mode "1280x1024@60" (no mode of this name)
(II) ATI(0): Not using mode "1024x768@60" (no mode of this name)
(II) ATI(0): Not using mode "1400x1050@60" (no mode of this name)
(II) ATI(0): Not using mode "1024x768@70" (no mode of this name)
(II) ATI(0): Not using mode "1024x768@75" (no mode of this name)
(II) ATI(0): Not using mode "1024x768@85" (no mode of this name)
(II) ATI(0): Not using default mode "840x525" (width too large for virtual size)
(--) ATI(0): Virtual size is 832x624 (pitch 832)
(**) ATI(0): *Mode "832x624@75": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) ATI(0): Modeline "832x624@75"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) ATI(0): *Mode "800x600@60": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) ATI(0): Modeline "800x600@60"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) ATI(0): *Mode "800x600@85": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) ATI(0): Modeline "800x600@85"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) ATI(0): *Mode "800x600@75": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) ATI(0): Modeline "800x600@75"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) ATI(0): *Mode "800x600@72": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) ATI(0): Modeline "800x600@72"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) ATI(0): *Mode "800x600@56": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) ATI(0): Modeline "800x600@56"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) ATI(0): *Mode "640x480@85": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) ATI(0): Modeline "640x480@85"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) ATI(0): *Mode "640x480@75": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) ATI(0): Modeline "640x480@75"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) ATI(0): *Mode "640x480@72": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) ATI(0): Modeline "640x480@72"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) ATI(0): *Mode "640x480@60": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) ATI(0): Modeline "640x480@60"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) ATI(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) ATI(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) ATI(0):  Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) ATI(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(**) ATI(0):  Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) ATI(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) ATI(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) ATI(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) ATI(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) ATI(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) ATI(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) ATI(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) ATI(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) ATI(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) ATI(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) ATI(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) ATI(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) ATI(0):  Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(II) ATI(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(**) ATI(0):  Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) ATI(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) ATI(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) ATI(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) ATI(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) ATI(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) ATI(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) ATI(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) ATI(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) ATI(0):  Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) ATI(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(**) ATI(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) ATI(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) ATI(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) ATI(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) ATI(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) ATI(0):  Driver mode "720x350": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) ATI(0): Modeline "720x350"   28.32  720 738 846 900  350 388 390 449 -hsync +vsync
(**) ATI(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) ATI(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) ATI(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) ATI(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) ATI(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) ATI(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) ATI(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) ATI(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) ATI(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) ATI(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) ATI(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) ATI(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) ATI(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) ATI(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) ATI(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) ATI(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) ATI(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) ATI(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) ATI(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) ATI(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) ATI(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) ATI(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) ATI(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) ATI(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) ATI(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) ATI(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) ATI(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) ATI(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) ATI(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync

---

### Post by moallen on 2007-07-20
(**) ATI(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) ATI(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(**) ATI(0): Display dimensions: (300, 230) mm
(**) ATI(0): DPI set to (70, 68)
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
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) ATI(0): I2C bus "Mach64" initialized.
(--) ATI(0): ImpacTV chip ID 0x8A detected.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfbfff000 - 0xfbffffff (0x1000) MS[B]
	[1] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[7] -1	0	0xf9fffc00 - 0xf9fffc1f (0x20) MX[B]
	[8] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
	[9] -1	0	0xfe100000 - 0xfe100fff (0x1000) MX[B]
	[10] -1	0	0xfe101000 - 0xfe101fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x0000ec00 - 0x0000ecff (0x100) IS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dce0 - 0x0000dcff (0x20) IX[B]
	[21] -1	0	0x0000cc78 - 0x0000cc7f (0x8) IX[B]
	[22] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[23] -1	0	0x0000cc80 - 0x0000ccbf (0x40) IX[B]
	[24] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) ATI(0): Write-combining range (0xfc000000,0x200000)
(WW) ATI(0): Direct rendering is not supported for ATI chips earlier than the ATI 3D Rage Pro.
(II) ATI(0): Largest offscreen areas (with overlaps):
(II) ATI(0): 	832 x 5 rectangle at 0,624
(II) ATI(0): 	704 x 6 rectangle at 0,624
(II) ATI(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		Not enough video memory for pixmap cache
(==) ATI(0): Backing store disabled
(==) ATI(0): Silken mouse enabled
(WW) ATI(0): Option "MergedFB" is not used
(II) ATI(0): Direct rendering disabled
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
(EE) AIGLX: DRI module not loaded
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
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
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
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetClientVersion: 0 9
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetGrabKeysState - disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by dougfractal on 2007-07-20
Wow! thats quite a list. (using quote will put it all in a box)

Ok It looks like you are out of memory try "DefaultDepth    16"

here a /etc/X11/xorg.conf that could work, it may not all there as I ripped and modded from 
[http://forums.scotsnewsletter.com/index.php?showtopic=17698](http://forums.scotsnewsletter.com/index.php?showtopic=17698)

```

Section "Device"
    Identifier    "ATI Technologies, Inc. 3D Rage IIC AGP"
    Driver        "ati"
    BusID        "PCI:1:0:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
   Identifier   "DELL D1028LR"
   HorizSync    30.0 - 69.0
   VertRefresh  48.0 - 120.0
   Option       "DPMS"
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. 3D Rage IIC AGP"
    Monitor        "DELL D1028LR"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

```


There are a few drivers you can try on an ATI card:

driver "ati" ( xorg driver)

driver "radeon" ( xorg driver )

driver "vesa" ( xorg generic video card driver )

Or install the propriety drivers ( [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) ) and set the driver to:

driver "fglrx"

NOTES: The propriety drivers are for cards > Radeon 8500 . . . and do most of the time NOT support the very latest kernel !!


Hope this works for you 
Doug

---

### Post by moallen on 2007-07-22
Thats brilliant.  It worked - Thank you so much.  I am amazed at how you guys provide so much help and am so impressed bu Ubuntu.

Thanks

again

Mo

---

