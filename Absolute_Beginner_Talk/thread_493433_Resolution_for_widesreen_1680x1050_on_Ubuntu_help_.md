---
title: "Resolution for widesreen 1680x1050 on Ubuntu help please !"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by silverhalo1 on 2007-07-05
Hi,
After dl the latest driver and used ENVY on ATI 9600 graphic card, I couldn't get Ubuntu to display 1680x1050 for my wide screen 22" monitor.  I m just a noob to Linus, please explain solutions in not so technical term.

Thanks

---

### Post by metallicamaster3 on 2007-07-05
you need to manually go into your xorg.conf file and put that resolution in there.....hopefully someone who has a ATI card can help you further, as i use nVidia, so my help stops here. sorry :(

---

### Post by overdrank on 2007-07-05
> **silverhalo1 said:**
> Hi,
After dl the latest driver and used ENVY on ATI 9600 graphic card, I couldn't get Ubuntu to display 1680x1050 for my wide screen 22" monitor.  I m just a noob to Linus, please explain solutions in not so technical term.

Thanks

HI you can try and edit you xorg with this command
```
gksudo gedit /etc/X11/xorg.conf
```
 scroll down and find the monitor section should look like this 
```
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
```
Then add the resolution that you want to each line and dont forget to add the " "
YOU can crash you xorg so back it up before any changes are made. Good luck!

---

### Post by silverhalo1 on 2007-07-05
It din't work.  Please see my attachment.
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

### Post by overdrank on 2007-07-05
You have two threads going at the same time! :(

---

### Post by silverhalo1 on 2007-07-05
> **overdrank said:**
> You have two threads going at the same time! :(

oops... I will remove the other thread

---

