---
title: "multi monitor in gutsy"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-10-25
Just installed gutsy gibbon
I use multi monitor, on feisty I had to edit my xorg.conf file.
The tool "Screens and Graphics" appears to be able to configure multi monitor but only 1 is detected. Is there a way to force it or am I back to editing my xorg.conf file again

---

### Post by Qwerty_ on 2007-10-25
Have you installed the restricted drivers?

Although I am not sure how much they will help though. First port of call though.

---

### Post by stfury on 2007-10-25
i have the same problem gutsy can only detect one of the monitors anyne know how to fix?

---

### Post by Old Pink on 2007-10-25
Have you tried plugging in the additional monitor, leaving it plugged in and rebooting, then after the reboot going to the Screen settings?

---

### Post by earobinson on 2007-10-25
what gfx card do you have?

---

### Post by bigmonmulgrew on 2007-10-25
> **Qwerty_ said:**
> Have you installed the restricted drivers?

Although I am not sure how much they will help though. First port of call though.

yes done that  made things worse dropped my resolution to 800x600 and 1 monitor goes black , was previously clone

---

### Post by bigmonmulgrew on 2007-10-25
> **Old Pink said:**
> Have you tried plugging in the additional monitor, leaving it plugged in and rebooting, then after the reboot going to the Screen settings?

not quite sure i'm following they are boith already plugged in

---

### Post by bigmonmulgrew on 2007-10-25
> **earobinson said:**
> what gfx card do you have?

POV 7600 GS 256MB

---

### Post by bigmonmulgrew on 2007-10-25
> **stfury said:**
> i have the same problem gutsy can only detect one of the monitors anyne know how to fix?

Yes Will post my xorg,conf file see if that helps you

---

### Post by bigmonmulgrew on 2007-10-25
Right now its working.
I installed the restricted drivers, and then (after a few attempts) edited my xorg.conf file to read the following

```

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option "AddARGBVisuals" "True"
        Option "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"TFT"
	Modelname	"Custom 1"
	Option "DPMS"
	Horizsync 28-64
	Vertrefresh 43-60
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"TFT"
	Option		"TwinView"	"on"
	Option		"SecondMonitorHorizSync"	"30-85"
	Option		"SecondMonitorVertRefresh"	"50-160"
	Option		"TwinViewOrientation"	"LeftOf"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2560	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

```

The difference being the virtual part i think.
In feisty it read
```

SubSection "Display"
		Depth	24
		Modes		"2560x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection

```

I would still like to be able to set this in the gui but I can live with this

---

