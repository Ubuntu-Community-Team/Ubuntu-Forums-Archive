---
title: "[SOLVED] First go at linux and no multimonitor or usb detect"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-09-03
Hi this is my first plunge into the Linux world. I have 2 problems at the moment. More are sure to follow.
1. I usually use multiple monitors. Currently 2 fed off a gf 7600. when using ubuntu I only get 1 monitor. I would like to use both like I can in windows to extend my desktop accross multiple monitors. Anyone know how.

2. I have a USB keyboard and mouse. When ubuntu boots they wont work. If I pull the dongle out and stick it back in it works fine. Its plugged in the front so it's only a minor annoyance but I'd still like to fix it. They both work fine before linux boots

---

### Post by bonzodog on 2007-09-03
Try this tutorial for xinerama set up on your monitors:

[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by bigmonmulgrew on 2007-09-24
I would like to thank everyone who has helped me get multi monitor working. It's now working superbly 
I have the time in the corner of both screens and a task bar on each screen.

For those wishing to enable multi monitor these are the changes I made

..............................................................
Open a terminal and type 
sudo gedit /etc/X11/xorg.conf
its case sensitive.

Below are the changes I made to my xorg.conf The changes I made are highlighted in blue.
I then saved and rebooted.  I had to alter the resolution and manually add task bar etc but that part is easy

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	 
EndSection

[COLOR="Blue"]Section "Monitor"
	Identifier	"TFT"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection[/COLOR]

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	[COLOR="Blue"]Monitor		"TFT"
    Option         "TwinView" "on"
    Option         "SecondMonitorHorizSync" "30-85"
    Option         "SecondMonitorVertRefresh" "50-160"
    Option         "TwinViewOrientation" "LeftOf"[/COLOR]
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth	24
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

---

