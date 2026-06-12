---
title: "X server config"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Mowcius on 2007-04-05
part way through the x server config my computer is asking me what the desired default color depth in bits is

i selected 24

then it came up with a message at the bottom saying:

x server-xorg postinst warning: over possibly-customised configuration
        file backup; in /etc/x1/xorg.conf. 20070404210759

it then came up with the command prompt

what do i do?

---

### Post by mikeyphi on 2007-04-05
Did everything work OK after a reboot?

---

### Post by Mowcius on 2007-04-05
No

I've tried many times and none of those tries have worked

---

### Post by sandman55 on 2007-04-05
does typing startx help 
by the way I looked at my xorg.conf file and here is part of it 
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

``` note my default depth is 24 but other than that I cant help you its the blind leading the blind

---

### Post by Terl on 2007-04-05
What choices are you selecting before then?  Are you entering your monitor information?  What might you be entering?  Which video card did you select?  I am thinking there is something amiss with the monitor info.

---

### Post by Mowcius on 2007-04-05
i was just entering default for all of the options that i wasn't sure of

---

### Post by Terl on 2007-04-05
Did you check your monitor specs before selecting a horizontal synch and vertical synch?  Those need to be accurate.

---

### Post by Mowcius on 2007-04-05
i chose simple so it just asked me the rough size of the screen

---

