---
title: "[SOLVED] Help! I'm stuck in 640x480 and none of the threads on this helped"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-31
All right, I have a Toshiba Satellite A105, with a an Intel 945 graphics card. My standard res is 1280x800. I also have a external monitor that I switch to, to watch movies which is set at 1152x864. It used to run in 1280x800, but for some reason it no longer supports that res.
 I've had gutsy running just fine for a couple weeks now, but last night I switched the output to the external monitor using the commands:

xrandr --output VGA --mode 1152x864
xrandr --output LVDS --off

Like I always do when I want to watch a movie, no problems... then I double-clicked the video file, and my monitor flickered, turned off, and then turned back on in 640x480. 
I tried running xrnadr on the external and laptop monitors, but it just came back at 640x480
I tried reconfiguring my xorg.conf, but it did no good.
I copied my xorg.conf_backup over my xorg.conf, and when it booted up, the login screen was set to the proper resolution, but as soon as it loaded gnome... it was back in 640x480.

I'm losing my mind here... I found 5 or 6 threads dealing with people being stuck in this resolution, but they were all fixed by things I've already tried, that didn't work.
except this 855 resolution thing, I just found... It would seem though, that if it was working fine before and this is a fix for people having this issue from the get-go... I dunno I can't fathom why my driver would suddenly decide to not work...

---

### Post by Jeezus on 2008-01-31
I thought it might be a good idea to post my xorg.conf:

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
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
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

---

### Post by zvacet on 2008-01-31
Did you try with [this](https://help.ubuntu.com/community/FixVideoResolutionHowto)?

---

### Post by Jeezus on 2008-01-31
No, I haven't... Looks promising, but I don't know how to find the vertical sync, and horizontal refresh rates for my display. I can't auto-detect them, and all I know about the monitor is this WXGA TFT Active Matrix, which hasn't helped me in finding the information I need. :p

---

### Post by Jeezus on 2008-01-31
I called Toshiba, and they are telling me that there is a fixed refresh rate of 75hz and that is the only number I can get from them they tell me there is no horizontal sync rate... ?!
that doesn't make much sense to me... can anyone help with this?

---

### Post by Jeezus on 2008-01-31
well, I managed to fix it... somehow... I ran the xorg reconfigure dealy again, and I guess by choosing a resolution that refreshed at 75hz, caused it to work properly... even though the screen settings still lists it as operating at 60hz... but whatever, it works now, and I am releived.
Thanks Zvacet!

---

