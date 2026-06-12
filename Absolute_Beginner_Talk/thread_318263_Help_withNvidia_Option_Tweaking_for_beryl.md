---
title: "Help withNvidia Option Tweaking for beryl"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Abu Imak on 2006-12-13
Hi, I've switched to Ubuntu about 2 months ago and I'm still new to a lot of things, but one thing I particularly love is Beryl. I'm intriguing my friends with it and trying to get them to switch as well. I have a simple subjective question.

I've seen in various forum posts numerous people have certain options on. I've turned on some of these options myself and noticed an increase in the performance of beryl. I was wondering if anyone could give me some good ideas about what to enable and what not to enable because I feel that my "shotgun" approach isn't the best.  I have a Dell Inspiron 8600 with a Nvidia go5200 and 512MB of ram. Tell me what you think about my xorg.conf and what options do you think i should enable/disable. Thank You.

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option         "backingstore" "true"
        Option         "RenderAccel" "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "TripleBuffer" "true"
        Option          "AddARGBGLXVisuals" "true"
        #Option "NvAGP" "true"
        Option "VBERestore" "true"
        EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
        DefaultDepth     24
        Option           "twinview" 
        Option           "TripleBuffer" "true"
        Option           "AllowGLXWithComposite" "true"
        Option           "RenderAccel" "true"
        Option           "AddARGBGLXVisuals" "true"
        SubSection   "Display"
        Depth 1
        Modes "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
        Depth 4
        Modes "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
        Depth 8
        Modes "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
        Depth 15
        Modes "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
        Depth 16
        Modes "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
        Depth 24
        Modes "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
        Option   "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
Option "Composite" "Enable"
EndSection

---

