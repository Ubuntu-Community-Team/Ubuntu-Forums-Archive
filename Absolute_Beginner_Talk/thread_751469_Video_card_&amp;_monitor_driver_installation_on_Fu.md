---
title: "Video card &amp; monitor driver installation on Fujitsu-Siemens Amilo notebook"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by vagyok on 2008-04-10
Hi,

I have a Fujitsu Siemens Amilo L7310 notebook and I'm having problems with graphics (and other things) using (k)ubuntu. I'm an (almost) absolute beginner to Linux (this is the first time I have Linux on any of my computers).

Backstory briefly:

A couple of days ago I tried to run the Ubuntu and Kubuntu 7.10 LiveCDs but both gave me a black/blank screen after the boot selection menu. I managed to install Kubuntu 7.10 from the alternate CD using text mode.

However, when Kubuntu was about to load properly for the first time (i.e. not in text mode), I got the same blank screen immediately. I got to a command line using CTRL+ALT+F1, stopped the xserver, installed lynx, downloaded and installed the video card driver from [http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=159](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=159) , rebooted and it seemed to work (GUI loaded).

The problem:

There's something fishy about the graphics. Firstly, it didn't want to go above 1024x768, which it did under WinXP easily. I manually added 1280x1024 (which the readme said was supported) to the Screen/Display subsection in xorg.conf, but when I select it under System Settings it does not resize my desktop, but rather it expands it so that always only part of my desktop is visible and I can move around using the mouse. How can I make it work properly? Also, for 1280x1024 it lists refresh rates of 60 and 70Hz to choose from, but the readme says 60, 75, and 85Hz are supported.

Second, under the Hardware tab in my System Settings, I've got 2 monitors listed (in reality I've got only one), "plug 'n' play (widescreen)" as primary and "unknown" as secondary. I want it to recognize that my notebook has  (only) one LCD monitor, but when I click Configure, I don't know which one to choose and I don't want to damage the monitor by accidentally setting up the refresh rates really badly.

Any help is appreciated.

Here's my xorg.conf:

> Section "Files"
	# path to defoma fonts
    FontPath 	"/usr/share/fonts/X11/misc"
    FontPath 	"/usr/share/fonts/X11/100dpi:unscaled"
    FontPath 	"/usr/share/fonts/X11/75dpi:unscaled"
    FontPath 	"/usr/share/fonts/X11/Type1"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/usr/local/share/fonts"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"vbe"
	Load   "extmod"
	Load  "dri"
	Load  "glx"
	Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"	"on"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	BoardName   "via"
	VendorName  "VIA Tech"
	Driver "via"
EndSection

Section "Monitor"
	Option		"DPMS"
	ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
	ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
	ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
	ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
	ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
	ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
	ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
	ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
	ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
	ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
	ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
	ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
	ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
	ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
	ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
	ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
	ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
	ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
	ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
	ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
	ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
	ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
	#Refresh Rate 60Hz
	Identifier "MonitorGeneric Video Card"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
    Monitor  "MonitorGeneric Video Card"
	DefaultDepth	24
	SubSection "Display"
		Modes  "1024x768"         
		Depth		1
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		4
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		8
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		15
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		16
	EndSubSection
	SubSection "Display"
		Modes  "1024x768" "1280x1024"
		Depth		24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode 0666
	Group 0
EndSection

---

### Post by smurphy_it on 2008-04-10
I noticed you have a VIA video card.  They can be wonky from what I've read.  As for the screen resolution, I noticed that your default screen is 24 (24-bit) but the line reads 1024x768 1280x1024.... this should be reversed so that 1280x1024 is first.

---

### Post by vagyok on 2008-04-10
I reversed it and rebooted.
Now it starts automatically in the 1280x1024 desktop-partly-visible-use-mouse-to-move-around mode. Also, 70Hz is no longer selectable for 1280x1024 under System Settings, only 60Hz.

---

### Post by lackofcreativity on 2008-04-10
Go to your video card section and try changing the driver it's using to vesa or vga. Since they're generic drivers, they should work with most cards.

---

