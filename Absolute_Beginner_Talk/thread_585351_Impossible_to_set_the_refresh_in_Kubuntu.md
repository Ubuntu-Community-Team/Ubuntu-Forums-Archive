---
title: "Impossible to set the refresh in Kubuntu"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Landrovan on 2007-10-21
I just installed Kubuntu Gusty, and I enable the use of the nvidia drivers in the restricted driver manager (I have a GeForce 8500 GT). My screen is an LG 20" that supposed to run at 1680x1050 at 60Hz. In KDE, i choose the monitor "LCD Panel 1680x1050" and I put it in widscreen mode. So I can choose the good resolution, but I can only choose a refresh rate of 59Hz. Because my screen think I give him 60Hz, I have blur on some vertical line.

So I change the xorg.conf file to set the horizontal and vertical refresh rate. I got this:
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	30.0-83.0
	Vertrefresh	56.0 - 75.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8500 GT]"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8500 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection


I only change the refresh rate. And if I restart the X or do a real shutdown, in the system settings of KDE I still only can choose 59Hz.

What can I do?

---

### Post by jd65pl on 2007-10-21
Can you set the refresh rate using

```
nvidia-settings
```

---

### Post by Landrovan on 2007-10-21
In nvidia-settings, the refresh rate is set to 60Hz. I click save and it doesn't change anything

---

### Post by Landrovan on 2007-10-21
Ok now work,

I was needed to click "save to x configuration file" and restart the x server

Thanks

---

