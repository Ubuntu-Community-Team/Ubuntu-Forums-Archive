---
title: "Ubuntu 6.10 &amp; ATI Dual Screen issue"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by ids777 on 2006-11-13
Arrrgh!!

Just installed Ubuntu for the first time & I've trying for day's to get my ATI Radeon 9800 to dual screen.  The closest i've is at logon it's is a dual screen - as soon as i've logged on thou it switches to a clone again....
Please help...
 Copy of xorg.conf
[COLOR="DeepSkyBlue"]Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
Driver "fglrx"
BusID "PCI:1:0:0"
Option "UseInternalAGPGART" "no"
Option "no_accel" "no"
Option "no_dri" "no"
Option "mtrr" "off"
Option "DesktopSetup" "0x00000200"
Option "MonitorLayout" "AUTO, AUTO"
Option "IgnoreEDID" "off"
Option "NoTV" "yes"
Option "TVStandard" "PAL-B"
Option "TVHSizeAdj" "0"
Option "BlockSignalsOnLock" "on"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Screen 0
EndSection

Section "Monitor"
	Identifier	"ULTRASCANP99"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"ULTRASCANP99"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "false"
EndSection
[/COLOR]

---

