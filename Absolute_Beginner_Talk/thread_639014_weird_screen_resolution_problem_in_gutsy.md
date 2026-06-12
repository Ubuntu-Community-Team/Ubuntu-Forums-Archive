---
title: "weird screen resolution problem in gutsy"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by wherethebibawi on 2007-12-12
The problem I have is that I can't get a resolution of 1680x1050. The first time I booted I could set that resolution and it worked fine. However after I set the effects to high and rebooted I got a 1024x768 resolution.
I read through some of the posted problems and I ran

sudo dpkg-reconfigure xserver-xorg

and it was available, but in the GUI 1680x1050 isnt available.
I checked my xorg.conf file and it lists all the resolution i specified in the reconfigure. The strange thing is the resolutions in xorg.conf arent all available in the GUI.

I get a higher resolution of 1600x1200 but not 1680x1050 it is so weird.

Why is it so?

---

### Post by nikoPSK on 2007-12-12
add -phigh to your command.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Might possibly make a difference. Also you have looked in screen resolution and can't find your resolution...

---

### Post by Nano Geek on 2007-12-13
Could you post your xorg.conf here please?

---

### Post by wherethebibawi on 2007-12-13
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
	Identifier	"ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Monitor		"Acer AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1440x900" "1280x960" "1280x768" "1200x800" "800x600" "640x480"
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

### Post by wherethebibawi on 2007-12-13
I have decided to reinstall because of other problems as well. Thanx for your trouble...

---

### Post by CatKiller on 2007-12-13
Change this bit:

> **wherethebibawi said:**
> 
Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection


to this:

> Section "Monitor"
     Identifier     "Acer AL2216W"
     Option     "DPMS"
     HorizSync     30-90
**     VertRefresh     56-76**
EndSection

---

### Post by wherethebibawi on 2007-12-13
Thanks for the help, but the reinstall restored my graphics. It all works now, it must have been something strange with the previous install. I think it will be OK now...

Thanks again.

---

### Post by Nano Geek on 2007-12-13
Sorry I didn't get back to you earlier, I have been out nearly all day. 
I'm glad you got it working.

---

### Post by nikoPSK on 2007-12-13
please mark this thread as "SOLVED". :)

---

