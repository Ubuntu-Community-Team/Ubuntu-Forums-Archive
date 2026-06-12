---
title: "Driven back to XP - what resets xorg?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by YoYoSan on 2007-10-25
I've really enjoyed the speed and sense of security that ubuntu has given me over the last few months, but for the last 3 days I've been using XP.

Having just upgraded from my happy 7.04 state - Why the b****dy h**l do I have to reset the screen res every time I log on - if only this wasn't a mission away from mass conformity (did any one else see the interview that put the number of ie users for iPlayer at +600, 000 and the number using linux at 400-600?).

Any how this is my XOrg Config (oh,and why when I run" sudo gedit /etc/X11/xorg.conf" does it sometimes show detailed modeline info and sometime just the stuff below?!)

- any help gratefully received!

by-the-by I want to achieve a 1280x768@60 regularly and then get my systems to recognise my 19" desk monitor when I plug it in.

Cheers


Section "File
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
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
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
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
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by SunnyRabbiera on 2007-10-25
did you copy the xorg configuration from a live CD?
I have found this works.

---

### Post by bodhi.zazen on 2007-10-25
We need more information to help. 

Videocard ? driver ? monitor ?

How are your configuring your resolution ?

---

### Post by YoYoSan on 2007-10-25
Gutsy updgrade from feisty - the Xorg config I've posted above is from my live system.

My concern is that I don't understand, nor can I control what is continually resetting my screen res to the the wrong res. on reboot.

 Having fiddled for a three days I've managed to get 1280x768 onto my screen & graphics option but I  can't fix it as I could using the updated intel driver added to feisty.

They do say that it's the things you don't feel in control of that create the greatest stress!

---

### Post by YoYoSan on 2007-10-25
Thanks for the replies guys

This is a Samsung Q30 laptop , Intel 915gm driver, screen is standard 1280x768

I've tried resetting using the sudo dpkg-reconfigure xserver-xorg and edited the res to include 1280x768. Then rebooted and used the screens & graphics option to choose the correct res.

---

### Post by ed-koala on 2007-10-25
I notice your xorg file only shows one resolution setting - 640x480.
My xorg files shows this for modes:

Modes		"1024x768"	"800x600"	"720x400"	"640x480"

I actually had to edit my xorg file to add the 1024x768 before that option would appear in my screen resolution settings.  This may be why you have to reset your resolution on reboot, your xorg says 640x480 is the only option.  Back up your file and try editing the file, then go to System - Preferences - Screen Resolution and change to the desired setting.  That should fix the reboot problem ... I think lol.  Hope it helps.

---

### Post by YoYoSan on 2007-10-25
Hmmm - some more xorg editing then.

I'll have a fiddle - the confusing thing is that sometimes when I run "sudo gedit /etc/X11/xorg.conf"

I get a number of alternative modelines listed, and thten, as with this post I get a very limited amount of information.

I enjoy a challenge - I just like it to be a predictable one!

Hey ho!

---

