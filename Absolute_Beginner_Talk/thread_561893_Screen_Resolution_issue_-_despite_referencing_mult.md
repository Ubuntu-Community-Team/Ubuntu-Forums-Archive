---
title: "Screen Resolution issue - despite referencing multiple threads here!"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by themainliner on 2007-09-28
I realise (after two days of heavy searching and testing) that Screen Resolution problems with Intel chipsets are de rigeur.  I have tried a lot of the things suggested so I thought I'd try to get help with my specific issue.

OK, for my sins I am trying to configure Edubuntu 7.04 on a IBM NetVista (urrgghhh), it appears to have an Intel 845G chipset and Edubuntu has configure xorg.conf to use the i810 (urrgggghhh) driver.

I installed 915resolution and followed [these steps]("http://ubuntuforums.org/showthread.php?t=351647&highlight=Intel+845G").  I had to use the command line to copy back the original 915resolution file and I've lost count of the modification I've done to xorg.conf that I've had to undo this way.

Here are the appropriate sections of xorg.conf:
```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SyncMaster"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

Wanna see it all?

**My problem is simple I cannot change the screen res to anything other than 640 x 480, 75 Hz...surely we can do better than this.**

---

### Post by kosmic on 2007-09-28
Your problem is in this section :

Section "Monitor"
    Identifier    "SyncMaster"
    Option        "DPMS"
EndSection


Just insert your VerticalRefreshRate and Horizontal Refresh rate of your monitor, and you
should be capable of changing resolutions after that.

it should be something like that :
HorizSync       30.0 - 86.0 (Change this it your Horizontal R. Rate) See in your Manual
VertRefresh     55.0 - 75.0 ("                     "                       ")

---

### Post by themainliner on 2007-09-28
Yes, I have tried that the appropriate values are:```
HorizSync 30.0 - 81.0
VertRefresh 56.0 - 75.0

```
Inserting these lines into xorg.conf killed my X session and I had to restore a xorg.conf backup without these lines. :confused:

OK, I had another go with this and this time the X server is accepting those values in the xorg.conf - still trying to change resolution...

---

