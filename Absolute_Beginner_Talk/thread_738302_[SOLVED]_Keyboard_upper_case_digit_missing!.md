---
title: "[SOLVED] Keyboard upper case digit missing!"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-03-28
I'm feeling a little confused!  I seem to remember that within the past 7 days I have set my keyboard at 104 (or 105) digits, or whatever the term is, which is what it was with XP (I don't dual boot).  Around the same time - it _may_ just be a coincidence - i have been unable to access the pound sign (above the "3") at all.  Both shift keys are working as I get other "shift" digits.  I've taken the key off and cleaned it, but being a laptop, there's not a lot to clean.  Any ideas?  Software or hardware problem?  Regards.

---

### Post by LowSky on 2008-03-28
the british pound sign (£) or the american pound sign(#)?
could you post your xorg file ```
gedit /etc/X11/xorg.conf
```

---

### Post by Berean on 2008-03-28
Thanks: is this the readout you wanted?

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uK"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor Laptop"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)]"
	Monitor		"Generic Monitor Laptop"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

I'm hoping it's the pound sign and not the dollar sign.  I'm in the UK.  Regards

---

### Post by Berean on 2008-03-29
bump

---

### Post by dnairb on 2008-03-29
I may be wrong, but I believe that the first section is wrong:

```
Option "XkbLayout" **"uK"**
```

is

```
Option "XkbLayout" **"gb"**
```

on my system with a 105-key keyboard.

You could try editing the file, restarting and testing.

---

### Post by Berean on 2008-03-29
dnairb,

You're a star!  Many thanks, indeed.  Regards.

---

