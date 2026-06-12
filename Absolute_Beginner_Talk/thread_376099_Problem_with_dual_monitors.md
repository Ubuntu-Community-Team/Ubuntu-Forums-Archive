---
title: "Problem with dual monitors"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by bob_barker on 2007-03-04
I am trying to get dual monitors working and I am having problems.  I have an Acer Aspire 56306895.  I have changed xorg.conf to include the needed information but when i restart X my external monitor is my primary monitor, I don't think it's supposed to be, maybe i'm wrong?  Also the resolution on my monitor seems to be screwed up to, the monitor Brand is Benq and it's a 15" LCD monitor.
Below is my xorg.conf, can someone tell me what is wrong with it?
[
Section "Device"
	Identifier	"Card0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option        "VBERestore" "true"
        Option        "DRI" "true"
        Option        "SWCursor" "true"
        Option        "MonitorLayout" "CRT,LFP"
        Option        "CloneRefresh" "85"
        Screen           0
EndSection

Section "Device"
	Identifier	"Card1"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option        "Display" "CRT"
        Option        "MonitorLayout" "CRT,LFP"
        Screen           1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"Monitor0"
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

Section "Screen"
	Identifier	"Screen1"
	Device		"Card1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Two Screen Layout"
    Screen  0     "Screen0" LeftOf "Screen1"
    Screen  1      "Screen1" 0 0
    Option        "Xinerama" "On"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option    "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

