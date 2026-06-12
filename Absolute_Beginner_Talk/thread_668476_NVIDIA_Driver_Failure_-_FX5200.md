---
title: "NVIDIA Driver Failure - FX5200"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by zds on 2008-01-15
I'm tearing my hair out trying to get an add-on nvidia FX5200 (tv-out over svideo) working in ubuntu 7.10. I've used envy, mucked with xorg.conf, and tried every solution posted on this forum, over the past 5 hours.

I can't get past either using the vesa driver in low-res mode (what the hell), or using any nvidia driver and getting black and white picture with some sort of dot / line interference / distortion all over the screen.

Can anyone explain how to make this allegedly supported card actually work? Please?!

Thanks

---

### Post by zds on 2008-01-15
Anyone? Someone must know the answer since plenty of people have gotten this card working.

Here's a picture of the problem:

[IMG]http://img165.imageshack.us/img165/5531/img1531gy0.jpg[/IMG]

---

### Post by zds on 2008-01-15
And while I'm at it... the startup and shutdown splash screens look great (in full color), and the "Ubuntu is operating in low-graphics mode" screen looks fine too (but still b&W)

---

### Post by zds on 2008-01-15
Fixed by following the instructions here: [http://wiki.archlinux.org/index.php/Nvidia_TV-out_and_Video_Tearing](http://wiki.archlinux.org/index.php/Nvidia_TV-out_and_Video_Tearing)

Specifically, editing the card to get the tv-out settings:

Section "Device"
    Identifier   "Card0"
    Driver       "nvidia"
    VendorName   "ALL"
    BoardName    "ALL"
    Option       "TwinView"
    Option       "TwinViewOrientation" "Clone"
    Option       "MetaModes"           "CRT-0: 1024x768,  TV-0: 1024x768"
    Option       "HorizSync"           "CRT-0: 30-81;  TV-0: 30-50"
    Option       "VertRefresh"         "CRT-0: 56-76;  TV-0: 60"
    Option       "ConnectedMonitor"    "CRT-0, TV-0"
    Option       "TVStandard"          "PAL-B"
    Option       "TVOutFormat"         "SVIDEO" 
EndSection

---

### Post by NT4usB on 2008-01-15
Post your xorg.conf.
Are you using svideo to TV as your **only** monitor?
What other displays are connected? via DVI, VGA, what?
When you ran Envy, did you first choose the uninstall driver option... to clean up all your other attempts, then install?
What does enabling the restricted drivers manager get you?
Did you try:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then restart gdm...

---

### Post by zds on 2008-01-15
Yes, the tv is the only monitor. The problem was that Envy, the restricted drivers, other techniques, etc was never setting up the different outputs (tv and crt).

Here's my xorg.conf

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
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
        Option "TwinView"
	Option "TwinViewOrientation" "Clone"
	Option "MetaModes"           "CRT-0: 1024x768,  TV-0: 1024x768"
	Option "HorizSync"           "CRT-0: 30-81;  TV-0: 30-50"
	Option "VertRefresh"         "CRT-0: 56-76;  TV-0: 60"
	Option "ConnectedMonitor"    "CRT-0, TV-0"
	Option "TVStandard"          "NTSC-M"
	Option "TVOutFormat"         "SVIDEO" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
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
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@60"	"1280x960@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
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
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #    
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
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

