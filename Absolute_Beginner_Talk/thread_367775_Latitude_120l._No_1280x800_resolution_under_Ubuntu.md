---
title: "Latitude 120l. No 1280x800 resolution under Ubuntu 6.10"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by firsak on 2007-02-22
No native screen resolution under Ubuntu 6.10 with Dell Latitude 120L. Only 1024x768 is available. Though under section screen xorg.conf file I have the following:

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection
EndSection

What's wrong? BTW, I'm a complete noob.

---

### Post by Troubled on 2007-02-22
I have the exact same problem, and I've yet to find a solution.

One bit of advice, though --- don't follow the instructions you find unless you are absolutely certain you can do a complete restore of your system. I've tried following some of the recommendations that have been posted on these forums, and (two "solutions" later) my computer crashes whenever I try to adjust my resolution, and my refresh rate is about 1/5 of what it used to be.

Beware!

---

### Post by roboducky28 on 2007-02-24
Hello,

I have a compaq v6000 series, and I have the same problem....I am unable to select 1280x800 in my screen resolution preferences.  The highest it lets me go is 1048x768, and I don't even know where that is coming from....this seems like a big deal to a lot of people on the forum, and no one seems to have an answer!!  Are they currently trying to fix this for the next Ubuntu release? or is there some driver I can install?

This is my Xorg.conf file:

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
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

---

### Post by chrome307 on 2007-02-24
Sorry to add to this but I'm another newbie stuck at 1024x768 .......... apart from this minor annoyance I'm a happy bunny !

---

### Post by robophred on 2007-02-24
> **Troubled said:**
> I have the exact same problem, and I've yet to find a solution.

One bit of advice, though --- don't follow the instructions you find unless you are absolutely certain you can do a complete restore of your system. I've tried following some of the recommendations that have been posted on these forums, and (two "solutions" later) my computer crashes whenever I try to adjust my resolution, and my refresh rate is about 1/5 of what it used to be.

Beware!

I had the same issues trying to get nvidia trueview functioning.  I ended up reinstalling Ubuntu 2 times before I finally was able to get the nvidia drivers functional.

Anyway, I had a fight with the refresh rate and screen ratios before (several times before), I was finally able to learn that you need to get the horizontal and vertical refresh rates from your monitor manual or the web and enter them into the xorg config lines

HorizSync 30-67
VertRefresh 30-60

Apparently most drivers will lock out modes it thinks your monitor cannot handle, based on the h and v refresh rates you give it.

Of course, after I got the nvidia drivers installed, my refresh rate locked from 75 back to 60 again... drat...

---

### Post by firsak on 2007-02-25
That sucks!

---

