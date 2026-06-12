---
title: "Gutsy and nvidia issues"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by c3r3al_kill3r on 2007-10-22
I've just clean installed Gutsy over my Feisty install. I gave up on feisty because, firstly, it wouldn't recognise my wireless card and once I got that sorted I couldn't get wpa working properly. Anywho, on Gutsy the wireless worked out of the box. hurrah thought I. 

My joy was short lived however when my nvidia 7800 gtx wouldn't install correctly using the restricted driver manager. It worked fine in Feisty, had beryl running etc, but now when I enable the drivers in Gutsy and reboot, it defaults to 640x480 res and I can't change it. To get back to it's proper resolution I have to disable the driver and revert to the vesa driver. 

I've tried installing with Envy, but the same thing happens. Is this a known bug? Any help would be greatly appreciated.

Apart from that everything else works fine, it's a significant improvement on Feisty. Not sure i'm quite ready to ditch winblows yet.

---

### Post by realvz on 2007-10-22
can you post your /etc/X11/xorg.conf file here

---

### Post by c3r3al_kill3r on 2007-10-22
thanks, xorg.conf below;

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"

 #  
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

 #  
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 #  
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by realvz on 2007-10-22
this is the failsafe xorg.conf file...can you post 
these files
/etc/X11/xorg.conf.broken
/var/log/Xorg.0.log

---

### Post by c3r3al_kill3r on 2007-10-22
sorry. i had to remove the driver to use the thing. the log and broken conf are below;

```
Section "Files"
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
	Identifier	"nVidia Corporation G70 [GeForce 7800 GTX]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"formac TFT"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7800 GTX]"
	Monitor		"formac TFT"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```


~~~ LOG ~~~

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux pru 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 22 12:23:25 2007
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cd8a0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0091 card 1682,2180 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:06:0: chip 1814,0301 card 1737,0055 rev 00 class 02,80,00 hdr 00
(II) PCI: 05:0a:0: chip 1095,3114 card 1043,8167 rev 02 class 01,04,00 hdr 00
(II) PCI: 05:0c:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00009000 - 0x0000afff (0x2000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd3000000 - 0xd4ffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd5100000 - 0xd51fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7800 GTX] rev 161, Mem @ 0xd0000000/24, 0xc0000000/28, 0xd1000000/24, I/O @ 0xb000/7, BIOS @ 0xd2000000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd4008000 - 0xd400bfff (0x4000) MX[B]
	[1] -1	0	0xd400c000 - 0xd400c3ff (0x400) MX[B]
	[2] -1	0	0xd4000000 - 0xd4007fff (0x8000) MX[B]
	[3] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[4] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[5] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[8] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[9] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[13] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[14] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[15] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[16] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[17] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[27] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[28] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd4008000 - 0xd400bfff (0x4000) MX[B]
	[1] -1	0	0xd400c000 - 0xd400c3ff (0x400) MX[B]
	[2] -1	0	0xd4000000 - 0xd4007fff (0x8000) MX[B]
	[3] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[4] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[5] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[8] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[9] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[13] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[14] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[15] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[16] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[17] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[27] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[28] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
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
	[4] -1	0	0xd4008000 - 0xd400bfff (0x4000) MX[B]
	[5] -1	0	0xd400c000 - 0xd400c3ff (0x400) MX[B]
	[6] -1	0	0xd4000000 - 0xd4007fff (0x8000) MX[B]
	[7] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[8] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[9] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[12] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[20] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[21] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[22] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[33] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[34] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd4008000 - 0xd400bfff (0x4000) MX[B]
	[5] -1	0	0xd400c000 - 0xd400c3ff (0x400) MX[B]
	[6] -1	0	0xd4000000 - 0xd4007fff (0x8000) MX[B]
	[7] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[8] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[9] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[12] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[20] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[21] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[22] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[33] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[34] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd4008000 - 0xd400bfff (0x4000) MX[B]
	[5] -1	0	0xd400c000 - 0xd400c3ff (0x400) MX[B]
	[6] -1	0	0xd4000000 - 0xd4007fff (0x8000) MX[B]
	[7] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[8] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[9] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[12] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[24] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[25] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[26] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[29] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[30] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[31] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[32] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[36] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[37] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[39] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.112
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G70 Board - p347h2  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: FOR  Model: 919  Serial#: 65536
(II) VESA(0): Year: 2005  Week: 21
(II) VESA(0): EDID Version: 1.2
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) VESA(0): Gamma: 1.80
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.641 redY: 0.353   greenX: 0.288 greenY: 0.626
(II) VESA(0): blueX: 0.142 blueY: 0.077   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 91.2 MHz   Image Size:  376 x 301 mm
(II) VESA(0): h_active: 1280  h_sync: 1310  h_sync_end 1410 h_blank_end 1432 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1028  v_sync_end 1034 v_blanking: 1062 v_border: 0
(II) VESA(0): Monitor name: formac TFT
(II) VESA(0): Monitor name: 1900 AU3-0
(II) VESA(0): Serial No: Version 1.80N
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0019f2190900000100
(II) VESA(0): 	150f010280261e502e1d70a45a49a024
(II) VESA(0): 	13505400000001010101010101010101
(II) VESA(0): 	010101010101a0230098500026401e64
(II) VESA(0): 	4600782d11000018000000fc00666f72
(II) VESA(0): 	6d616320544654200a20000000fc0031
(II) VESA(0): 	393030204155332d300a2020000000ff
(II) VESA(0): 	0056657273696f6e20312e38304e002d
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x1024"   91.20  1280 1310 1410 1432  1024 1028 1034 1062 -hsync -vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009f03
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Failsafe Monitor: Using hsync value of 63.69 kHz
(II) VESA(0): Failsafe Monitor: Using vrefresh value of 59.97 Hz
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0): Display dimensions: (380, 300) mm
(**) VESA(0): DPI set to (85, 86)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11a)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd4008000 - 0xd400bfff (0x4000) MX[B]
	[5] -1	0	0xd400c000 - 0xd400c3ff (0x400) MX[B]
	[6] -1	0	0xd4000000 - 0xd4007fff (0x8000) MX[B]
	[7] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[8] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[9] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[12] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[24] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[25] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[26] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[29] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[30] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[31] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[32] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[36] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[37] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[39] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.112
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G70 Board - p347h2  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xc0000000,0x10000000)
(II) VESA(0): virtual address = 0x2b7ae747f000,
	physical address = 0xc0000000, size = 268435456
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

I really have to apologise, i know my way around a kernel but im very much a linux noob. I assume you'll need the log from when the restricted drivers are enabled for it to be of any use?

---

### Post by c3r3al_kill3r on 2007-10-22
Solved this issue. I used Envy to completely remove the native Nvidia driver then reinstalled using Envy again. I then removed restricted driver manager et voila, it's all working. Thanks

---

