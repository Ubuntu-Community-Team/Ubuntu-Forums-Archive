---
title: "Screen resolution resets when rebooting machine"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by tsantsa31 on 2008-01-20
I have a Samsung Syncmaster 940bw 19" widescreen monitor with an ATI Radeon card. I have been able to enable desktop effects and get my resolution looking nice at 1440x900, but whenever I reboot (either X or full reboot) it will load up 1152x864 resolution! What's more interesting is that my welcome screen is in 1440x900!

In the Screen and Graphics area my monitor reads as PlugnPlay. If I change it to a samsung monitor, the settings get even more screwy.

I'm running 7.10 and I am a total nuub to this. I am just now learning terminal commands and how to use them. So far all I have memorized are sudo and nano! I don't know how to use special modifiers, so if I have to do anything in the terminal, please be patient with me!

I have been reading about this and have tried quite a few things but to no avail.

As is usually requested, here is my xorg: (if you happen to notice anything really wrong otherwise, please let me know!)  Thanks a bunch for any help.
:confused:
Section "Files"
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
	Identifier	"ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
	Boardname	"ati"
	Busid		"PCI:2:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1400x1050@60"	"1600x1200@65"	"1280x960@75"	"1600x1200@60"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:2:0:0"
	Driver		"fglrx"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by Scarath on 2008-01-20
Backup /etc/X11/xorg.conf then open ur terminal and do:

```
sudo nano /etc/X11/xorg.conf
```

Scroll down to the section under "Section "Screen"" and delete the resolution it keeps rebooting in and make sure the resolution you want is the first in line e.g.

```
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
Monitor "SyncMaster"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1600 1200
Modes "1400x900@60", whatever,whatever
EndSubSection
EndSection
```

then press:
ctrl + x
then y
then enter

hope it works, if it messes anything up just rename ur backed-up xorg back to xorg.conf (over writing the modded one) and u'll be set

---

### Post by spiderbatdad on 2008-01-20
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

