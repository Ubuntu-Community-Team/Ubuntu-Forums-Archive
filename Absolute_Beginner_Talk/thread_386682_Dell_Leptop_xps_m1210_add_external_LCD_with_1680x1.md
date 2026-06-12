---
title: "Dell Leptop xps m1210 add external LCD with 1680x1050 resolution"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by anter on 2007-03-17
Hi,
I'm using a dell xps m1210 12.1 laptop with 1280x800 res.
How can I add an external ACER 2016W LCD  ?
The desire resolution for the external LCD is 1680X1050.
This is my "xorg.conf": what do I need to do?
Thanks

..........
...........
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
.........
.......

---

### Post by anter on 2007-03-18
Someone please help...

---

### Post by annda on 2007-03-18
for nvidia, install the nvidia driver 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

and then type in the terminal:

gksudo nvidia-settings

you will get a nice GUI that will modify xorg.conf for you (i just did it 2 days ago and was surprised how easy that was).

---

### Post by anter on 2007-03-18
Thanks, It's working :)

This guide for NVIDIA is excellent, I'm starting to like Linux...

[http://www.ubuntuforums.org/showthread.php?t=336412](http://www.ubuntuforums.org/showthread.php?t=336412)

---

