---
title: "very slow typing, strange refresh rates"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by K_Boomer on 2008-01-12
AS i type this i cannot see the words until about 20 seconds later. the problem started after i got the driver for my ATI radeon 9550 card. it was a pain to get without it screwing up my resolution and making it 800x600. Still i have lots of problems, namely that the refresh rates make everything jittery. For example, when i try to play nexuiz, the mouse jumps around instead of fluidly moving. Same with the side scroll bar. everything is jittery.

Here is my /etc/X11/xorg.conf:
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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"UseFBDev"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"19''"
	Option		"DPMS"
	Horizsync	31-101
	Vertrefresh	60-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"19''"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
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
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Disable"
	Option		"Composite"	"0"
EndSection



And here is my compiz, if that helps:

compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


woah, now my typing is fluid all of a sudden, but the scroll bar is still sluggish and nexuiz is running sluggishly. But if any1 can help by checking my xorg.conf and my compiz and tell me what i can do to smoothen my experience with linux, it would be greatly appreciated.

---

### Post by nikoPSK on 2008-01-12
Nexuiz! yay! Well, reconfigure your xorg file as so:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

