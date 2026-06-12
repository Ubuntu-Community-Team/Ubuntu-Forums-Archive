---
title: "[SOLVED] Problems installing fglrx"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-10-01
Hi everyone,

After using Ubuntu for about a month I decided to give Kubuntu a go (I like the interface better), so I went tor a complete reinstall. As a results of this, I have to reinstall the driver for my graphics card, fglrx. Here are my computer specs:
* ATI radeon X800XL
*Sempron 3200+
*1 GiB RAM

I have tried to install fglrx using the guide found [here]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") as this is what I used when I installed in it Ubuntu. Now, I've gotten almost to the end of the guide and things have fowled up. I get to the section called "Finished the installation" and when I try to reboot, it doesn't work. I just get taken to a black screen with a blinking underscore in the upper left corner of the screen.

Does anyone either know how to:
1) Fix up whatever I have done wrong so far with the guide to make that work, or
2) Undo what I have done in the guide so far so I can install using Envy.

Here is my xorg.conf file (people helping always seem to ask for this first)

```
Section "ServerLayout"
	Identifier     "XFree86 Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
# PS/2 Mouse not detected
# Serial Mouse not detected
        InputDevice    "USB Mouse" "CorePointer"
# compiz, beryl 3D-Support with DRI & Composite
        Option         "AIGLX"     "true"
EndSection

Section "ServerFlags"
	Option "AllowMouseOpenFail"  "true"
	
EndSection

Section "Files"
	RgbPath      "/usr/share/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi:unscaled"
	FontPath     "/usr/share/fonts/X11/100dpi:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/Speedo"
	FontPath     "/usr/share/fonts/X11/PEX"
# Additional fonts: Locale, Gimp, TTF...
	FontPath     "/usr/share/fonts/X11/cyrillic"
#	FontPath     "/usr/share/fonts/X11/latin2/75dpi"
#	FontPath     "/usr/share/fonts/X11/latin2/100dpi"
# True type and type1 fonts are also handled via xftlib, see /etc/X11/XftConfig!
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/usr/share/fonts/truetype"
	FontPath     "/usr/share/fonts/latex-ttf-fonts"
EndSection

Section "Module"
# Comments: see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=346408
	Load  "dbe" # Double Buffering Extension, very important.
	Load  "dri" # This shouldn't be available choice if user has selected driver vga, vesa or nv.
	Load  "glx" # GLX Extension.
	Load  "freetype" # Freetype fonts.
	Load  "type1"  # Type 1 fonts
	Load  "record" # Developer extension, usually not needed
#	Load  "extmod" # This is okay, but if you look into "man xorg.conf" you'll find option NOT to include DGA extension with extmod, and for a good reason.. DGA causes instability as it access videoram without consulting X about it.
	SubSection      "extmod"
		Option          "omit xfree86-dga"
	EndSubSection
#	Load  "speedo" # Speedo fonts, this module doesn't exist in Xorg 7.0.17
# The following are deprecated/unstable/unneeded in Xorg 7.0
#       Load  "ddc"  # ddc probing of monitor, this should be never present, as it gets automatically loaded.
#	Load  "GLcore" # This should be never present, as it gets automatically loaded.
#       Load  "bitmap" # Should be never present, as it gets automatically loaded. This is a font module, and loading it in xorg.conf makes X try to load it twice.
EndSection

Section "Extensions"
	# beryl and compiz need this, but it can cause bad (end even softreset-resistant)
	# effects in some graphics cards, especially nv.
	# Option "Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
        Option      "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"

EndSection

Section "InputDevice"
	Identifier  "Serial Mouse"
	Driver      "mouse"
	Option      "Protocol" "Microsoft"
	Option      "Device" "/dev/ttyS0"
	Option      "Emulate3Buttons" "true"
	Option      "Emulate3Timeout" "70"
	Option	    "SendCoreEvents"  "true"
EndSection

Section "InputDevice"
	Identifier  "PS/2 Mouse"
	Driver      "mouse"
	Option      "Protocol" "auto"
Option          "ZAxisMapping"          "4 5"
	Option      "Device" "/dev/psaux"
	Option      "Emulate3Buttons" "true"
	Option      "Emulate3Timeout" "70"
	Option	    "SendCoreEvents"  "true"
EndSection

Section "InputDevice"
        Identifier      "USB Mouse"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mice"
	Option		"SendCoreEvents"	"true"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "5"
EndSection

# Auto-generated by KNOPPIX mkxf86config

Section "Monitor"
	Identifier	"Monitor0"
	Option	"DPMS"	"true"
#	HorizSync    28.0 - 78.0 # Warning: This may fry very old Monitors
	HorizSync    28.0 - 96.0 # Warning: This may fry old Monitors
	VertRefresh  50.0 - 75.0 # Very conservative. May flicker.
#	VertRefresh  50.0 - 62.0 # Extreme conservative. Will flicker. TFT default.
	# These are the DDC-probed settings reported by your monitor.
	# 1280x1024, 75.0Hz; hfreq=79.98, vfreq=75.03
	ModeLine "1280x1024"	135.00 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	# 1024x768, 75.0Hz; hfreq=60.02, vfreq=75.03
	ModeLine "1024x768"	 78.75 1024 1040 1136 1312  768  769  772  800 +hsync +vsync
	# 1024x768, 70.0Hz; hfreq=56.48, vfreq=70.07
	ModeLine "1024x768"	 75.00 1024 1048 1184 1328  768  771  777  806 -hsync -vsync
	# 1024x768, 60.0Hz; hfreq=48.36, vfreq=60.00
	ModeLine "1024x768"	 65.00 1024 1048 1184 1344  768  771  777  806 -hsync -vsync
	# 800x600, 75.0Hz; hfreq=46.88, vfreq=75.00
	ModeLine "800x600"	 49.50  800  816  896 1056  600  601  604  625 +hsync +vsync
	# 800x600, 72.0Hz; hfreq=48.08, vfreq=72.19
	ModeLine "800x600"	 50.00  800  856  976 1040  600  637  643  666 +hsync +vsync
	# 800x600, 60.0Hz; hfreq=37.88, vfreq=60.32
	ModeLine "800x600"	 40.00  800  840  968 1056  600  601  605  628 +hsync +vsync
	# 800x600, 56.0Hz; hfreq=35.16, vfreq=56.25
	ModeLine "800x600"	 36.00  800  824  896 1024  600  601  603  625 +hsync +vsync
	# 640x480, 75.0Hz; hfreq=37.50, vfreq=75.00
	ModeLine "640x480"	 31.50  640  656  720  840  480  481  484  500 -hsync -vsync
	# 640x480, 72.0Hz; hfreq=37.86, vfreq=72.81
	ModeLine "640x480"	 31.50  640  656  696  816  480  481  484  504 -hsync -vsync
	# 640x480, 60.0Hz; hfreq=31.47, vfreq=59.94
	ModeLine "640x480"	 25.17  640  648  744  784  480  482  484  509 -hsync -vsync
	# Extended modelines with GTF timings
	# 640x480 @ 100.00 Hz (GTF) hsync: 50.90 kHz; pclk: 43.16 MHz
	ModeLine "640x480"  43.16  640 680 744 848  480 481 484 509  -HSync +Vsync
	# 768x576 @ 60.00 Hz (GTF) hsync: 35.82 kHz; pclk: 34.96 MHz
	ModeLine "768x576"  34.96  768 792 872 976  576 577 580 597  -HSync +Vsync
	# 768x576 @ 72.00 Hz (GTF) hsync: 43.27 kHz; pclk: 42.93 MHz
	ModeLine "768x576"  42.93  768 800 880 992  576 577 580 601  -HSync +Vsync
	# 768x576 @ 75.00 Hz (GTF) hsync: 45.15 kHz; pclk: 45.51 MHz
	ModeLine "768x576"  45.51  768 808 888 1008  576 577 580 602  -HSync +Vsync
	# 768x576 @ 85.00 Hz (GTF) hsync: 51.42 kHz; pclk: 51.84 MHz
	ModeLine "768x576"  51.84  768 808 888 1008  576 577 580 605  -HSync +Vsync
	# 768x576 @ 100.00 Hz (GTF) hsync: 61.10 kHz; pclk: 62.57 MHz
	ModeLine "768x576"  62.57  768 816 896 1024  576 577 580 611  -HSync +Vsync
	# 800x600 @ 100.00 Hz (GTF) hsync: 63.60 kHz; pclk: 68.18 MHz
	ModeLine "800x600"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync
	# 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
	ModeLine "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
	# 1152x864 @ 60.00 Hz (GTF) hsync: 53.70 kHz; pclk: 81.62 MHz
	ModeLine "1152x864"  81.62  1152 1216 1336 1520  864 865 868 895  -HSync +Vsync
	# 1152x864 @ 85.00 Hz (GTF) hsync: 77.10 kHz; pclk: 119.65 MHz
	ModeLine "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907  -HSync +Vsync
	# 1152x864 @ 100.00 Hz (GTF) hsync: 91.50 kHz; pclk: 143.47 MHz
	ModeLine "1152x864"  143.47  1152 1232 1360 1568  864 865 868 915  -HSync +Vsync
	# 1280x960 @ 72.00 Hz (GTF) hsync: 72.07 kHz; pclk: 124.54 MHz
	ModeLine "1280x960"  124.54  1280 1368 1504 1728  960 961 964 1001  -HSync +Vsync
	# 1280x960 @ 75.00 Hz (GTF) hsync: 75.15 kHz; pclk: 129.86 MHz
	ModeLine "1280x960"  129.86  1280 1368 1504 1728  960 961 964 1002  -HSync +Vsync
	# 1280x960 @ 100.00 Hz (GTF) hsync: 101.70 kHz; pclk: 178.99 MHz
	ModeLine "1280x960"  178.99  1280 1376 1520 1760  960 961 964 1017  -HSync +Vsync
	# 1280x1024 @ 100.00 Hz (GTF) hsync: 108.50 kHz; pclk: 190.96 MHz
	ModeLine "1280x1024"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync
	# 1400x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 122.61 MHz
	ModeLine "1400x1050"  122.61  1400 1488 1640 1880  1050 1051 1054 1087  -HSync +Vsync
	# 1400x1050 @ 72.00 Hz (GTF) hsync: 78.77 kHz; pclk: 149.34 MHz
	ModeLine "1400x1050"  149.34  1400 1496 1648 1896  1050 1051 1054 1094  -HSync +Vsync
	# 1400x1050 @ 75.00 Hz (GTF) hsync: 82.20 kHz; pclk: 155.85 MHz
	ModeLine "1400x1050"  155.85  1400 1496 1648 1896  1050 1051 1054 1096  -HSync +Vsync
	# 1400x1050 @ 85.00 Hz (GTF) hsync: 93.76 kHz; pclk: 179.26 MHz
	ModeLine "1400x1050"  179.26  1400 1504 1656 1912  1050 1051 1054 1103  -HSync +Vsync
	# 1400x1050 @ 100.00 Hz (GTF) hsync: 111.20 kHz; pclk: 214.39 MHz
	ModeLine "1400x1050"  214.39  1400 1512 1664 1928  1050 1051 1054 1112  -HSync +Vsync
	# 1600x1200 @ 100.00 Hz (GTF) hsync: 127.10 kHz; pclk: 280.64 MHz
	ModeLine "1600x1200"  280.64  1600 1728 1904 2208  1200 1201 1204 1271  -HSync +Vsync
	# 1680x1050 (Notebook)
	ModeLine "1680x1050" 154.2 1680 1712 2296 2328   1050 1071 1081 1103
	# 1920x1200 @ 60.00 Hz (GTF)  hsync: 74.52; pclk: 193.16 MHz
	ModeLine "1920x1200" 193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +HSync
EndSection

Section "Device"
	### Available Driver options are:-
# sw_cursor is needed for some ati and radeon cards
        #Option     "sw_cursor"
        #Option     "hw_cursor"
        #Option     "NoAccel"
        #Option     "ShowCache"
        #Option     "ShadowFB"
        #Option     "UseFBDev"
        #Option     "Rotate"
	Identifier  "Card0"
# auto-generated by KNOPPIX mkxorgconfig
	Driver      "vesa"
	VendorName  "All"
	BoardName   "All"
#	BusID       "PCI:1:0:0"
#
# compiz, beryl 3D-Support with DRI & Composite
	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

# This two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultColorDepth 16
	Option "AddARGBGLXVisuals" "true"
	Option "DisableGLXRootClipping" "true"
	SubSection "Display"
		Depth     1
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     32
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection
```

