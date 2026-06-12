---
title: "help! stuck with 640x480 screen reolution"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by painterboy on 2006-12-17
hey ive been trying to figure out how to get the proper resolution for my monitor for a couple of days now and cant figure it out on my own. Here are the specs...

optimal resolution (the one I had in windows and the one I want)  1024x768 @75hz
hor. scan range 30-70 khz
ver. scan range 50-160 hz
preset display modes 
1024x768 vesa  hor. freq. 60khz   ver. freq. 75hz  pixel clock 78.8 mhz sync polarity ++
1024x768 vesa  hor. freq. 68.7khz   ver. freq. 85  pixel clock 94.5 mhz sync polarity ++

The modeline that was generated is "1024x768 75.00"  81.80 1024 1080 1192 1360 768 769                    772 802 -hsync +vsync
 
here is the relevant part of my etc/X11/xorg.conf

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E773c"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E773c"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Right now the only resolution i have is 640x480 with no other options available. I have tried sudo dpkg-reconfigure xserver-xorg,  tried downloading new version of i810 driver, tried 915resolution and so far nothing has worked now my only conclusion is I messed up some steps somewhere (very possible) or these arent the correct solutions to my problem.  If someone has some ideas or maybe could point me in the right direction I would very much appreciate it.  Thanks in advance

---

### Post by taurus on 2006-12-17
Not even with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by painterboy on 2006-12-17
nope tried it a couple of times even with after turning off X.  What I dont get is that the resolution i want is listed as available but when i go to preferences to change the resolution The only option i have is 640x480

---

### Post by taurus on 2006-12-17
What video card do you have and which release are you running right now?

---

### Post by painterboy on 2006-12-17
No graphics card to speak of, just the intergrated one from Intel 
82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device to be exact

---

### Post by painterboy on 2006-12-17
Sorry forgot to say that I am running dapper

---

### Post by Westies on 2006-12-17
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
Perhaps this will help :)

---

### Post by painterboy on 2006-12-17
Thanks westies I have tried 915resolution but this link you gave me seems a little more in depth im going to take a look right now.  Wish me luck

---

