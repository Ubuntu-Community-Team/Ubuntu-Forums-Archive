---
title: "Helping hand for ATI (nvidia also?) users"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Kobalts on 2006-10-14
I am a n00b to this, so I thought I would share what I did to fix my display problem I had with my ATI 9600 PRO gfx card.  I installed the latest ATI gfx drivers (8.29.6)

The problem was that on login, the screen was stuck at 60hz. The other problem was that any game/app that wanted to start full screen, errored out with cryptic errors.  Stuff like mythtv said 'floating point error' bzflag said 'BadValue (integer parameter out of range for operation)'

THe fix for this was to edit the xorg.conf file so that I would have the mode lines in 3 areas.
Here is what it looks like now:

The stuff in **BOLD** is what I changed/added.  The frequency stuff is for a iiyama 8617E monitor.  YOURs will be different if you have a different monitor!
sidenote, yes, I know the 8617E can have higher res than 1152x768...

```
Section "Monitor"
	Identifier   "Generic Monitor"
	[B]HorizSync    23.0 - 86.0
	VertRefresh  50.0 - 120.0[/B]
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	[B]HorizSync    23.0 - 86.0
	VertRefresh  50.0 - 120.0[/B]
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "vesa"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		**Modes    "1152x864" "1024x768" "800x600" "640x480"**
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		**Modes    "1152x864" "1024x768" "800x600" "640x480"**
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

Now I don't get any of those cryptic error messages, and everything now works as expected. Even the login screen is correct now! =D>

---

