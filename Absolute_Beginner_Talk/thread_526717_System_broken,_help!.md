---
title: "System broken, help!"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by MicroChris on 2007-08-15
Hello all,

I restarted my KDE (Kubuntu) box, and it'll get to the part where the logo shows and the status bar goes across, then itll blink out, show ANOTHER Kubuntu logo then go directly to a black screen with a blinking _. Commands won't work or anything

I'm trying to figure out what's wrong with it, are there any logs I can pull up so someone can help me?

Please help! I didn't install anything funky or mess with anything for the system to break like this..

HELP!

Thanks,
Chris

---

### Post by p_quarles on 2007-08-15
You could try taking a look at this:
```
cat /var/log/Xorg.0.log | less
```
Look for any patterns that might indicate a problem with starting up.

---

### Post by MicroChris on 2007-08-15
> **p_quarles said:**
> You could try taking a look at this:
```
cat /var/log/Xorg.0.log | less
```
Look for any patterns that might indicate a problem with starting up.

I'd have to someone mount my harddrive on the LiveCD right? I guess that's another project :(

---

### Post by p_quarles on 2007-08-15
Possibly. If you can start in recovery mode (the second Grub option), you should be able to get a command line interface running. If not, then, yeah, live CD it is.

---

### Post by MicroChris on 2007-08-15
> **p_quarles said:**
> Possibly. If you can start in recovery mode (the second Grub option), you should be able to get a command line interface running. If not, then, yeah, live CD it is.

Well, I'm on the LiveCD right now. How would I mount my existing filesystem?

Thanks again.

---

### Post by MicroChris on 2007-08-15
Okay mounted the drive, here's the log:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux linux 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 15 20:49:07 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
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
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
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
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 02:00:0: chip 1002,4152 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,4172 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xe7ffffff (0x10000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc RV350 AR [Radeon 9600] rev 0, Mem @ 0xd8000000/27, 0xe9000000/16, I/O @ 0xc000/8
(--) PCI: (2:0:1) ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xe9010000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[1] -1	0	0xea001000 - 0xea001fff (0x1000) MX[B]
	[2] -1	0	0xea000000 - 0xea0000ff (0x100) MX[B]
	[3] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[4] -1	0	0xea004000 - 0xea004fff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[1] -1	0	0xea001000 - 0xea001fff (0x1000) MX[B]
	[2] -1	0	0xea000000 - 0xea0000ff (0x100) MX[B]
	[3] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[4] -1	0	0xea004000 - 0xea004fff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[5] -1	0	0xea001000 - 0xea001fff (0x1000) MX[B]
	[6] -1	0	0xea000000 - 0xea0000ff (0x100) MX[B]
	[7] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[8] -1	0	0xea004000 - 0xea004fff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4152) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[5] -1	0	0xea001000 - 0xea001fff (0x1000) MX[B]
	[6] -1	0	0xea000000 - 0xea0000ff (0x100) MX[B]
	[7] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[8] -1	0	0xea004000 - 0xea004fff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6ba8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[5] -1	0	0xea001000 - 0xea001fff (0x1000) MX[B]
	[6] -1	0	0xea000000 - 0xea0000ff (0x100) MX[B]
	[7] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[8] -1	0	0xea004000 - 0xea004fff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI RADEON 9600 Series" (Chipset = 0x4152)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd8000000
(--) fglrx(0): MMIO registers at 0xe9000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 215  Serial#: 1296380215
(II) fglrx(0): Year: 2006  Week: 13
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
(II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HVEL308070
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2d15023731454d
(II) fglrx(0): 	0d1001030e221b782a3d85a6564a9a24
(II) fglrx(0): 	125054bfef80818f714f814001010101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300520e1100001e000000fd00384b1e
(II) fglrx(0): 	510e000a202020202020000000fc0053
(II) fglrx(0): 	796e634d61737465720a2020000000ff
(II) fglrx(0): 	004856454c3330383037300a2020007a
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  4 power states available:
(II) fglrx(0):   1. 500/297MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   2. 398/297MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   3. 513/297MHz @ 50Hz [overclocked, enable load balancing, overdrive]
(II) fglrx(0):   4. 527/297MHz @ 50Hz [overclocked, enable load balancing, overdrive]

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb755ce5f]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(DALCWDDE+0x1a2) [0xb755b4a2]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlDalHelperAddCustomizeMode+0x1a4) [0xb74f1d54]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0xb7b) [0xb74cb75b]
6: /usr/bin/X(InitOutput+0x9aa) [0x80a5b9a]
7: /usr/bin/X(main+0x27b) [0x807456b]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d83ebc]
9: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting


```

Quite extensive, sorry.

Thanks for the help.

-Chris

---

### Post by p_quarles on 2007-08-15
Caveat: I've never done this, so you might want to search for a more comprehensive tutorial, or wait for better advice before doing this.

When you boot from the live CD, there's an option "Recover a broken system." EDIT: It doesn't do anything automatically, though. That's why I suggest you look up a tutorial first.

Based on the last few lines of the log you posted, this definitely looks like an X server problem. It could be as simple as resetting the configuration file, or it could be your video card.

EDIT: Wish I could offer more help, but, like I said, I haven't been through this yet.

---

### Post by MicroChris on 2007-08-15
> **p_quarles said:**
> Caveat: I've never done this, so you might want to search for a more comprehensive tutorial, or wait for better advice before doing this.

When you boot from the live CD, there's an option "Recover a broken system." EDIT: It doesn't do anything automatically, though. That's why I suggest you look up a tutorial first.

Based on the last few lines of the log you posted, this definitely looks like an X server problem. It could be as simple as resetting the configuration file, or it could be your video card.

EDIT: Wish I could offer more help, but, like I said, I haven't been through this yet.

Not a problem man, you pointed me in the right direction :)

I did a dpkg-reconfigure xserver-xorg, and everything seemed to work after that.

I'm just trying to figure out what it was that caused the error. I've been booting and rebooting all day and haven't messed with my drivers or anything at all.

Ahh well.

---

### Post by MicroChris on 2007-08-15
Now I'm getting this error in a terminal:

```
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5483' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

```

What's up with that?

---

### Post by p_quarles on 2007-08-15
Awesome. I had a feeling that would fix it, but didn't want to be too confident. :)

I don't know what did it either, but it looks like you have an ATI video adapater, and those do cause a lot of problems for Linux.

---

### Post by p_quarles on 2007-08-15
I spoke too soon, I see. 

It looks like you have an ATI card, and are using the VESA driver. Again, this is not something I've ever dealt with, but you might want to try installing the ATI drivers:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

