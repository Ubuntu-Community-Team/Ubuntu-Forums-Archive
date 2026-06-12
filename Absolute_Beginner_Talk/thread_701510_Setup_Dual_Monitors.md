---
title: "Setup Dual Monitors"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by wolveirne16 on 2008-02-19
Hey Guys - I'm having some problems setting up a dual monitor display. I have one working just fine right now, and the other one works just fine as well (when I set it as the default display). However, I can't get them to display at the same time. What should I add to my xorg.conf file to force it to have the dual monitor display. My current xorg.conf:

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E153FP"
	Horizsync	30.0-63.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1280x960@60"
	EndSubSection
EndSection

Any ideas, comments, help with this?

---

### Post by Hobo Joe on 2008-02-19
What are your graphics card and drivers?

---

### Post by Guitaraholic on 2008-02-19
im also interested in setting up a dual monitor display using 7.10 

got a 7600gt xxx edition....

latest drivers....

is it easy to setup?

---

### Post by blithen on 2008-02-19
Making this WAY harder then it needs to be. make sure you have the most updated drivers for your card then run.
```
gksudo nvidia-setting
```
Obviously only works if you have an nvidia card.
The program is rather self explanatory.
Post again if you need help though.

---

### Post by Hobo Joe on 2008-02-19
Yes, provided the drivers are correctly installed it's a breeze, I'm doing it right now without any problems.

---

### Post by Northsider on 2008-02-19
I have dual monitors set up, but I still cannot get the 2nd monitor to extend the desktop.  Instead it just mirrors it, so it's pretty useless.

---

### Post by Hobo Joe on 2008-02-19
> **Northsider said:**
> I have dual monitors set up, but I still cannot get the 2nd monitor to extend the desktop.  Instead it just mirrors it, so it's pretty useless.

What drivers are you using? That's a pretty easy fix if you're using nVidia. Just open the control panel, select the second monitor, then instead of 'clone desktop', set it to 'Twinview'.

---

### Post by wolveirne16 on 2008-02-19
Well I built this computer from spare parts so bear with the crappy video cards.

One is a ATI Rage128 Pro Ultra, the other is an ATI Mach 64, the rage is AGP and the Mach64 is PCI.

---

### Post by Northsider on 2008-02-19
I've got some crappy ATI Mobile Radeon.  IGP 345 or something.  My computer is Sony Vaio pcg k45

Here we go: ATI® Mobility Radeon&#8482; IGP 345M Graphics Controller Driver

---

### Post by wolveirne16 on 2008-02-19
any other thoughts?

---

### Post by aaguilar4 on 2008-02-20
I want to set up dual monitors, and I have the problem where if I put dual monitors, then my second one doesn't show the whole screen (and is not centered either).  My monitor has a widescreen resolution of 1440*900 and my laptop screen has the same one... so I don't see why it would the image would be shifted on the second monitor.  

I have an Intel Graphics Accelerator:** Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller**
On the Screen and Graphics tab it says that my driver is: **intel - Experimental modesetting driver for linux**
For screen 2, the only option available is Default Screen (it won't let me select it as a Secondary Screen)  

I also tried chanigng my driver to the actual one for **Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller**, that worked and let me do both screens at the same time; however as soon as I disconnected the cable, my laptop screen got very distorted and wouldn't display my whole desktop (only the top right corner pretty much). 

It works fine on Windows so it's not the cable or anything like that.  

Help please...

---

