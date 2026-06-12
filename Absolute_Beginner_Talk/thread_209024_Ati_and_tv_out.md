---
title: "Ati and tv out"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by gote on 2006-07-04
Hi fellow ubuntu users !

I have just upgraded from windows to ubuntu but i cant get my ATi Radeon 9600's TV-out port to work like it does on windows. I've installed the fglrx drivers but i still dont got a clue of how i can get it working so i hope that someone of u guys can help me out.

Regards

---

### Post by wombat20 on 2006-07-04
You could try the official proprietary ATI Linux drivers:
[http://www.ati.com/products/catalyst/linux.html](http://www.ati.com/products/catalyst/linux.html)

They installed and seem to work fine for me, but I've not tried the TV out.

---

### Post by toorima on 2006-07-04
No need for the official proprietary ATI Linux drivers, the ones from repos works fine. All you have to modify your /etc/X11/xorg.conf 
Here is the lower part of mine so you see what you need to change, my dell inspiron 8600 with a ATi Radeon 9600 works perfect with this.
Remember that you must boot with the tv plugged in for it to work.

```

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Screen		0
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section	"Device"
	Identifier	"ATI tvout"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"TVOutFormat"	"COMPOSITE" #COMPOSITE SVIDEO RGB
	Option		"TVStandard"	"NTSC-M"
	Option		"ConnectedMonitor"	"TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"HorizSync"	"30-50"
	Option		"VertRefresh"	"50"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section	"Screen"
	Identifier	"Screen1"
	Device		"ATI tvout"
	Monitor		"TV"
	DefaultDepth	24
	SubSection	"Dsiplay"
	Depth		24
	Modes		"640x480"
#	Modes		"800x600"
EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen0"
	Screen 1	"Screen1" rightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Tristan9669 on 2006-07-08
> **toorima said:**
> No need for the official proprietary ATI Linux drivers, the ones from repos works fine. All you have to modify your /etc/X11/xorg.conf 
Here is the lower part of mine so you see what you need to change, my dell inspiron 8600 with a ATi Radeon 9600 works perfect with this.
Remember that you must boot with the tv plugged in for it to work.

```

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Screen		0
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section	"Device"
	Identifier	"ATI tvout"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"TVOutFormat"	"COMPOSITE" #COMPOSITE SVIDEO RGB
	Option		"TVStandard"	"NTSC-M"
	Option		"ConnectedMonitor"	"TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"HorizSync"	"30-50"
	Option		"VertRefresh"	"50"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section	"Screen"
	Identifier	"Screen1"
	Device		"ATI tvout"
	Monitor		"TV"
	DefaultDepth	24
	SubSection	"Dsiplay"
	Depth		24
	Modes		"640x480"
#	Modes		"800x600"
EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen0"
	Screen 1	"Screen1" rightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
I used your etc/X11/xorg.conf in reference to edit mine and now my tv-out is working fine but my now my monitor is messed up. Its too bright and the color is faded, I bearly can see text or anything at all, what is causing this problem. I took a screenshot and when I view with the tv the color and brightness is fine so there is some problem with the monitor's display, maybe the drivers? Here is my etc/X11/xorg.conf 
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Screen		0
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section	"Device"
	Identifier	"ATI tvout"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"TVOutFormat"	"COMPOSITE" #COMPOSITE SVIDEO RGB
	Option		"TVStandard"	"NTSC-M"
	Option		"ConnectedMonitor"	"TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"HorizSync"	"30-50"
	Option		"VertRefresh"	"50"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section	"Screen"
	Identifier	"Screen1"
	Device		"ATI tvout"
	Monitor		"TV"
	DefaultDepth	24
	SubSection	"Dsiplay"
	Depth		24
	Modes		"640x480"
#	Modes		"800x600"
EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen0"
	Screen 1	"Screen1" rightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by FrancoNero on 2006-07-08
> **Tristan9669 said:**
> I used your etc/X11/xorg.conf in reference to edit mine and now my tv-out is working fine but my now my monitor is messed up. Its too bright and the color is faded, I bearly can see text or anything at all, what is causing this problem. I took a screenshot and when I view with the tv the color and brightness is fine so there is some problem with the monitor's display, maybe the drivers? Here is my etc/X11/xorg.conf 
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Screen		0
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section	"Device"
	Identifier	"ATI tvout"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"TVOutFormat"	"COMPOSITE" #COMPOSITE SVIDEO RGB
	Option		"TVStandard"	"NTSC-M"
	Option		"ConnectedMonitor"	"TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"HorizSync"	"30-50"
	Option		"VertRefresh"	"50"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section	"Screen"
	Identifier	"Screen1"
	Device		"ATI tvout"
	Monitor		"TV"
	DefaultDepth	24
	SubSection	"Dsiplay"
	Depth		24
	Modes		"640x480"
#	Modes		"800x600"
EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen0"
	Screen 1	"Screen1" rightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

for THAT, there REALLY sould be GUI. I mean... really ;-) anyone working on this? would be another "switch to ubuntu" argument, to have tv-out working with just a few clicks of the mouse!

---

### Post by Tristan9669 on 2006-07-08
yeah i know, there should be one

---

### Post by Dr.Thompson on 2006-11-29
I just get "command not found"....

---

