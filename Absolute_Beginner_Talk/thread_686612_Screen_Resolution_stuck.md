---
title: "Screen Resolution stuck"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Hybrid_1014 on 2008-02-03
Last night i shut down my comp at 1200x800 (i think thats what it was) and when i turned it on today it was/ still 640x480. is there something i can do?

---

### Post by ichbinesderelch on 2008-02-03
try editing the /etc/X11/xorg.conf, there should be a line under screen section, just replace 640x480 with 1280x800 and restart the xserver (ctrl + alt + backspace)

---

### Post by spiderbatdad on 2008-02-03
not sure. I believe I had a similar problem, briefly, after trying envy, or one of the fglrx drivers. Anyway I find a lot of theses types of problems go away if I set the gnome session up then navigate to Preferences>>Sessions>>Session Options>>Remember Currently Running Applications.

---

### Post by Hybrid_1014 on 2008-02-03
> **ichbinesderelch said:**
> try editing the /etc/X11/xorg.conf, there should be a line under screen section, just replace 640x480 with 1280x800 and restart the xserver (ctrl + alt + backspace)

i found this 
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

and this
 Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

i dont want to mess anything up so what do i switch?

---

### Post by ichbinesderelch on 2008-02-03
could it be that you installed ati catalyst control center before shutting down the pc? you should be able to change the resolution with the catalyst control center i guess!

---

### Post by Hybrid_1014 on 2008-02-03
i dont know if i did.......

---

### Post by ichbinesderelch on 2008-02-03
search your menu for catalyst control center, dunno the console command for it, maybe something like "catalyst"

---

### Post by Hybrid_1014 on 2008-02-03
i have it, but its been there for a while.......

---

### Post by Hybrid_1014 on 2008-02-03
........theres one small problem....... i cant see half the page.....

---

