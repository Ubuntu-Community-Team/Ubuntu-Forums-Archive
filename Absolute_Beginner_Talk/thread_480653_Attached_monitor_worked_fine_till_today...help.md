---
title: "Attached monitor worked fine till today...help"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-06-21
I have a keyboard/mouse/monitor ready to plug into my HP laptop at work.  It has worked great till today.  Normally, the system boots and video is displayed on both the laptop and external widescreen.  The screen resolution matches the laptop (1280 x 800) which is what I like (so I can close the top, or unplug it and go.

Today Ubuntu started up and the resolution suddenly became 1680 x 1050.  Looks great on the external, but I lose a lot on the laptop.  I cannot even select 1280 x 800 in system preferences (not there).  If I boot without the monitor plugged in I can select 1280x800.

Is there some conf file that I can set to always remain at 1280x800 ?  I poked around xorg.conf, but it seems to have the right settings listed already so I'm kind of confused.

I am using xserxer-xorg-video-intel driver from the repos.

Here is my xorg.conf file section on video if it helps any: *screen resolution is much higher than xorg has set as I type this.

```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"LinearAlloc"	"8160"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

---

