---
title: "Change ati propietary drivers resolutions set"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by srg84 on 2007-05-17
Hi, i want to know how to add more resolutions with ati propietary drivers installed.

My resolutions now are 

1280x1024
640x480
1152x864

And i wanna have for example 1024x768.

How to do it?

---

### Post by overdrank on 2007-05-17
> **srg84 said:**
> Hi, i want to know how to add more resolutions with ati propietary drivers installed.

My resolutions now are 

1280x1024
640x480
1152x864

And i wanna have for example 1024x768.

How to do it?

Hi you can reconfigure xorg text
sudo gedit /etc/X11/xorg.conf
If KDE replace gedit with kate
And add the resolution that you like if your monitor will support. Good luck!:popcorn:

---

### Post by srg84 on 2007-05-17
U oh bad news, my in the xorg file there are a lot of resolutions...

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"SDM-S71"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


The thing is that the propietary drivers seems to ignore xorg.conf file, why???

---

