---
title: "Editing xorg.conf"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2008-03-27
Hi there,

After enabling nVidia's non-free drivers through the "Restricted Drivers Manager", everything booted up seemingly fine. The resolution is fine. The only problem is, the refresh rate isn't what it should be. It currently shows at 60Hz, when my monitor is capable of 75Hz.

So I took a peek at xorg.conf and saw the following.....

Section "Monitor"
Identifier "Generic Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1280x1024"
Horizsync 31.5-64.0
Vertrefresh 56.0 - 65.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
Horizsync 24kHz - 80kHz
Vertrefresh 50Hz - 75Hz
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
Gamma 1.0

Knowing full well that editing the xorg.conf file can knack everything up, I made a copy of it, and edited the refresh part to......

Horizsync 24kHz - 80kHz
Vertrefresh 50Hz - 75Hz

....which is the settings for my current Neovo F-417 LCD type monotor. I did a quick restart of the xserver, altered the screen rez to the highest it would go in "Screens and Graphics" (from 50 to 57Hz), and lo and behold, there's my 75 Hz, and all is looking peachy.

Till i reboot. On reboot it slides back to 60Hz again, and on re-examining the xorg.conf file, the refresh values has been restored to what they were originally. So something is obviously rewriting the values on reboot. Any ideas on how I can stop this from happening?

Thanks...Bob

---

### Post by Bachstelze on 2008-03-27
Please paste your entire xorg.con, between CODE tags.

---

### Post by SpongeBob SquarePants on 2008-03-27
Sure thang.....Actually, on looking at this myself (and I have no brain), it seems that the non-free driver isn't in there at all. Yet I do have it selected in the "Screen and Graphics" gui, and I am getting 3D rendering. The only thing is, using the gui won't give me a high enough refresh rate. Before I had to edit the xorg.conf for a higher refresh rate to appear in the options....then I could choose it. Is something overiding the xorg.conf?

Anyway...here it is........

```
Section "Files"
EndSection

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
	Identifier	"Generic Video Card"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
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
	Load		"v4l"
EndSection
Section "device" #     
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
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
```

---

