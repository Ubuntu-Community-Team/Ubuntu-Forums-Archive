---
title: "Voodoo 3 won't display except in 640x480"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2007-03-13
I have tried installing both Dapper and Edgy on my computer with a Voodoo3 card, and neither version will allow me to switch out of 640x480.

lspci correctly identifies my card as a Voodoo 3.

I have tried changing xorg.conf to only allow 1024x768 and 800x600 but that doesn't work.  Here are the relevant packages I have installed:

x-server-xorg-driver-voodoo
x-server-xorg-driver-tdfx
libglide3


Do I need to install any others?  Is there something I have to do to enable the drivers?

Right now I have switched the driver to vesa so that I can at least USE the machine, but I would very much like to get it working properly.

I've searched these forums but haven't found a real answer for my problem.  I've also googled without luck.  Please help!

---

### Post by Crooksey on 2007-03-13
Post your xorg.conf

---

### Post by Monsieur le Comte on 2007-03-13
My xorg.conf:
```


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
#	Driver		"tdfx"
	Driver		"vesa"
	BusID		"PCI:0:8:0"
EndSection

Section "Monitor"
	Identifier	"VG150"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"VG150"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Monsieur le Comte on 2007-03-14
Anybody have any ideas?

---

### Post by Monsieur le Comte on 2007-03-14
Ok, last bump

Or does anybody know of any distro with good support of this older card?  I've tried Fedora Core 6 and OpenSuSE 10.2 with no luck either.

---

