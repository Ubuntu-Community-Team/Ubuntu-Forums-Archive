---
title: "Youtube Fullscreen &amp; Dual Monitors"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-07
i have a g-force FX 5500 and it has 2 monitor "ports" on it, i have a monitor on each one and it works great except when i go to youtube and hit full screen it goes on the left monitor, i want it on the right so i can watch it in bed... anyone else have this problem or know how to fix it?

thanks in advance...

---

### Post by msmyk2 on 2008-03-09
Hello, I have exactly the same problem. I have ATI Radeon x800, the browser is Firefox. I've already tried removing adobe plugin nonfree and use gnash instead, but it brings awkward results. 

I am quite sure this has something to do with the graphics and monitor settings, but this also might be something going on between the ATi driver and mozilla Flash plugin.

I already searched wherever I could, I also raised this question on Polish forum, but received no answer. It is quite important to me, because my left monitor is smaller & with lower res (1024x768). I can't see the whole video area, as it opens with the bigger screen resolution (1280x1024).

In case you need it, here's my xorg.conf:




```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "pl"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "Failsafe Monitor"
	VendorName   "Plug 'n' Play"
	ModelName    "Plug 'n' Play"
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
EndSection

Section "Monitor"

	# 
	Identifier   "monitor1"
	Gamma        1
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Failsafe Device"
	Driver      "fglrx"
	BoardName   "vesa"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1024x768+1024x768,1280x1024+1280x1024,1280x1024+1024x768"
	Option	    "OverlayOnCRTC2" "0"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"

	# 
	Identifier  "device1"
	Driver      "fglrx"
	BoardName   "vesa"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal,reverse"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OverlayOnCRT2" "true"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "HSync2" "30-82" #This sets the horizontal sync for the secondary display. 
	Option	    "VRefresh2" "56-76" #This sets the refresh rate of the secondary display.
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Mode2" "1280x1024"
	Option	    "MonitorLayout" "CRT,CRT"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Failsafe Device"
	Monitor    "Failsafe Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1280 1024
		Depth     24
		Modes    "800x600@72" "800x600@75" "800x600@56" "800x600@60" "640x480@75" "832x624@75" "640x480@72" "1024x768@75" "640x480@60" "1024x768@70" "1024x768@60" "1280x960@60"
	EndSubSection
EndSection

Section "Screen"

	# 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

---

### Post by The Titan on 2008-03-09
i have an nvidia card so i doubt that its gonna be a problem with your card. its probably something stupid or therse nothing we can do....

---

### Post by herbster on 2008-03-09
I use dual monitors on an Nvidia card and though I've never watched a Youtube video in fullscreen mode (goodness gracious the horrid quality) you can just hit ALT+drag the window to the other monitor.

---

### Post by Gepetto on 2008-03-09
Are you using xinerama? If so, make sure your firefox window is maximized in the monitor you want the youtube video in.

---

### Post by msmyk2 on 2008-03-10
> Are you using xinerama?

If xinerama = big desktop (= in newbie language "you can move windows between screens"), then yes. 
:P

I'll check this hint asap ;)

Cheers

---

### Post by msmyk2 on 2008-03-10
Gepetto: the maximized Firefox window didn't help. Youtube's full screen still appears on the leftmost monitor. 

herbster - how do you alt+ drag? I tried clicking with the mouse cursor over the left screen and alt key pressed. Then I moved the cursor. 
That didn't work either...

---

