---
title: "Enabling direct rendering"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Baen on 2007-12-14
I can't figure out how to enable direct rendering with my Intel Mobile 915GM/GMS/910GML Express Graphics Controller, and I keep getting an error message saying I need to have it enabled to install the latest 915 driver (currently using i810 driver). Any suggestions? 

xorg.conf, if that helps:

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Boardname	"Intel 915"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
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
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" 
	Identifier	"device1"
	Boardname	"Intel 915"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
	Option		"DRI"
EndSection
Section "screen"  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	16
	Monitor		"monitor1"
EndSection
Section "monitor" #
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "DRI"
Mode 0666
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by overdrank on 2007-12-15
HI and I am assuming you are using gutsy? And just another thought have you tried changing your default depth to 24 instead of 16 ( in your xorg)?  Also how much memory does the system have?

---

### Post by zcal on 2007-12-15
Try adding the line

Option       "DRI" "true"

under the "Device" section in xorg.conf.

Otherwise, these wikis might help you out.
[http://gentoo-wiki.com/HOWTO_setup_HP_NX_6110#cat_.2Fetc.2FX11.2Fxorg.conf]("http://gentoo-wiki.com/HOWTO_setup_HP_NX_6110#cat_.2Fetc.2FX11.2Fxorg.conf")
[http://gentoo-wiki.com/HOWTO_Direct_rendering_on_Intel_Extreme_Graphics_(855GM)_chipsets]("http://gentoo-wiki.com/HOWTO_Direct_rendering_on_Intel_Extreme_Graphics_(855GM)_chipsets")
(obviously, emerge commands are Gentoo-specific)

---

