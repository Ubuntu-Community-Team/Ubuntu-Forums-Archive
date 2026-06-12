---
title: "Video card fun"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-08-11
I've been working on getting my system up and running with dual monitors. One monitor works nicely, but the other (on another video card) does not work at all. Here's my lspci output for the two cards:

01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GS (rev a2)
02:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Here's the relevant sections of xorg.conf
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"Second Video Card"
	Driver		"nvidia"
	Busid		"PCI:02:09.0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-204
	Vertrefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	Horizsync	28-204
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"Second Video Card"
	Monitor		"Second Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24			
		Modes		"1680x1050" 	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen	"Default Screen" 
	screen	"Second Screen" RightOf "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection


Anyway, no signal is going to the second monitor. Anybody have any ideas what's going on?

THanks,
Will

---

### Post by overdrank on 2007-08-11
Hi I have not tried this but you may look at this thread
[http://ubuntuforums.org/showthread.php?t=53966](http://ubuntuforums.org/showthread.php?t=53966)

:popcorn:

---

### Post by BobCFC on 2007-08-11
Are you using the nvidia drivers?  I have dual monitors working on a single card very well using the nvidia control panel after downloading the drivers from the nvidia web site.

then type **gksudo nvidia-settings**

As I say I only have one card, but it is listed as GPU 0 and Screen 0 etc, so I imagine it is designed to work with multiple cards.

---

### Post by gantww on 2007-08-12
I'm using Nvidia drivers, but it doesn't seem to want to pick up the other card. It's probably some little setting in the x config, but I can't seem to figure it out.

---

### Post by BobCFC on 2007-08-12
how many cards are listed when you use **gksudo nvidia-settings**?  it is supposed to do the xorg.conf file for you

EDIT:  if you still get stuck after trying the nvidia control panel there is a [Linux section]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") on the nvidia forums which is pretty busy

---

### Post by gantww on 2007-08-12
Dude, that helped. I had no idea that nvidia-settings existed.

I've got both screens running. However, the second one won't go over 1280x720. It's almost working like I want it. If I could just fix the resolution on the second screen, it would be perfect. The second screen resolution should be the same as the first (1680x1050) Here's what I have in xorg.conf:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:9:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "nvidia-auto-select +0+0; 1680x1050 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "nvidia-auto-select +0+0; 1680x1050 +0+0; 1280x1024 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by BobCFC on 2007-08-12
I know that it tries the modes from left to right until it find the first one that works

Try removing the nvidia-auto-select +0+0;

So that the first option is 1680x1050 +0+0;

---

### Post by gantww on 2007-08-14
Still no luck. It just will not go above 1280x720. I know the monitor supports 1680x1050 (that's what my other monitor is). Any thoughts?

---

