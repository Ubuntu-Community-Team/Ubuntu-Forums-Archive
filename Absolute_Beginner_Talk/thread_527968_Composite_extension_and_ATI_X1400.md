---
title: "Composite extension and ATI X1400"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Drew88 on 2007-08-17
Hi all.  I'm new to Ubuntu and Linux (2 days) and have gotten most things up and running as I want.  However, I cannot for the life of me get the Desktop Effects to work.  All I get is an error "the Composite extension is not available".  My graphics card is an ATI Radeon Mobility X1400.  I have the proprietary drivers installed, and when I run the glxinfo | grep direct  command I get yes to rendering.  Is there anyway to get this to work or am I just going to have to give up on effects and wait for new drivers? 

thanks. 
drew

---

### Post by Hobo Joe on 2007-08-17
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Paste that to the end of your xorg.conf flie.

```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by Drew88 on 2007-08-17
Thanks for the reply hobo, but I tried that already.  When I then try to activate the extensions I get a bit further, to the prompt asking me if I want to launch the effects, bu then I get a shiny new error message:  "Desktop Effects could not be be enabled" if I try to enable them.  The second be is not a typo, it's what is in the message.  
Any other ideas?  
drew

---

### Post by Hobo Joe on 2007-08-17
Are you just using the defualt desktop effects?

I'd recommend Compiz Fusion or Beryl.

---

### Post by Drew88 on 2007-08-17
I was just trying to use teh default desktop effects, though I've got Beryl installed as well.  Problem is I don't really know how to make it work.  I change the settings and play with it but nothing really seems to happen.  When I go into the manager and activate it, the screen flickers and changes but there doesn't appear to be any difference in terms of what the desktop or windows do.

---

### Post by kellemes on 2007-08-17
Two things should be in your xorg.conf for sure!

```

Section "Extensions"
  Option "Composite" "Disable"
EndSection

Section "ServerFlags"
  Option "AIGLX" "off"
EndSection

```


Disable composite.. And disable the use of AIGLX, instead you need to configure XGL.

Try here: [http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385")

---

### Post by Hobo Joe on 2007-08-17
Ok, as far as Beryl goes, here's a good way to get it installed properly. First, uninstall and remove any settings you have by running this:
```

sudo aptitude purge beryl

