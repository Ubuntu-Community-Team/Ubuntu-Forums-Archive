---
title: "Problem with output to monitor"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-09-30
Hi,

I have a HP f2105 monitor, when I plug the monitor in before powering up my computer there is output to the monitor. However the monitor only shows about 70% of my desktop. Its like my hp monitor shows a zoomed in image of what my laptop monitor shows.

here is a copy of my xorg.conf file, perhaps there is something I can do to change the dimensions of the output to my monitor? 

thanks

xorg.conf:


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "InputDevice"
Identifier "Tablet"
Driver "fpit"
Option "Device" "/dev/ttyS0"
Option "AlwaysCore" "on"
Option "InvertY"
Option "MaximumXPosition" "12550"
Option "MaximumYPosition" "7650"
Option "MinimumXPosition" "400"
Option "MinimumYPosition" "400"
Option "SendCoreEvents"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680 x 1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680 x 1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680 x 1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680 x 1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680 x 1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"Tablet"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Yoooder on 2007-10-01
Have you tried adjusting the monitor's settings to make sure the remainder of your desktop isn't just being pushed offscreen by the monitor itself?

Also, your xorg.conf shows you only having one screen--so I presume it is attempting to clone your primary monitor to your secondary (show the same thing on both).  Does your external monitor support the resolution your primary monitor is running at?  Try changing your resolution to 1024x768 or 1280x1024--both are pretty standard and I would hope the external supports them.  Resolutions like 1680x1050 are becomming more common--but still not near as common as the otherxs.

---

