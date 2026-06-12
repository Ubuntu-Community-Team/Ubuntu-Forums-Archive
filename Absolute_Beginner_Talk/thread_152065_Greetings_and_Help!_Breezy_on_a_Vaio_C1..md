---
title: "Greetings and Help! Breezy on a Vaio C1."
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by MarkTBSc on 2006-03-29
Hello all. I've been meaning to try out Ubuntu for some time and I finally got around to installing it on my Vaio C1VFK (667Mhz Crusoe processor, bluetooth module, upgraded 80Gb HDD, 128Mb RAM, 1024x480 display)

I installed Breezy without too much trouble. When I got to the GUI, the screen did get all screwed up but I managed to get around that by only allowing Ubuntu to load the 640x480 display module.

The display is now offset. the toolbar at the top goes up off the screen and comes back on the bottom. There's also a portion lost somwhere as the join cuts through the icons on the bar and I can barely see any of them. A couple of pixels above and below the join, that's all.

Could some kind person educate me as to what I need to do in order to get the desktop displaying properly? Also, keep in mind that I'm as thick as two short planks. If you need me to work in the Terminal then you'll need to tell me how to get there!

Thanks again!

---

### Post by endersshadow on 2006-03-29
Try running this in the console:

```
sudo dpkg-reconfigure xserver-xorg
```

It will take you through a couple of fairly easy to answer questions.  Restart X (Ctrl+Alt+Backspace (not Del)), and you should be all set.

---

### Post by ranf on 2006-03-29
I have a C1VE. I'm not sure how much these differ.
1. try to search these forums for "c1ve".
2. tuxmobil: [http://tuxmobil.org/sony.html](http://tuxmobil.org/sony.html)
3. linux-on-laptops: [http://www.linux-on-laptops.com/sony.html](http://www.linux-on-laptops.com/sony.html)

A lot to read.

It sounds like you need a Modeline in your xorg.conf.

---

### Post by MarkTBSc on 2006-03-29
[QUOTE=endersshadow]Try running this in the console:

```
sudo dpkg-reconfigure xserver-xorg
```

It will take you through a couple of fairly easy to answer questions.  Restart X (Ctrl+Alt+Backspace (not Del)), and you should be all set.[/QUOTE]


Thanks. However, I've tried this one. It was what allowed me to get the video element of the GUI to work at all. It had no effect on the custom layout of the display.

Unfortunately the 1024x480 isn't a normal one for any OS.

---

### Post by rupert on 2006-08-29
did you had any luck with this,
I have a PCG-C1VFK here and really trouble getting xorg on dapper to display everything correctly.

here a cut from my xorg.conf, maybe you can post yours,
and what driver do you use?

```

Section "Device"
	Identifier	"rage"
	Driver		"ati"
	BusID		"PCI:0:13:0"
	VideoRam	8000
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"rage"
	Monitor		"Standardbildschirm"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x480"
	EndSubSection
EndSection


```

big thx

---

### Post by Duckrow on 2006-11-20
> **MarkTBSc said:**
> Hello all. I've been meaning to try out Ubuntu for some time and I finally got around to installing it on my Vaio C1VFK (667Mhz Crusoe processor, bluetooth module, upgraded 80Gb HDD, 128Mb RAM, 1024x480 display)

I installed Breezy without too much trouble. When I got to the GUI, the screen did get all screwed up but I managed to get around that by only allowing Ubuntu to load the 640x480 display module.

The display is now offset. the toolbar at the top goes up off the screen and comes back on the bottom. There's also a portion lost somwhere as the join cuts through the icons on the bar and I can barely see any of them. A couple of pixels above and below the join, that's all.

Could some kind person educate me as to what I need to do in order to get the desktop displaying properly? Also, keep in mind that I'm as thick as two short planks. If you need me to work in the Terminal then you'll need to tell me how to get there!

Thanks again!

I have this working on my PCG C1XN. You need to edit xorg.conf entries from 1024x768 1024x480. remember to ctr+x to exit and then try to shift the window up to find the save button. If you want more details I'll post how I did it and my xorg file which is randomly based on various pages I found on searches (My understanding of these things is very limited)

---

