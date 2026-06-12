---
title: "Total newb... widescreen and wireless problems."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Mediocreman on 2006-06-06
Hello all. Linux newb here trying Ubuntu on my laptop again. I'm using Ubuntu 6.06. I can't get my screen resolution over 1024x768, but when I look at xorg I get this: 

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
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

So, I should be able to get that resolution right? I think it could be this: 

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Again, total newb here so I'm probably wrong.

As to the wireless, I have a broadcom card that's not showing up at all. I'm completely lost here so any help here would be nice.

---

### Post by Jason_25 on 2006-06-07
Comment out DDC in your modules section and restart x.  If that doesn't work, post your Xorg.0.log.

---

