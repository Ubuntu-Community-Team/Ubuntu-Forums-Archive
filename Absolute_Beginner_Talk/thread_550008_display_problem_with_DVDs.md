---
title: "display problem with DVDs"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by auralay on 2007-09-13
Greetings.
I tried a similar message in the multimedia & video section with no reply- perhaps someone will take pity on me as a newbie!

I have a Dell Inspiron 510m with an Intel 855GM graphics. Running Ubuntu 7.04

I can get full 1400 x 1050 resolution OK but have problems with media players. When I play a DVD it plays OK but the screen has a mesh of black dots over it. Small window or full screen same effect, the dots are always the same number of pixels apart (about every fourth in both horiz. and vert).
Same effect with other screen resolutions, eg 1280 x 1024 or 1024 x 768.

When I try to take a screen shot it shows a blank blue screen.(Now where have I seen that colour before?) I tried uploading  the screen shot here.
file:///home/jg/Desktop/Screenshot-01.png


I tried updating the i810 driver as shown here
[http://ubuntuforums.org/showthread.p...t=855+graphics](http://ubuntuforums.org/showthread.p...t=855+graphics)
This has no effect.
I l\downloaded the 915resolution program but I cant work out how to actually use it.

My xorg.conf file shows 

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection



Thanks, JG.

---

### Post by justleen on 2007-09-13
sudo apt-get install vlc


See if that works better?

---

### Post by auralay on 2007-09-13
A lot of loading went on but no change in display, even after a restart.
Thanks for trying, JG

---

### Post by auralay on 2007-09-13
OK, sorry! Forget that last post- I didn't realise it was a DVD play program.
Now I find it will give a correct display but if I try to move the time line or open and close a window in front of it then the screen just goes black and does not recover. DVD playing, sound OK but no picture!

So, halfway better but still not useable.
Thanks again for replying, JG

---

