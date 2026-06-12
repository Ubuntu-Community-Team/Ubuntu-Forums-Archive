---
title: "Videos run extremely slow or not at all"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by DanielJackins on 2008-01-07
Whenever I attempt to look at videos on the internet (i.e youtube) it will either not work or go slow to the point of not being able to watch it. I don't know about videos on my computer itself as I haven't tried yet, but this only started occurring upon my switch to Linux. Any help would be appreciated :)

---

### Post by PetePete on 2008-01-07
try with vids on your computer
it could be the wrong video driver set, please post the contents of /etc/X11/xorg.conf and let us know what video card you got

---

### Post by DanielJackins on 2008-01-07
> **PetePete said:**
> try with vids on your computer
it could be the wrong video driver set, please post the contents of /etc/X11/xorg.conf and let us know what video card you got

The contents of what? 

I don't currently have any videos on my computer, but once I get back from work I'll try one out.  My graphics card is an NVIDIA GeForce 6150 SE, but I'm not sure if thats the same thing as a video card?

---

### Post by DanielJackins on 2008-01-09
Okay, so videos do run okay on the computer, just not the internet.

Another problem I also just found is that I attempted to play a burnt home-video DVD and it wouldn't play.

Thanks for any help

Oh and here is the readout you asked for:

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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
	Driver		"nvidia"
	BusID		"PCI:0:13:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

