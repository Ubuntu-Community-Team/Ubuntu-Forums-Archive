---
title: "Can't get widescreen resolution"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Big Ben on 2007-08-17
I've now spent hours searching the forums and modifying xorg and such, and nothing works.

I just bought a new 19" widescreen monitor with 1440x900 native resolution, and no amount of tweaking will get that to appear as an option in System>Preferences>Screen resolution.

 I upgraded to the new intel driver (I have an Intel82915G/GV/910GL chipset), and I added a new modeline to xorg.conf, it still won't show up.

Here's the relevant section of xorg.conf:
```
Section "Monitor"
	Identifier	"GH-AWG193SD"
     HorizSync          30-83
     VertRefresh        55-75
# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
# 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900_60.00" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900_60.00" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900_60.00" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900_60.00" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_60.00" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00" "1280x800_60.00" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

```

What am I doing wrong?

---

### Post by jjbean on 2007-08-17
I had that problem. [This]("http://ubuntuforums.org/showthread.php?t=523108") is my thread, and how I got it fixed. In a nutshell I had to drop the -HSync +Vsync from the modeline.

A word of caution. Make sure your modeline has the correct info.

Sorry I forgot this. The repos have a package called 915resolution for some Intel chipsets that helps with widescreen resolution

---

### Post by Big Ben on 2007-08-17
Thanks, jjbean, but it didn't work.

I tried copying your modeline from the other thread without the "-hsync +vsync" part, but 1440x900 still doesn't show up in the available resolutions.

xog.conf now reads:
```

Section "Monitor"
	Identifier	"GH-AWG193SD"
     HorizSync          30-83
     VertRefresh        55-75
# 1440x900@60 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900@60" 106.50 1440 1520 1672 1904 900 903 909 934
# 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900@60" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900@60" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900@60" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900@60" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900@60" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900@60" "1280x800_60.00" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection
```

But the only resolutions that show up in System>Preferenced>Screen Resolution are 1280x768, 1024x768, 800x600, 640 x480, 1280x800, and 1280x1280.

What is going on? Why am I even seeing 1280x1280 when it's not in xorg.conf?

---

### Post by alienexplorers on 2007-08-17
Did you add the 915resolution from the repo's

---

### Post by jjbean on 2007-08-17
You can look in your Xorg log to see what is available for your monitor. It is in System>Admin>System Log. Just look for the one starting with Xorg. My other thread shows what the part of the log you are looking for looks like. It should give you the proper info for making a modeline. It may our may not match mine. Also did you try the package 915resolution? It is for Intel chipsets. I edited that into my last post, just in case you missed it.  Hope this helps.

---

### Post by Big Ben on 2007-08-17
alienexplorers, I tried 915resolution earlier with no success, but I was led to believe that 915 resolution was a workaround for the old driver and not necessary with the newer intel driver, so I removed it. Is this wrong?

I guess I'll try it one more time.

---

### Post by w4ett on 2007-08-17
here is the 915 resolution startup script:

