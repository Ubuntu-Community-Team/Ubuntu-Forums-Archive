---
title: "HELP - Need External Projector/Monitor to work!"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by GreenMedallion on 2007-04-30
I am a part time faculty and have been struggling to use digital projection in my classes, and often opting to use one of those "other" platforms to project images via a laptop (Art History and Film Studies courses). But I really need to get this working on my Dell E1405. This is by homebase, all Ubuntu!

I have tried playing with Xinerama and can't seem to get it to work. My "test" monitor is an external LCD screen (also my HD tv). But in the classroom, I can be hooking up to any number of things - one day a screen, next day a projector. How can I get this to work reliably? Do I need to know the external monitors display size? My problem is, this changes day-to-day sometimes.

I have been playing around with this xorg setup. It is not the one that actually runs. I just backup/cut/paste/test to try and get it to work with my "test" monitor. But no luck. What am I missing?


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
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"LeftEdge"		"1700"
	Option		"RightEdge"		"5300"
	Option		"TopEdge"		"1700"
	Option		"BottomEdge"		"4200"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"0"
	Option		"MaxTapMove"		"0"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"0"
	Option		"MinSpeed"		"0.09"
	Option		"MaxSpeed"		"0.18"
	Option		"AccelFactor"		"0.0015"
	Option		"SHMConfig"		"on"
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
	Identifier	"Internal"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"External"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Internal Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Internal"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection


Section "Screen"
	Identifier	"External Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"External"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
		EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Internal Screen"
	Screen		1 "External Screen" RightOf "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection



Hey thanks Ubuntu community! I rarely need to post any questions, because people are so helpful out there all the time. Feisty is great, good job everyone who bult it!

---

### Post by sviglas on 2007-04-30
Try adding the following lines under the "Monitor" section of your xorg.conf file:

Option  "MonitorLayout"  "CRT,LFP"
Option  "Clone"  "true"

and then restart your Xserver.  That usually does the trick for me.  (You're basically cloning your laptop's output so when you hook it up to a projector you'll get the same output on both screens).

Hope it helps.

---

### Post by annda on 2007-04-30
you can try to see if xorg-edit works for you:
[http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)

i haven't tested it yet because the nvidia settings utility works great for me.

and here are download details:
[http://www.geole.info/Deb-Packages-for-Ubuntu-Feisty.90.0.html?&l=1](http://www.geole.info/Deb-Packages-for-Ubuntu-Feisty.90.0.html?&l=1)

---

### Post by GreenMedallion on 2007-04-30
sviglas - thanks for the tips. i just tried this out, and now it works perfectly. i can even 'plug and play' with my external LCD. i'll try it on campus with a projector later this week. but should work the same. there is a sizing discrepency when i 'plug and play' and don't restart, but i'll get over that, or just restart as the case may be. anyhow, thanks for the esay solution.

---

### Post by SendDerek on 2007-05-05
I just wanted to thank you guys for sharing your tips.

By using

Option "MonitorLayout" "CRT,LFP"
Option "Clone" "true"

I was able to get my external montior to show up.  However, after a long time searching, I wasn't able to figure out how to change the resolution on it (1024x786) to differ from the resolution on my laptop (1280 x 800).

Is there anyway you guys can help out with this?

Here is my xorg.conf file:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
        Option "MonitorLayout" "CRT,LFP"  #ADDED
        Option "Clone" "true"             #ADDED
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

