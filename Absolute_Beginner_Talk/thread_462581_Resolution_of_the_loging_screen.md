---
title: "Resolution of the loging screen"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by mindtrick on 2007-06-02
How do I change the resolution of the login screen (gdm) ? It's currently set up to a very high resolution.

---

### Post by luckyd on 2007-06-02
The GDM screen resolution shuold be the same as XORG's resolution, so just change that and it should work.
I believe it is under Preferences/Screen Resolution/

---

### Post by alienexplorers on 2007-06-02
I have the same problem.  I want xorg.conf to provide 1280x1024 resolution while I am working, but would like a lower resolution when running the login screen.

---

### Post by Mr. Picklesworth on 2007-06-06
Hi. Strange situation here, somewhat related:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024_60.00" "1280x960_60.00" "1024x768_60.00" "800x600_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024_60.00" "1280x960_60.00" "1024x768_60.00" "800x600_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024_60.00" "1280x960_60.00" "1024x768_60.00" "800x600_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024_60.00" "1280x960_60.00" "1024x768_60.00" "800x600_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024_60.00" "1280x960_60.00" "1024x768_60.00" "800x600_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_60.00" "1280x960_60.00" "1024x768_60.00" "800x600_60.00" "640x480_60.00"
	EndSubSection
EndSection
```
Previously, it was using a refresh rate of 72 Hz, which my monitor does not like. Changed that by adding _60.00 to all those resolutions. The resolution was fine then; it was just the refresh rate being messed up.
With that now, though, (and there is no mention of 1600 anywhere in my xorg.conf), it decides somehow to give me a resolution of 1600x1200 in the login screen. It finally does get the right refresh rate, so I guess that's progress...
I have made no other changes.

The screen resolution preferences within each account also provide some really high resolutions that I did not set in xorg.conf, all the way up to 1920x1200. (I believe somebody was looking for that one? :P)

It will be a great day when this stuff starts cooperating :(
I remember reading something along the lines of eliminating the need for xorg.conf to configure this stuff was somewhere in the road map... or was that just my imagination?

---

### Post by pandion on 2007-07-30
Checkout my posts (there's more than one) on this thread for the same problem.  I'm not sure how to set the login greeter screen to be a lower resolution than what you're using for your desktop though, but this method allows you to limit the login screen resolution (will prevent it from running at a higher resolution than your desktop resolution).  Hope it helps!

[http://ubuntuforums.org/showthread.p...olution&page=4](http://ubuntuforums.org/showthread.p...olution&page=4)

---

