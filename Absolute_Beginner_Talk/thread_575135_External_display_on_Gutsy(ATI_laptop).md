---
title: "External display on Gutsy(ATI laptop)"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Hakujin on 2007-10-13
I have a HP laptop and am using an external LCD that is connected via a docking station. My goal is to have the external display used when the laptop is docked, and the internal display when undocked. (rebooting or killing the x server between docks/undocks is fine)

I'm running the Gutsy RC, have an ATI graphics card with the fglrx drivers installed and working, and am enjoying the hell out of compiz. Laptop LCD's native resolution is 1680x1050, external LCD is 1280x1024.

Other points of interest: currently the external LCD works, but it is a clone of the internal LCD. Higher resolution and all. (ATI has some scaling software that lets me mouse around to change the viewing area) The FN+F4 key combo that switches between attached displays does not seem to do anything.

Any help is appreciated. This is the only "issue" I've found with Gutsy so far. Everything else works wonderfully. Thanks in advance.

X.org config:
```
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
	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
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
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by Hakujin on 2007-10-13
I apologize, changing the screen resolution with the laptop lid closed worked perfectly. Problem solved.

---

