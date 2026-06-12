---
title: "I can only get 640x480 when using a BNC cable"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-05-30
I have a Samsung SyncMaster 900IFT that I'd like to use with a BNC cable if possible, but when I hook it up I only get 640x480 as the available options despite the fact that my monitor works just fine with the standard 15-pin d-sub.

---

### Post by Wim Sturkenboom on 2007-05-30
As the system is not able to detect the monitor capabilities over the BNC cable, it will use safe settings. You have to 'hard-code' your xorg.conf.

Please post the section *device*, *monitor* and *screen* of /etc/X11/xorg.conf as well as the make/model of your video card.

---

### Post by AncientPC on 2007-05-30
Make/model is listed under device, relevent section:
```
Section "Device"
	Identifier	"Leadtek GeForce2 MX100/200"
	Driver		"nv"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Samsung SyncMaster 900IFT"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Leadtek GeForce2 MX100/200"
	Monitor		"Samsung SyncMaster 900IFT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by Wim Sturkenboom on 2007-05-30
That should work in my opinion. Sorry, don't think that I can help you further.

---

### Post by AncientPC on 2007-05-30
It's no problem, it might have something to do with the open nvidia drivers (the video card doesn't work with closed drivers) and most people don't use BNC cables for their CRTs.

---

### Post by Wim Sturkenboom on 2007-05-30
Just for the fun, try the vesa driver and see if that works. You can't get the 'extreme' resolutions, but 1024x768 should be possible with it.

---

