---
title: "Screen Resolution"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by curlyham1 on 2005-11-19
I have installed Ubuntu 5.04 in a dual boot system on a 600Mhz Pent 3 system. The video resolution  is always 640X480. On my windows 98SE system it is 1024X768. The video card is a Trident TGUI 9680. I am a real newbie and I need guidence.
                             Dave

---

### Post by estel on 2005-11-19
Ermm...

I assume that there are no choices if you go to System -> Preferences -> Screen Resolution?

Failing that, you need to reconfigure X.

Open the Terminal (Applications -> Accessories -> Terminal) and type ```
sudo dpkg-reconfigure x-window-system
```

Go for a basic setting, following the instructions: you should be able to select your range of prefered resolutions.

---

### Post by estel on 2005-11-19
There's a slightly easier way too:

In the terminal:
```
sudo gedit /etc/X11/xorg.conf
```

Go careful...
Scroll down to the **Section: "Screen"**
In each subsection, change your prefered resolutions or add new ones, for example, my section reads:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