```
Then follow the guide here:
[https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

---

### Post by Drew88 on 2007-08-17
Tried this as well, and when I login to the gnome with XGL session, I get into the session but all the images on the desktop are distorted beyond recognition.  Basically, it looks like one big fuzzy brown blur.  
Any ideas why this might be?

---

### Post by kellemes on 2007-08-17
Please post (and look at) /var/log/Xorg.0.log

---

### Post by Drew88 on 2007-08-17
Here is the first part of the Xlog.0.log file:


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux andrew-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 17 15:09:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
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
(++) using VT number 9

(

---

### Post by Drew88 on 2007-08-17
and the second part:

II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1179,ff10 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1179,ff10 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1179,ff10 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1179,ff10 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1179,ff10 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1179,ff10 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1179,ff10 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1179,ff10 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1179,ff10 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1179,ff10 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7145 card 1179,ff10 rev 00 class 03,00,00 hdr 00
(II) PCI: 05:00:0: chip 8086,4222 card 8086,1041 rev 02 class 02,80,00 hdr 00
(II) PCI: 07:06:0: chip 104c,8039 card 5400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 07:06:1: chip 104c,803a card 1179,ff10 rev 00 class 0c,00,10 hdr 80
(II) PCI: 07:06:2: chip 104c,803b card 1179,ff10 rev 00 class 01,80,00 hdr 80
(II) PCI: 07:06:3: chip 104c,803c card 1179,ff10 rev 00 class 08,05,01 hdr 80
(II) PCI: 07:08:0: chip 8086,1092 card 1179,ff10 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,8), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdc0fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:30:0), (0,7,11), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[1] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[2] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[3] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xdc100000 - 0xdc1fffff (0x100000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x33ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 8: bridge is at (7:6:0), (7,8,11), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[1] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x33ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility X1400 rev 0, Mem @ 0xc8000000/27, 0xdc000000/16, I/O @ 0x2000/8
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
(II) Active PCI resource ranges:
	[0] -1	0	0xdc105000 - 0xdc105fff (0x1000) MX[B]
	[1] -1	0	0xdc106800 - 0xdc1068ff (0x100) MX[B]
	[2] -1	0	0xdc104000 - 0xdc104fff (0x1000) MX[B]
	[3] -1	0	0xdc100000 - 0xdc103fff (0x4000) MX[B]
	[4] -1	0	0xdc106000 - 0xdc1067ff (0x800) MX[B]
	[5] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[6] -1	0	0xdc404000 - 0xdc4043ff (0x400) MX[B]
	[7] -1	0	0xdc400000 - 0xdc403fff (0x4000) MX[B]
	[8] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[11] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdc105000 - 0xdc105fff (0x1000) MX[B]
	[1] -1	0	0xdc106800 - 0xdc1068ff (0x100) MX[B]
	[2] -1	0	0xdc104000 - 0xdc104fff (0x1000) MX[B]
	[3] -1	0	0xdc100000 - 0xdc103fff (0x4000) MX[B]
	[4] -1	0	0xdc106000 - 0xdc1067ff (0x800) MX[B]
	[5] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[6] -1	0	0xdc404000 - 0xdc4043ff (0x400) MX[B]
	[7] -1	0	0xdc400000 - 0xdc403fff (0x4000) MX[B]
	[8] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[11] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
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
	[4] -1	0	0xdc105000 - 0xdc105fff (0x1000) MX[B]
	[5] -1	0	0xdc106800 - 0xdc1068ff (0x100) MX[B]
	[6] -1	0	0xdc104000 - 0xdc104fff (0x1000) MX[B]
	[7] -1	0	0xdc100000 - 0xdc103fff (0x4000) MX[B]
	[8] -1	0	0xdc106000 - 0xdc1067ff (0x800) MX[B]
	[9] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[10] -1	0	0xdc404000 - 0xdc4043ff (0x400) MX[B]
	[11] -1	0	0xdc400000 - 0xdc403fff (0x4000) MX[B]
	[12] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[17] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[18] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[27] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)

---

### Post by Drew88 on 2007-08-17
and the final part:

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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.40.4
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.40.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.402                    
(II) ATI Proprietary Linux Driver Build Date: Jul 31 2007 22:20:14
(--) Chipset Supported AMD Graphics Processor (0x7145) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc105000 - 0xdc105fff (0x1000) MX[B]
	[5] -1	0	0xdc106800 - 0xdc1068ff (0x100) MX[B]
	[6] -1	0	0xdc104000 - 0xdc104fff (0x1000) MX[B]
	[7] -1	0	0xdc100000 - 0xdc103fff (0x4000) MX[B]
	[8] -1	0	0xdc106000 - 0xdc1067ff (0x800) MX[B]
	[9] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[10] -1	0	0xdc404000 - 0xdc4043ff (0x400) MX[B]
	[11] -1	0	0xdc400000 - 0xdc403fff (0x4000) MX[B]
	[12] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[17] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[18] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[27] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e4648
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc105000 - 0xdc105fff (0x1000) MX[B]
	[5] -1	0	0xdc106800 - 0xdc1068ff (0x100) MX[B]
	[6] -1	0	0xdc104000 - 0xdc104fff (0x1000) MX[B]
	[7] -1	0	0xdc100000 - 0xdc103fff (0x4000) MX[B]
	[8] -1	0	0xdc106000 - 0xdc1067ff (0x800) MX[B]
	[9] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[10] -1	0	0xdc404000 - 0xdc4043ff (0x400) MX[B]
	[11] -1	0	0xdc400000 - 0xdc403fff (0x4000) MX[B]
	[12] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[20] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
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
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1400" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x1179, PciSubDevice = 0xff10)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xdc000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.40.4
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) fglrx(0):  SAMSUNG
(II) fglrx(0):  LTN154X3-L06
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004ca3333600000000
(II) fglrx(0): 	000f0103802115780a87f594574f8c27
(II) fglrx(0): 	27505400000001010101010101010101
(II) fglrx(0): 	010101010101ee1a0080502010301030
(II) fglrx(0): 	13004bcf100000190000000f00000000
(II) fglrx(0): 	00000000002387026402000000fe0053
(II) fglrx(0): 	414d53554e470a2020202020000000fe
(II) fglrx(0): 	004c544e31353458332d4c30360a0070
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 439/342MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 128/153MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/153MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/153MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 9 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync

---

### Post by kellemes on 2007-08-17
Tip of the day: For long posts like this you can use the CODE-tags, look in the toolbar of the editor.
It saves a lot of paging ;)

I don't see anything wrong with the log, looks fine.
Can you please post your xorg.conf (don't forget the CODE-tags)

---

### Post by Drew88 on 2007-08-17
Thanks for the tip! here is my xorg.conf file:

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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```

---

### Post by Drew88 on 2007-08-17
any ideas?

thanks. 
drew

---

