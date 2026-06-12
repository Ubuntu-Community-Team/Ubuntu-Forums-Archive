---
title: "Screen resolution problems"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Thia on 2007-07-28
I have problems with resolution. My monitor resolution is 1280x1024 but i can choose only 1024x768 and lower. I've read many threads but none worked for me. I tried different  commands, including > sudo dpkg-reconfigure xserver.xorg but it says: the package is not installed...
Also tried to edit xorg.conf - no result

Can anybody, please, paste the part of the xorg.conf file whith monitor and screen settings. I'm sure that i'm doing something wrong :(

---

### Post by jmaryinchina on 2007-07-28
In a terminal (Application->Accessories->Terminal) and copy paste the result here.
Also copy-paste your xorg.conf

---

### Post by MrHippocampus on 2007-07-28
Posting my xorg.conf wont help you, but if you post yours we can have a look and see whats going wrong :)

---

### Post by myoungf1 on 2007-07-28
> **Thia said:**
> I have problems with resolution. My monitor resolution is 1280x1024 but i can choose only 1024x768 and lower. I've read many threads but none worked for me. I tried different  commands, including  but it says: the package is not installed...
Also tried to edit xorg.conf - no result

Can anybody, please, paste the part of the xorg.conf file whith monitor and screen settings. I'm sure that i'm doing something wrong :(


Its actually sudo dpkg-reconfigure xserver-xorg you were doing xserver.xorg

---

### Post by NilsE on 2007-07-28
> **Thia said:**
> I have problems with resolution. My monitor resolution is 1280x1024 but i can choose only 1024x768 and lower. I've read many threads but none worked for me. I tried different  commands, including  but it says: the package is not installed...
Also tried to edit xorg.conf - no result

Can anybody, please, paste the part of the xorg.conf file whith monitor and screen settings. I'm sure that i'm doing something wrong :(

A little more detail on what you are running won't hurt either in debugging your problem. Like what system, what distro, the video chip/card etc.

---

### Post by Thia on 2007-07-28
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	48-75
Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Monitor		"Generic Monitor"
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

Distro: Ubuntu 7.04
NVIDIA GeForce4 Ti 4200 AGP 8x

---

### Post by NilsE on 2007-07-28
What does the 3 or 4 lines above this in your xorg.conf say.  Those are actually the video device and driver.

---