---

### Post by gamerteck on 2007-10-01
Can you post your xorg log in /var/log/Xorg.0.log?

Run the command below, to display the errors only and then post it along with the full xorg log.
```

cat /var/log/Xorg.0.log | egrep '(WW|EE)'

```


Also, to reconfigure your xorg back to its default configuration; get to one of the terminal screens, login and run this command.

```

sudo dpkg-reconfigure xserver-xorg

```

Follow the prompts, it's prettty straight forward.  Select the defaults if you're not sure what to do.

---

### Post by eph1973 on 2007-10-01
You might want to post the results of
```
lspci | grep Radeon
```

Also, have you tried running dpkg-reconfigure xserver-xorg?  I think you can choose fglrx as the driver during all the prompts it goes through.  Or are you trying to avoid that?

---

### Post by NovaAesa on 2007-10-01
I used the Knoppix LiveCD to get the following (LiveCD for Ubuntu doesn't work on my computer).

Here's the Xorg.0.log file:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu-hp 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  2 10:56:29 2007
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
(II) PCI: 00:00:0: chip 1002,5950 card 103c,2a24 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 103c,2a24 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a24 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a24 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a24 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a24 rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a24 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 103c,2a24 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,2a25 rev 02 class 04,01,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,554d card 0000,0000 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,556d card 0000,0001 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 11c1,0620 card 11c1,0620 rev 00 class 07,80,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 103c,2a24 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1106,3044 card 103c,2a24 rev 80 class 0c,00,10 hdr 00
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
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) rev 0, Mem @ 0xd0000000/28, 0xfddf0000/16, I/O @ 0xef00/8
(--) PCI: (1:0:1) ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary rev 0, Mem @ 0xfdde0000/16
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
(II) PCI I/O resource overlap reduced 0x00004100 from 0x0000411f to 0x000040ff
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe0000000 to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdcfe000 - 0xfdcfe7ff (0x800) MX[B]
	[1] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[12] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[13] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[14] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[20] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[25] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
	[1] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdcfe000 - 0xfdcfe7ff (0x800) MX[B]
	[1] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[12] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[13] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[14] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[20] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[25] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
	[1] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
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
	[4] -1	0	0xfdcfe000 - 0xfdcfe7ff (0x800) MX[B]
	[5] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[19] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[20] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[21] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[27] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[28] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[30] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[33] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.41.7
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
(II) ATI Proprietary Linux Driver Version Identifier:8.41.7
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.413.1                  
(II) ATI Proprietary Linux Driver Build Date: Sep  7 2007 22:35:20
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x554D) found
(II) AMD Video driver is running on the exact device targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdcfe000 - 0xfdcfe7ff (0x800) MX[B]
	[5] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[19] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[20] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[21] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[27] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[28] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[30] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[33] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) fglrx(0): pEnt->device->identifier=0x81e7888
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdcfe000 - 0xfdcfe7ff (0x800) MX[B]
	[5] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[22] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[23] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[24] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[30] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[31] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[32] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[33] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[34] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[35] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[36] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
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
(**) fglrx(0): Option "DPMS" "true"
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
(--) fglrx(0): Chipset: "ATI RADEON X800 XL" (Chipset = 0x554d)
(--) fglrx(0): (PciSubVendor = 0x0000, PciSubDevice = 0x0000)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfddf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.10
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: R430
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
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
	compiled for 7.1.0, module version = 8.41.7
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information. 
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 398/493MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 27 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.85  960 1008 1104 1248  720 721 724 746 +hsync
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(0): DPI set to (75, 75)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.85  960 1008 1104 1248  720 721 724 746 +hsync
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfdcfe000 - 0xfdcfe7ff (0x800) MX[B]
	[7] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[10] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[11] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[12] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[13] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000ef00 - 0x0000efff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[25] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[26] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[27] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[33] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[34] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[36] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[37] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[38] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[39] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
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
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7fd2000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7fd2000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x07fc0000
(II) fglrx(0): Splitting WC range: base: 0xd0000000, size: 0x7fc0000
(II) fglrx(0): Splitting WC range: base: 0xd4000000, size: 0x3fc0000
(II) fglrx(0): Splitting WC range: base: 0xd6000000, size: 0x1fc0000
(II) fglrx(0): Splitting WC range: base: 0xd7000000, size: 0xfc0000
(II) fglrx(0): Splitting WC range: base: 0xd7800000, size: 0x7c0000
(II) fglrx(0): Splitting WC range: base: 0xd7c00000, size: 0x3c0000
(II) fglrx(0): Splitting WC range: base: 0xd7e00000, size: 0x1c0000
(II) fglrx(0): Splitting WC range: base: 0xd7f00000, size: 0xc0000
(==) fglrx(0): Write-combining range (0xd7f80000,0x40000)
(==) fglrx(0): Write-combining range (0xd7f00000,0xc0000)
(==) fglrx(0): Write-combining range (0xd7e00000,0x1c0000)
(==) fglrx(0): Write-combining range (0xd7c00000,0x3c0000)
(==) fglrx(0): Write-combining range (0xd7800000,0x7c0000)
(==) fglrx(0): Write-combining range (0xd7000000,0xfc0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd6000000,0x1fc0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4000000,0x3fc0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x7fc0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 6991

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxScreenInit+0x505) [0xb79b1725]
3: /usr/bin/X(AddScreen+0x1ee) [0x8073dce]
4: /usr/bin/X(InitOutput+0x21e) [0x80a540e]
5: /usr/bin/X(main+0x27b) [0x807456b]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dedebc]
7: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting
```

When I run > cat /var/log/Xorg.0.log | egrep '(WW|EE)' from Ubuntu recovery mode, nothing happens, it just goes to the next line.

The output of > lspci | grep Radeon is > 01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
01:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary

---

### Post by NovaAesa on 2007-10-01
If I've screwed things up beyond repair, you guys can tell me! I am quite happy to do a reinstall if that's what it needs (I did one only a day ago so I haven't really configured anything yet).

---

### Post by NovaAesa on 2007-10-02
ok, don't worry guys, I've decided to do a reinstall instead (it only took half an hour :)). I'll try tonight to get fglrx working via Envy.

---

