---
title: "graphics card issue"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Cer4 on 2008-03-12
i'm having a slight problem in that whenever i am doing something,

i get an odd flckering across the screen that looks like it code be code moving (if you get whati mean by that...  its mostly obscured by the desk top itself so its just lots of small lines moving really.

if someone could tell me all the info i would need to give for someone to figure why its doing it i'll post it,  

thankyou in advance :)

C3r4

---

### Post by InfinityCircuit on 2008-03-12
We can't really do anything without knowing what kind of graphics card you're using.  Are you using proprietary drivers?

To help, please post the contents of /etc/X11/xorg.conf and the output of "lspci -nn"

---

### Post by Cer4 on 2008-03-13
Ok, my graphics card is an nVidia NV17 [GeForce4 MX 420]  heres the contents of /etc/x11/xorg.conf,  (sorry if its a lot more than you needed...lol)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 420]"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"SAMSUNG"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 420]"
	Monitor		"SAMSUNG"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@60"	"1280x960@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
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
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1280x960@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0

and the output of "lspci -nn" is:

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] [1106:3099]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] [1106:b099]
00:06.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
00:07.0 Communication controller [0780]: Ambient Technologies Inc HaM controllerless modem [1813:4000] (rev 02)
00:08.0 Multimedia audio controller [0401]: Ensoniq 5880 AudioPCI [1274:5880] (rev 04)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233 PCI to ISA Bridge [1106:3074]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
00:11.4 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 MX 420] [10de:0172] (rev a3)

to be honest i have very little idea of what i'm doing,  but i'm learning as i go :D

thanks,

C3r4

---

### Post by OffAxis on 2008-03-13
how much memory is on your video card?
Is it an onboard video card (as in, part of the motherboard)?
Do you have compiz effects enabled?

Is this a new development?
If so, what triggered it?

---

