---
title: "Finally ATI X1600 working with Compiz"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by seijling on 2008-03-05
Got it working - no need to blather on about it.

I just wanna let others know.  It can be annoying finding the right combo of drivers, settings and configs to make it all work - why squander it by not sharing? besides, there is little or no conclusive work outlining this hardware set.

So the specs of the situation:

Computer: ACER 8204WLMi 
GPU: ATI X1600 (Mobility Radeon)
Video Ram: 256 Mb
CPU: Intel T2500 (2.0 GHz - Yonah)
RAM: 2 GB 667 MHz bus
Resolution: 1680x1050

OS: Ubuntu 7.10


Please note: before using/reading any of the information I have posted here, be aware that the method I have employed is in no way the "right" way to do it - just the way I have done it.  I am sorta new to *nix.

Anyhoo, the steps I (roughly) took to generate a completely working compiz xserver:

1.) install a fresh copy of 7.10
2.) select a few updates and install
3.) Install restricted drivers (ATI was restricted in my case)
4.) With synaptic, select "xserver-xgl' and "compizconfig-settings-manager"
5.) modify xorg.conf to look something like: (taking note of the "composite" section at the bottom)


```
# xorg.conf (xorg X Window System server configuration file)
#

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
	Identifier	"ATI Mobility Radeon X1600"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Mobility Radeon X1600"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
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
	Option		"Composite"	"1"
EndSection
```


5.) reboot!
6.) select the right appearance setting i.e. "System Preferences"--> "Appearance"--> "visual Effects"

To be honest, I shut my computer down the night before after making a few changes to xorg. In frustration thought sarcastically, "Yeah right! That'll work!" and to my surprise it did.  Ask me to explain it and I'll tell you the universal cosmic rays had aligned in such a way to make me type the correct xorg.

I hope that it can be of help to other noobs out there.

BTW: I am acknowledging this thread and its author- I think made all of the difference: [http://ubuntuforums.org/archive/index.php/t-575215.html](http://ubuntuforums.org/archive/index.php/t-575215.html)

Mike k

---

### Post by philosophicscience on 2008-03-05
I have been struggling all day with the same graphics card on my acer asipre. I wish I had some idea of how to replicate your findings. Sadly most of this is greek to me :(

---

### Post by seijling on 2008-03-09
Anything can be hard when you start out.  To be honest I myself am very green to this stuff.  But if its any consolation, taking minute steps to obtain a goal was the only "brains" I employed. I failed a lot, reinstalled a lot but ultimately got it going.  

Message back, I am familiar with Acer's "quirks" - maybe I can guid you more directly?

Mike

---

### Post by sayhar on 2008-03-09
this is awesome! Thank you so much.

---

### Post by seijling on 2008-03-10
Just a heads up - tried to get rid of the jaggies (anti aliasing) by enabling fsaa (full screen anti aliasing)


```
aticonfig --fsaa=on
```

and yikes was that messy.  Not only did it core dump, it re-wrote xorg to complete suckitude.

Anyhoo, I don't think I'll try that one again until I read more.

BTW: At least it backed up the old xorg thankfully


Mike

---

### Post by forrestcupp on 2008-03-10
Congrats.

When Hardy comes out it will be even easier.  The ATI drivers that will be in Hardy's Restricted Drivers Manager don't need Xgl.

---

### Post by seijling on 2008-03-10
> **forrestcupp said:**
> Congrats.

When Hardy comes out it will be even easier.  The ATI drivers that will be in Hardy's Restricted Drivers Manager don't need Xgl.

No xgl? Hmpf. 

Must be hamsters and duct tape then.  :)

Seriously, how will Hardy negotiate 3D then?  Furthermore, why change a good thing (or am I crazy to think that)

Mike

---

