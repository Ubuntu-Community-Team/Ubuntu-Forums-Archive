---
title: "ATI Radeon 9600 issue"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-05-25
Hello all,
I'm trying to get my desktop working with a dual screen setup with an ATI Radeon 9600 All-in-Wonder. I've altered the xorg.conf as follows in a moment, but can't change resolution because "The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available.". Also, I can't figure out how to get the second screen to act as a desktop extension instead of simply mirroring the first. Here's the relevant bits of my config - any ideas?

Section "Device"
Identifier "ATI Technologies Inc RV350 AP [Radeon 9600]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Main Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Monitor"
Identifier "Second Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Main Screen"
Device "ATI Technologies Inc RV350 AP [Radeon 9600]"
Monitor "Main Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Second Screen"
Device "ATI Technologies Inc RV350 AP [Radeon 9600]"
Monitor "Second Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection


Section "ServerLayout"
Identifier "Default Layout"
Screen "Main Screen"
Screen "Second Screen" RightOf "MainScreen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "ServerFlags"
Option "Xinerama" "true"
EndSection

---

### Post by dstew on 2007-05-25
You need to install the xorg-driver-fglrx package using Synaptic. Then, change the driver in your Device section from "ati" to "fglrx".

---

### Post by gantww on 2007-05-25
I switched it over, but it still doesn't seem to be working. I also still can't change resolution. Any ideas?

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Main Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Second Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Main Screen"
  screen "Second Screen" rightof "MainScreen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by gantww on 2007-05-25
I cut out the following:

Section "ServerFlags"
	Option	    "Xinerama" "true"
EndSection

Now I can change resolution, but I still can't figure out how to get two screens. Does that help?

---

### Post by dstew on 2007-05-26
I lack personal experience with dual ATI monitors, but I found a thread that seemed to have some good information: [http://ubuntuforums.org/showthread.php?t=85215](http://ubuntuforums.org/showthread.php?t=85215)

I think you have to be sure all the driver components are installed, and use the **aticonfig** program. Here is a command that worked for one poster:```
sudo aticonfig --dtop=horizontal -f --mode2=1600x1200,1280x1024,1152x864,1024x768,800x60 0
```

---

### Post by gantww on 2007-05-26
That worked. Thanks a bunch!

---

