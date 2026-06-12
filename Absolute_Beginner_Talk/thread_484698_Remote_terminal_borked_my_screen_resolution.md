---
title: "Remote terminal borked my screen resolution"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2007-06-26
Running Dapper 6.04. Last night I was using my laptop as a remote terminal to my main desktop. At the end of the session I closed down my desktop using my laptop. This morning when I fired up the desktop, I can only get 640x480 resolution when I key System>Preferences>Screen resolution. My xorg.conf file shows this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. Savage 4"
	Monitor		"GATEWAY EV70"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x856" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x856" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x856" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x856" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x856" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x856" "800x600" "640x480"
	EndSubSection
EndSection

```  

How to I get my normal 1024x768 res back?

---

### Post by Dritzen on 2007-06-26
What is that 800x856 resolution in there?  I've never seen it before.  Perhaps it is testing whether it can use that resolution and just defaulting to 640x480.  I'd try removing that from all of the lines.  Make a backup of your file first of course.

---

### Post by SteveHoffmanUK on 2007-06-27
Dritzen

Thanks very much for taking the time to reply. 

I had not noticed the strange resolution of 800x856. This morning I booted up to delete it from my xorg.conf file as you suggested, and the screen res had reverted to the correct one of 1024x768 without my doing anything.:confused:

I rechecked xorg.conf and the strange res is still there. I am not going to change anything at the moment unless the problem reoccurs.  I also noticed that my keyboard has now changed from UK to US, so I am concerned that I may have some kind of hardware instability.

Anyway, thanks again for your help.

---

