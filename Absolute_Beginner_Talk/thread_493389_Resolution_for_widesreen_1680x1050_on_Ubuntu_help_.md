---
title: "Resolution for widesreen 1680x1050 on Ubuntu help please !"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by silverhalo1 on 2007-07-05
There are several threads provided help for resolution but none are fit mine.  I updated latest ATI 9600 driver and even use ENBY but still couldn't get resolution up to 1680x1050 for wide sreen even my ATI 9600 support it.

I m just a noob to Linus so please explain the solution in plain English please.

Thanks

---

### Post by Pragmatist on 2007-07-05
Please attach your **/etc/X11/xorg.conf**

---

### Post by robertc36 on 2007-07-05
Found these instructions seem fairly straight forward 
[http://ubuntuforums.org/showthread.php?t=490587&highlight=resolution+ati](http://ubuntuforums.org/showthread.php?t=490587&highlight=resolution+ati)

---

### Post by silverhalo1 on 2007-07-05
> **Pragmatist said:**
> Please attach your **/etc/X11/xorg.conf**

Here it is, I still couldn't get the 1680x1050 .
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
        Option           "metamode" "LCD: 1680X1050_60_0 +0+0"
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"
	EndSubSection
EndSection

---

### Post by Pragmatist on 2007-07-05
>          Option           "metamode" "LCD: 1680X1050_60_0 +0+0"

Did you follow some instructions for this line?  If so, what instructions?

Have you tried just leaving the 1680x1050 resolution in depth 24?

In other words, you change this:
```
 		Depth	24
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"
	EndSubSection
```

To this:
```
 		
Depth	24
 		Modes		"1680x1050"
 	EndSubSection

```

---