[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

---

### Post by Big Ben on 2007-08-17
915resolution doesn't seem to do anything. The options in the screen resolution GUI are unchanged.

w4ett, I appreciate the tip. I tried the startup script, and it doesn't help.
Do I need to revert to the i810 driver for this to work?

jjbean,  xorg.0.log is confusing me. I don't see any section that resembles th one in your post. I can't find anything about sync rates or resolutions in it at all. Here's the whole file if that helps.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ben-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 18 10:23:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "GH-AWG193SD"
(**) |   |-->Device "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
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
(II) PCI: 00:00:0: chip 8086,2580 card 107b,4037 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2581 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2582 card 107b,4037 rev 04 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,2668 card 107b,4037 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2666 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 107b,4037 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 107b,4037 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 107b,4037 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 107b,4037 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 107b,4037 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 107b,4037 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 107b,4037 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 107b,4037 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 107b,4037 rev 03 class 0c,05,00 hdr 00
(II) PCI: 06:00:0: chip 10ec,8139 card 6409,001c rev 10 class 02,00,00 hdr 00
(II) PCI: 06:01:0: chip 163c,3052 card 14fe,0005 rev 04 class 07,03,00 hdr 00
(II) PCI: 06:05:0: chip 11c1,5811 card 8086,4556 rev 61 class 0c,00,10 hdr 00
(II) PCI: 06:08:0: chip 8086,1064 card 107b,4037 rev 03 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff300000 - 0xff3fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbf900000 - 0xbf9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:0), (0,5,5), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xff700000 - 0xff7fffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xbfd00000 - 0xbfdfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xff600000 - 0xff6fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xbfc00000 - 0xbfcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xff500000 - 0xff5fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xbfb00000 - 0xbfbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:3), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xff400000 - 0xff4fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xbfa00000 - 0xbfafffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,6), BCTRL: 0x0206 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0xbfe00000 - 0xbfefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xffa80000/19, 0xd0000000/28, 0xffa40000/18, I/O @ 0xec00/3
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
	[0] -1	0	0xff8fc000 - 0xff8fcfff (0x1000) MX[B]
	[1] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[2] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[3] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[4] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[5] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[6] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[9] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[10] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[12] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff8fc000 - 0xff8fcfff (0x1000) MX[B]
	[1] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[2] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[3] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[4] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[5] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[6] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[9] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[10] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[12] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
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
	[4] -1	0	0xff8fc000 - 0xff8fcfff (0x1000) MX[B]
	[5] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[6] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[7] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[8] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[9] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[10] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[32] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
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
(==) AIGLX enabled
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 14.94.94
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8fc000 - 0xff8fcfff (0x1000) MX[B]
	[5] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[6] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[7] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[8] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[9] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[10] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[32] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8fc000 - 0xff8fcfff (0x1000) MX[B]
	[5] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[6] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[7] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[8] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[9] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[10] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[34] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[35] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFFA80000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(**) intel(0): Option "NoDDC"
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xffa40000 - 0xffa7ffff (0x40000) MS[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MS[B]
	[2] 0	0	0xffa80000 - 0xffafffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xff8fc000 - 0xff8fcfff (0x1000) MX[B]
	[8] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[9] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[10] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[11] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[12] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[13] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000ec00 - 0x0000ec07 (0x8) IS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[31] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[38] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[39] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 4860 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x00037fff: xaa scratch (64 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x343a8000 physical)
(II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x33c5c000 physical)
(II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x34b89000 physical)
(II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x33c60000 physical)
(II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x343bc000 physical)
(II) intel(0): 0x007d0000-0x037c7fff: front buffer (49120 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB)
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB)
(II) intel(0): 0x06000000-0x07ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x08000000-0x09ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf8db8000
(II) intel(0): [drm] mapped SAREA 0xf8db8000 to 0xb7ae2000
(II) intel(0): [drm] framebuffer handle = 0xd07d0000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0xffa80000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] init sarea width,height = 1280 x 1280 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x2a0fa000
(II) intel(0): [drm] Back Buffer = 0xd4000000
(II) intel(0): [drm] Depth Buffer = 0xd5000000
(II) intel(0): [drm] textures = 0xd8000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x007c0000 (pgoffset 1984)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007c4000 (pgoffset 1988)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x007c5000 (pgoffset 1989)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x007c9000 (pgoffset 1993)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x007d0000 (pgoffset 2000)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 8 at 0x08000000 (pgoffset 32768)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 203
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "jp106"
(**) Generic Keyboard: XkbModel: "jp106"
(**) Option "XkbLayout" "jp,jp"
(**) Generic Keyboard: XkbLayout: "jp,jp"
(**) Option "XkbVariant" "latin,"
(**) Generic Keyboard: XkbVariant: "latin,"
(**) Option "XkbOptions" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(**) Generic Keyboard: XkbOptions: "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
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
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetClientVersion: 0 9
(II) XAA: Evicting pixmaps
```

---

### Post by w4ett on 2007-08-17
From the terminal type:
```

xrandr
```

and post the output...this will show ALL the available resolutions.

---

### Post by Big Ben on 2007-08-17
xrandr gives me:
```
 SZ:    Pixels          Physical       Refresh
 0   1280 x 768    ( 433mm x 433mm )   60  
