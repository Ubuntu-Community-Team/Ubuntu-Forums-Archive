---
title: "beryl on powerbook 1.67"
date: 2006-12-24
forum: Apple PPC Users
---

### Post by atomik on 2006-12-24
I'm trying to enable beryl with AIGLX on my powerbook 15 inch 1.67 Ghz..

I'm follow three or four guide, but result is the same screen become black and white...

This is my xorg.conf:

> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
Identifier "Apple Touchpad"
Driver "synaptics"
Option "CorePointer"
Option "SendCoreEvents" "true"
Option "Device"
Option "Protocol"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
Option "MinSpeed" "0.30"
Option "MaxSpeed" "1.10"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "FastTaps" "1"
Option "MaxTapTime" "0"
Option "AccelFactor" "0.030"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "CircularScrolling" "1"
Option "CircScrollTrigger" "0"
Option "FingerLow" "1"
Option "FingerHigh" "3"
Option "LeftEdge" "80"
Option "TopEdge" "80"
Option "RightEdge" "850"
Option "BottomEdge" "560"
Option "TapButton1" "1"
Option "LTCornerButton" "3"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
	Option 		"AGPMode" 		"4"
	#Option 	"ColorTiling" 		"on"
	Option 		"EnablePageFlip" 	"true"
	Option 		"LVDSProbePLL" 		"true"
	#Option 	"AccelMethod" 		"EXA"
	#Option 	"RenderAccel" 		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	#DisplaySize	338	225	# 1280x854 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x854"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Apple Touchpad"
	Option 		"AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "true"
EndSection



With glxgear -printfps i get only 39 FPS:

> atomik@moon:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File r300_maos.c function r300EmitArrays line 546
Cannot handle offset 80302000 with stride 3, comp 3
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
197 frames in 5.0 seconds = 39.361 FPS



Help me please

---

### Post by fuoco on 2006-12-27
it's probably related to our problem/bug. Join us at: [http://www.ubuntuforums.org/showthread.php?t=320649&page=3](http://www.ubuntuforums.org/showthread.php?t=320649&page=3)

---

### Post by atomik on 2006-12-27
Thanks for the reply!

---

