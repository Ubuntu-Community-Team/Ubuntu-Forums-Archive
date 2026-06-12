---
title: "3D Card issues (laptop)"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Trollax on 2007-02-27
Currently I'm Running Ubuntu Edgy on a laptop (Compaq nx6120) and I'm having major chunking issues with any game that uses 3D acceleration (namely Nexuiz).
The Laptop uses the Intel i915 graphics chip,

The relevent section of my Xorg.conf file reads as follows:

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

I'm thinking it may be possible that the System's onboard RAM isn't being allocated properly as it's *supposed* to go up to 128MB. But I'm not entirely sure.

That aside, how do I add in more options for screen resolution under  'System>Preferences>Screen Resolution'? At present it's just the monitor's optimal resolution at (1024 X 768 )

---

### Post by Crooksey on 2007-02-27
```
$ glxinfo
```

Paste the results.

---

### Post by Trollax on 2007-02-27
[IMG]http://exile.pinktowel.net/pics/Glu.gif[/IMG]

Okay. replaced it with a screencap

---