*1   1024 x 768    ( 433mm x 433mm )  *60  
 2    800 x 600    ( 433mm x 433mm )   60  
 3    640 x 480    ( 433mm x 433mm )   60  
 4   1280 x 800    ( 433mm x 433mm )   60  
 5   1280 x 1280   ( 433mm x 433mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none

```

---

### Post by jjbean on 2007-08-17
This might work. From the terminal.
 
```
 xvidtune -show
```

This should show you what your modeline should look like.

---

### Post by Big Ben on 2007-08-17
"xvidtune -show" gives me:
```
"1024x768"     65.00   1024 1048 1184 1344    768  771  777  806 -hsync -vsync
```
...which is what the monitor is currently using, but it's a 4:3 stretched onto the widescreen monitor, so it's ugly.

---

### Post by Big Ben on 2007-08-17
Does that give me any information on what my 1440x900 modeline should look like?

---

### Post by jjbean on 2007-08-17
It does show it as -hsync -vsync not +vsync. Honestly do not know if that matters.

Were did you get the modeline info you tried to use?

Also what type of monitor is it? Make and model?

---

### Post by jjbean on 2007-08-17
This might help you as well. 
[URL="http://ubuntuforums.org/showthread.php?t=351647&highlight=how+to+get+correct+modeline"]
 The PAINLESS way to set Screen Resolution for Intel Chipsets [/URL]

---

### Post by Big Ben on 2007-08-17
It's a cheap 19" widescreen from a company called [Greenhouse]("http://www.green-house.co.jp/products/lcd/awg193sd/awg193sd_spec.html"). 
I'm starting to think that I got what I paid for.

I used "gtf 1440 900 60" in the terminal to generate my modeline.

---

### Post by w4ett on 2007-08-17
BigBen..what are the results when you use the regular xorg-driver-intel????

---

### Post by Big Ben on 2007-08-17
> **w4ett said:**
> BigBen..what are the results when you use the regular xorg-driver-intel????
How do I do that?
apt says "xserver-xorg-video-intel is already the newest version." Do I need to do anything else to select it?

---

### Post by w4ett on 2007-08-17
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select intel, not the i810 driver, the select desired resolutions, save, close the app, and restart x

---

### Post by Big Ben on 2007-08-17
jjbean,
I tried everything on the "painless way" link again, and nothing changes. 
915resolution -l shows 1440x900 available, but they're still not in the screen resolution GUI or xrandr.

I also tried changing the modeline to -vsync, but no luck.

---

### Post by jjbean on 2007-08-17
And I thought my HP monitor was a pain.  I would follow w4ett's advice and go back to the base driver and give it a go.

---

### Post by Big Ben on 2007-08-17
I'm seriously banging my head against the wall here.

Tried "sudo dpkg-reconfigure -phigh xserver-xorg" and selected "intel", although it appears to have already been selected. Rebooted, and now 1440x900 is available in the GUI (and Compiz stopped working for some reason), but if I select 1440x900 and click Apply,  X crashes and I get back to the login screen.

The even weirder part is that the login screen is a different resolution that only takes up the middle part of the screen as if it were a 4:3 display. After logging in, I'm back to a stretched 1024x768.

Any suggestions?

---

### Post by w4ett on 2007-08-17
That IS wierd....Well at least there is some progress 8)

Now do the same:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

now select 'i810 as the driver and try again.

BTW, checked your blog....nice pics and bikes!

---

### Post by Big Ben on 2007-08-17
Thanks, w4ett.

Unfortunately the behavior is the same when I choose i810. X crashes if I choose 1440x900.

---

### Post by w4ett on 2007-08-17
> **Big Ben said:**
> I'm seriously banging my head against the wall here.

Tried "sudo dpkg-reconfigure -phigh xserver-xorg" and selected "intel", although it appears to have already been selected. Rebooted, and now 1440x900 is available in the GUI (and Compiz stopped working for some reason), but if I select 1440x900 and click Apply,  X crashes and I get back to the login screen.

The even weirder part is that the login screen is a different resolution that only takes up the middle part of the screen as if it were a 4:3 display. After logging in, I'm back to a stretched 1024x768.

Any suggestions?

As far as the login resolution this section:

> SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00" "1280x800_60.00" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection


you are missing the:

> "1280x1024"

when x is crashing it is reverting to the next resolution in the line.

The final thing I can suggest is to now try the 915 resolution script I linked before.....worth a try anyway now that we've worked our way up from the basic intel driver.

---

### Post by Big Ben on 2007-08-17
No luck.

The dpkg thing rewrote xorg.conf, so now the relevant section no longer has my modelines:
```
Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"GH-AWG193SD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
915resolution -l :
```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 1440x900, 32 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1440x900, 8 bits/pixel
Mode 41 : 1440x900, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1440x900, 16 bits/pixel
Mode 50 : 1440x900, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1440x900, 24 bits/pixel

```
xrandr :
```
 SZ:    Pixels          Physical       Refresh
 0   1440 x 900    ( 366mm x 366mm )   60  
 1   1280 x 1024   ( 366mm x 366mm )   75   60  
*2   1024 x 768    ( 366mm x 366mm )   75   70  *60  
 3    832 x 624    ( 366mm x 366mm )   75  
 4    800 x 600    ( 366mm x 366mm )   72   75   60   56  
 5    640 x 480    ( 366mm x 366mm )   75   73   67   60  
 6    720 x 400    ( 366mm x 366mm )   70  
 7   1440 x 1440   ( 366mm x 366mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none

```

I'm lost.

---

### Post by w4ett on 2007-08-18
xrandr can also be used to change your resolutions on the fly see:

[http://www.debian-administration.org/articles/201](http://www.debian-administration.org/articles/201)

The modelines (if you want to use them)  can be copy and pasted back to your xorg.conf...the old xorg.conf files will be located in the folder  /etc/X11/..you can rename them if you desire.

as far as other ideas, I going to have to sleep on it....Late Friday night here..been a long day.

Final thought....try running the live cd and see if the system will pick up on the eid of the monitor and if it will attempt to go into 1440x900.

---

### Post by Big Ben on 2007-08-18
"xrandr --size 1440x900" also crashes x.

I'll try the liveCD again and see if I can make any progress.

Thanks for all your help.

---

### Post by Big Ben on 2007-08-18
I couldn't get it to work on the liveCD either.

This is doubly frustrating because I'm dual booting with XP, and Windows found the 1440x900 resolution immediately, so it's not that the monitor can't do it or that the intel card can't handle it. 

I have to get other things done, so I'm giving up for now and I'll just have to use Windows for anything related to pictures or video. I want to thank everyone who helped, even though it didn't work out. I would appreciate new suggestions if anyone has them.

---

### Post by dougfractal on 2007-08-18
Your xorg.conf file got shot to pieces

so Xorg just did the best it could.

[http://www.mepislovers.org/forums/showthread.php?p=69609](http://www.mepislovers.org/forums/showthread.php?p=69609)
```

Section "Monitor"
Identifier	"GH-AWG193SD"
VendorName "Generic LCD"
ModelName "LCD Panel 1440x900"
Option "DPMS"
HorizSync 31.5 - 100.0       #    HorizSync          30-83
VertRefresh 59.0 - 75.0      #   VertRefresh        55-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
SubSection "Display"
Depth 8
Modes "1440x900" "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1280x1024" "1024x768" "800x600"
EndSubSection
EndSection


```


I've been working on intel's the last few days and come up with a diagnostic tool

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by Big Ben on 2007-08-18
Thanks, dougfractal.

I tried the xorg you attached, and then tried modifying it as described in the mepis thread you linked, but I'm still stuck with only 1280 x 768   1024 x 768      800 x 600    640 x 480   1280 x 800     1280 x 1280  in the GUI and in xrandr.

Do I need to delete 915resolution?

My current xorg is now:
```
Section "Monitor"
Identifier	"GH-AWG193SD"
VendorName "Generic LCD"
ModelName "LCD Panel 1440x900"
Option "DPMS"
HorizSync 31.5 - 100.0       #    HorizSync          30-83
VertRefresh 59.0 - 75.0      #   VertRefresh        55-75
#Following modeline from Mepis 6.0 xorg.conf got monitor width to display properly
Modeline "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 +HSync +VSync
EndSection
Section "Monitor"
Identifier	"GH-AWG193SD"
VendorName "Generic LCD"
ModelName "LCD Panel 1440x900"
Option "DPMS"
HorizSync 31.5 - 100.0       #    HorizSync          30-83
VertRefresh 59.0 - 75.0      #   VertRefresh        55-75
#Following modeline from Mepis 6.0 xorg.conf got monitor width to display properly
Modeline "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 +HSync +VSync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
SubSection "Display"
Depth 8
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" 
EndSubSection
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
SubSection "Display"
Depth 8
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" 
EndSubSection
EndSection
```

I'm attaching the output from your script.

---

### Post by Big Ben on 2007-08-18
Oops.
My xorg isn't that confused, it was just a cut and paste error.
```
Section "Monitor"
Identifier	"GH-AWG193SD"
VendorName "Generic LCD"
ModelName "LCD Panel 1440x900"
Option "DPMS"
HorizSync 31.5 - 100.0       #    HorizSync          30-83
VertRefresh 59.0 - 75.0      #   VertRefresh        55-75
#Following modeline from Mepis 6.0 xorg.conf got monitor width to display properly
Modeline "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 +HSync +VSync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
SubSection "Display"
Depth 8
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" 
EndSubSection
EndSection
```

---

### Post by dougfractal on 2007-08-19
try the i810 driver

```
sudo apt-get install --reinstall xserver-xorg-video-i810
```
you might have to remove xserver-xorg-video-intel
**sudo apt-get remove xserver-xorg-video-intel**

```
Section "Device"
    Identifier    "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
  #  VideoRam    131072
EndSection
```

also try (I know you have done already) 
In Section "Device"
**Option "NoDDC"**

---

### Post by Arthur Archnix on 2007-08-19
In section device, until driver, what happens when you change i810 to "intel", and then restart x, with ctrl alt backspace

---

### Post by Big Ben on 2007-08-19
dougfractal,

At least that changed the available resolutions: 
 0   1920 x 1440   ( 488mm x 366mm )   60  
 1   1600 x 1200   ( 488mm x 366mm )   75  
 2   1280 x 1024   ( 488mm x 366mm )   75  
*3   1024 x 768    ( 488mm x 366mm )  *75  
 4    800 x 600    ( 488mm x 366mm )   75  
 5    640 x 480    ( 488mm x 366mm )   75  

But still no 1440x900, even though that's the only resolution in xorg.conf:
```
Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option "NoDDC"
EndSection

Section "Monitor"
Identifier	"GH-AWG193SD"
VendorName "Generic LCD"
ModelName "LCD Panel 1440x900"
Option "DPMS"
HorizSync 31.5 - 100.0       #    HorizSync          30-83
VertRefresh 59.0 - 75.0      #   VertRefresh        55-75
#Following modeline from Mepis 6.0 xorg.conf got monitor width to display properly
Modeline "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 +HSync +VSync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
SubSection "Display"
Depth 8
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" 
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" 
EndSubSection
EndSection
```

Any other ideas?


Arthur Archnix,
Thanks, but I just went through all of that with "intel" with no success.That's why we're trying something different now.

---

### Post by Arthur Archnix on 2007-08-19
Ok, thanks. I thought I'd gone through your output and didn't see you replace it with intel, which is why I'd recommended it. For instance, even now your output shows the wrong driver.

Best,

---

### Post by Big Ben on 2007-08-19
Thanks Arthur Archnix, any help is appreciated. I'm just following dougfractal's advice to try reverting to the old "i810", since nothing we've tried has worked with the "intel".

---

### Post by Arthur Archnix on 2007-08-19
Sorry to harp, or cover old ground, but would you mind posting the output of lspci

Thank you

---

### Post by Big Ben on 2007-08-19
We're making progress!

After reverting to i810, I tried 915resolution again, and now I have 1440x900 available in the GUI. Unfortunately, when I select it, the screen is now too wide (The "Applications" menu and the right half of the task tray are past the sides of the screen.) Do I fix this with a modeline?

Arthur Archnix, here's the lspci output:
```
ben@ben-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
```

---

### Post by Arthur Archnix on 2007-08-19
Ok, again i'm sorry if this is covering old ground for you, I'm just trying to make certain that the basics are covered. I apologize if this is old news. What does this, plus a reboot do:
```
sudo apt-get remove 915resolution
sudo apt-get install xorg-xserver-video-intel
```

Edit: you can get back to where you were by reinstalling 915 res, and apt-get removing the xorg-xserver-video-intel deal, but please let me know what the outcome of that was.

Best,

---

### Post by Ozeuss on 2007-08-19
> **Arthur Archnix said:**
> Ok, again i'm sorry if this is covering old ground for you, I'm just trying to make certain that the basics are covered. I apologize if this is old news. What does this, plus a reboot do:
```
sudo apt-get remove 915resolution
sudo apt-get install xorg-xserver-video-intel
```
i'm with arthur- that method also worked for me, for that same resolution. it is best to run ```
sudo dpkg-econfigure xserver-xorg
``` aftwerwards. main thing is to change the driver from i810 to intel.
pardon me for bugging, i didn't read the whole thread and don't know if you tried this methot before.

---

### Post by Big Ben on 2007-08-19
Ok, I'll thry that again and let you know what happens.

---

### Post by Big Ben on 2007-08-19
Curiouser and curiouser...

Now I've got what claims to be 1440x900, but it's squished up into part of the screen. Big black bars on the right and left of the screen, and everything is thinner than it should be.

---

### Post by Arthur Archnix on 2007-08-19
Ok, so now try:
```
gksudo gedit /etc/X11/xorg.conf
```
and change the driver portion from i810 to intel, and again, reboot.

Any change?

---

### Post by Big Ben on 2007-08-19
Since I did the dpkg-reconfigure, it already is set as "intel".

```
Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"GH-AWG193SD"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Rebooting didn't help. Everything is still squished into what looks like a 4:3 sized portion of the screen.

---

### Post by Arthur Archnix on 2007-08-19
ok, well this could be just a sync problem. Can you post the exact name and model of your monitor.

Edit, By the way, I' encouraged from what you've told me that we're making progress.

---

### Post by Big Ben on 2007-08-19
Unfortunately I need to leave now and won't be back for another day and a half. I appreciate everyone's help, and I hope someone can give me some more suggestions to help me though this. I'd hate to have to use Windows for everything graphics-related.

The monitor is a cheap 19" widescreen from a Japanese company called Greenhouse, and the model is [GH-AWG193SDB]("http://www.green-house.co.jp/products/lcd/awg193sd/awg193sd_spec.html").

For reference, I ran dougfractal's script again, and I'm attaching the output.

---

### Post by w4ett on 2007-08-19
After all the modifications of your xorg, and the failure of the 915 resolution patch, I too am wondering if the monitor specifications are wrong.  (it's been known to happen before), or the EDID is not being correctly transferred from the monitor.

---

### Post by Big Ben on 2007-08-20
w4ett,

How would I go about checking that? 

Xorg's autodetect is correctly getting the model number GH-AWG193SD, and all the documentation says its native resolution is 1440x900.

Granted, its a slightly shady-looking company that just recently started making monitors. And while XP was able to run 1440x900, fonts and such don't look as smooth as I expected them to.

Is there any way to find out what the real specifications are?

---

### Post by w4ett on 2007-08-20
BigBen, review this post:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

It's got a few cobwebs on it, but the commands and concepts still apply to feisty.

---

### Post by dougfractal on 2007-08-20
I found this posiible fix.

[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b4edf9f796d7f1ff720372aa5e7f4759618cf6d3](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b4edf9f796d7f1ff720372aa5e7f4759618cf6d3)
> Added by TonyS, 12 May 07

I impulsively bought a ViewSonic VG1930WM 19" widescreen LCD (at a distinctly newfangled 1440x900 native resolution) without considering the possible pain in making the low powered Intel i810 (82845G/GL) graphics in my old Compaq EVO desktop (and Feisty) talk to it...

It really was a hassle, but I've solved it and thought someone, somewhere, sometime might benefit from knowing how.

Just a wee note first that the "915resolution" solution described in the wiki above did NOT work. After fiddling for ages I got the mode installed and the GUI would come up OK, but the display was corrupt, with the left edge missing in action off the edge of the window, the top inch or so blank and the right hand side two inches peculiarly munted. Hopeless.

OK, here's what solved it for me...

---

### Post by Big Ben on 2007-08-20
w4ett, I went through the linked post step by step, but it didn't work. After following the instructions my xorg.conf reads:
```
Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
        Option "NoDDC"
EndSection

Section "Monitor"
	Identifier	"GH-AWG193SD"
     HorizSync          30-83
     VertRefresh        55-75
# 1440x900 @ 59.89 Hz (GTF) hsync: 55.82 kHz; pclk: 106.28 MHz
  Modeline "1440x900_59.89"  106.28  1440 1520 1672 1904  900 901 904 932 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900_59.89"  "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900_59.89"  "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900_59.89" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900_59.89" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_59.89" "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_59.89" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection
```
but I still can't choose 1440x900 in the GUI.


dougfractal, I had seen that in the community docs before and tried it several times, but for some reason it doesn't work for me. I'll try it one more time just in case.

---

### Post by Big Ben on 2007-08-20
OK, tried it. Like before, it gives me the option of 1440x900 in the GUI, but choosing it crashes x.

What's next? Could this be fixed with a new graphics card? Or do I just have to live with a widescreen monitor that won't display widescreen resolution?

---

### Post by w4ett on 2007-08-20
Ben, give us your /var/log/xorg.0.log and let's see what happens to cause the crash.

---

### Post by w4ett on 2007-08-20
Plus I completely forgot to ask...are you using a VGA or DVI cable?

---

### Post by Big Ben on 2007-08-21
Attatching the log file.

What happens is, gnome starts up in a stretched 1024x768. I choose 1440x900 from the GUI, and x crashes. After a few seconds, I get the login screen, and the login screen appears to be the weird squished 1440x900 with blank black bars on the left and right. After login, I'm back to the stretched 1024x768.

I'm using the standard blue analog (VGA?) cable.


```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ben-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 21 13:16:26 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "GH-AWG193SD"
(**) |   |-->Device "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
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
(II) PCI: 00:00:0: chip 8086,2580 card 107b,4037 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2581 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2582 card 107b,4037 rev 04 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,2668 card 107b,4037 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2666 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 107b,4037 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 107b,4037 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 107b,4037 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 107b,4037 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 107b,4037 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 107b,4037 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 107b,4037 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 107b,4037 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 107b,4037 rev 03 class 0c,05,00 hdr 00
(II) PCI: 06:00:0: chip 10ec,8139 card 6409,001c rev 10 class 02,00,00 hdr 00
(II) PCI: 06:05:0: chip 11c1,5811 card 8086,4556 rev 61 class 0c,00,10 hdr 00
(II) PCI: 06:08:0: chip 8086,1064 card 107b,4037 rev 03 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff300000 - 0xff3fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbf900000 - 0xbf9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:0), (0,5,5), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xff700000 - 0xff7fffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xbfd00000 - 0xbfdfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xff600000 - 0xff6fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xbfc00000 - 0xbfcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xff500000 - 0xff5fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xbfb00000 - 0xbfbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:3), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xff400000 - 0xff4fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xbfa00000 - 0xbfafffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,6), BCTRL: 0x0206 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0xbfe00000 - 0xbfefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xffa80000/19, 0xd0000000/28, 0xffa40000/18, I/O @ 0xec00/3
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
	[0] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[1] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[2] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[3] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[4] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[5] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[8] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[9] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[1] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[2] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[3] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[4] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[5] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[8] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[9] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
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
	[4] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[5] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[6] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[7] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[8] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[9] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
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
(==) AIGLX enabled
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 14.94.94
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[5] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[6] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[7] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[8] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[9] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[5] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[6] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[7] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[8] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[9] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[32] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFFA80000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "GRN", prod id 0
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (400, 250) mm
(**) intel(0): DPI set to (91, 146)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xffa40000 - 0xffa7ffff (0x40000) MS[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MS[B]
	[2] 0	0	0xffa80000 - 0xffafffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xff8fd000 - 0xff8fdfff (0x1000) MX[B]
	[8] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[9] -1	0	0xff8ffc00 - 0xff8ffcff (0x100) MX[B]
	[10] -1	0	0xffa3bc00 - 0xffa3bfff (0x400) MX[B]
	[11] -1	0	0xffa3c000 - 0xffa3ffff (0x4000) MX[B]
	[12] -1	0	0xffa40000 - 0xffa7ffff (0x40000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] 0	0	0x0000ec00 - 0x0000ec07 (0x8) IS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[35] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[36] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(**) intel(0): VideoRam: 64000 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(WW) intel(0): Failed to allocate back buffer space.
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       small DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(WW) intel(0): Failed to allocate back buffer space.
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(WW) intel(0): Failed to allocate depth buffer space.
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       small DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(WW) intel(0): Failed to allocate depth buffer space.
(WW) intel(0): Not enough video memory.  Disabling DRI.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x00037fff: xaa scratch (64 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x04a77000 physical)
(II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x1ad70000 physical)
(II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x260a2000 physical)
(II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x10d28000 physical)
(II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x02fdd000 physical)
(II) intel(0): 0x007d0000-0x03021fff: front buffer (41288 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x007c0000 (pgoffset 1984)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007c4000 (pgoffset 1988)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x007c5000 (pgoffset 1989)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x007c9000 (pgoffset 1993)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x007d0000 (pgoffset 2000)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Disabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) intel(0): Setting screen physical size to 408 x 255
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ja"
(**) Generic Keyboard: XkbLayout: "ja"
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
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "GRN", prod id 0
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "GRN", prod id 0
SetClientVersion: 0 9
```

---

### Post by w4ett on 2007-08-21
Big Ben: to me the log doesn't look bad except for this:

> (II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(**) intel(0): VideoRam: 64000 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(WW) intel(0): Failed to allocate back buffer space.
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       small DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(WW) intel(0): Failed to allocate back buffer space.
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(WW) intel(0): Failed to allocate depth buffer space.
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       small DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(WW) intel(0): Failed to allocate depth buffer space.
(WW) intel(0): Not enough video memory.  Disabling DRI.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)

Possibly a Video Ram problem, IMO. You might try running memtest and see the results are. X can't allocate the memory as you see above.  Other than that I'm running out of suggestions.  

To answer your previous question, a replacement Video Card, would give you better 3d rendering definately, if you are willing to spend the extra yen,  A decent 128-256MB Nvidia card (Compiz Fusion capable) here in the States now run between 30-40 $.  I'd also invest in a DVI cable (less trouble in the long run).

---

### Post by Big Ben on 2007-08-21
The 64000 is a value I entered manually on the advice of one of the threads linked above. I'll try running dpkg-reconfigure again leaving that blank.

Do you think there's much hope of a new video card fixing the resolution problem? I've been impressed with what compiz fusion does even on this old intel chipset.

---

### Post by w4ett on 2007-08-21
> **Big Ben said:**
> The 64000 is a value I entered manually on the advice of one of the threads linked above. I'll try running dpkg-reconfigure again leaving that blank.

Do you think there's much hope of a new video card fixing the resolution problem? I've been impressed with what compiz fusion does even on this old intel chipset.

Yep...give that a try.....just remember that the bios selected video ram has to match what you manually input in xorg.conf...64Mb is actually VideoRam 65536

As in all things, a stand alone card will give you better video performance than the shared video memory and chipset.

---

### Post by Big Ben on 2007-08-21
Progress!

After taking out that 64000, I was able to select 1440x900 without x crashing. Now the only problem is that it's squished into what looks like a 4:3 portion of the screen with black bars on the right and left, like a horizontal letterbox effect.

---

### Post by w4ett on 2007-08-21
Can you now use the monitors manual adjustments to stretch the display, or is there only an auto adjustment?

---

### Post by Big Ben on 2007-08-21
There's an adjustment available, but it's already stretched to 100% (slightly wider than before, but I've still got around 4cm of black on the left and 1cm on the right.

---

### Post by w4ett on 2007-08-21
Definite progress....Now I would make sure the refresh rate is set at 60Hz....not the 58.xx that was previously set in your xorg.conf.  it might just work this time!  This is close...you might have to fiddle a bit with the resolution rate.

---

### Post by Big Ben on 2007-08-21
The GUI says 60. Do you mean to fiddle within xorg.conf?

---

### Post by w4ett on 2007-08-21
Yep like here:

> SubSection "Display"
		Depth		1
		Modes		[COLOR="Red"]"1440x900_59.89" [/COLOR] "1280x1024" "1280x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection

'1440x900_60

---

### Post by Big Ben on 2007-08-21
No visible difference. What other sorts of values should I be trying? Should I be adding a new modeline?

I don't know if it's relevant, but xvidtune -show gives me:
```
"1440x900"    106.50   1440 1520 1672 1904    900  903  909  934 +hsync -vsync

```

xorg.conf:
```
Section "Monitor"
	Identifier	"GH-AWG193SD"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by w4ett on 2007-08-21
Yes...a new modeline now is worth a shot.....just make sure to backup your xorg.conf first.

---

### Post by Big Ben on 2007-08-21
I tried a new modeline, but I don't notice any difference. Still skinny.
Which of those values should I try tweaking?
```
Section "Monitor"
	Identifier	"GH-AWG193SD"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"GH-AWG193SD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Also, I'm seriously considering running out to the store and buying an nVidia card. Would a GeForce 7300LE with 128k be enough to handle compiz fusion and such. (I suppose it's superior to the intel chipset I've got either way, but I don't want to spend the money if I can get by without it.)

---

### Post by w4ett on 2007-08-21
At this point, I would re-try the 915 resolution patch and see if it will improve the display....Also (since I don't read Japanese) does the manual or online documents give you an other refresh rates at your desired 1440x900 resolution rates?  If so enable the additional refresh rates and see what you get.

The Nvidia card you mention will easily be able to use Compiz, in fact you will see a marked improvement in display response and clarity over your intel chipset. I have a 6200/128Mb card and it works well.   If you do decide to go that route, the easiest method to install the proprietary driver is to simply enable it from the restricted driver manager.  If that gives you any problems with installation, use Envy.

---

### Post by Big Ben on 2007-08-21
I tried 915resolution again, but it seems to have no effect.

The only refresh rate given in the manual for 1440x900 is 59.89.  Should I try a new modeline with that instead of 60.0?

---

### Post by w4ett on 2007-08-21
Yes...try the modeline adjustment....Also give serious consideration to using the DVI input...don't know if your intel chipset provides one, but dvi cures a lot of ills if you have the capability.

Also you might want to have a look at the new backported driver:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

---

### Post by Big Ben on 2007-08-22
Neither the modeline nor the backported intel driver made any difference. I'll need a new video card to try DVI, but I think I'm going to go out and buy an nVidia card sometime in the next few days anyway.

I'm disappointed that this doesn't seem to be solvable with my current hardware, since XP was able to detect and use the monitor fine on the same box. That means it's not that the card and monitor are incompatible, just that ubuntu doesn't know what to do with them. This is the first time ubuntu has ever really let me down.

 I really appreciate everyone's help trying to work me through this.

---

### Post by dougfractal on 2007-08-23
>  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

I'm not sure but modeline might be case sensitive. 

> Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +**VSync**
 or commonly **-hsync +vsync**

---

### Post by Big Ben on 2007-08-29
I'm not sure whether I should mark this "Solved", but I've got the resolution I wanted. Pity I couldn't get it to work with the Intel chipset.

I bought myself a cheap GeForce 7300LE, installed the restricted drivers, and everything is fine. (And the cube is spinning even more beautifully than before.) 

Thanks to eveyone who helped.

---

