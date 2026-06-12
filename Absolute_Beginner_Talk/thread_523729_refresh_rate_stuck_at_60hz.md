---
title: "refresh rate stuck at 60hz"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by fasad on 2007-08-12
G'day all,

 Firstly, I have no experience with anything to do with linux or unix, etc. I have been using MS-dos through MS winXP for ~20 years.

 I've just installed Ubuntu 7.04, and I cannot change the refresh rate. The change screen resolution dialog states the refresh rate is 85 hz (the only option), yet the monitor is running at 60hz. This is very unpleasant.

I've followed some advice on another forum, and ran some x-something config, but now when I load the computer, X Window (or something like that) states something is wrong, restricting me to the terminal/command prompt. I will reinstall ubuntu tomorrow.

 Is there a simple way to change the refresh rate and screen resolution? I have found my way to the terminal, but have no idea how to use it. I've seen solutions to this problem involving downloading files and typing cryptic commands, which seems rather laborious for something so trivial as changing refresh rate. Again, I don't know anything about linux.

Also, do I need to install drivers for my video card (ati x1950)? I downloaded the linux drivers from ati.com, but they seem to be only for red-hat.

 Thanks :)

---

### Post by ridgeland on 2007-08-12
from a terminal edit the system file, first make a backup
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.20070812
$ sudo gedit /etc/X11/xorg.conf
There you have sections to define the refresh rate and the default resolution;
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 7300 LE"
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

```
Refresh rates are in Monitor section
Edit the Modes as needed - the first listed is the default - Here 1024x768, you can pick the sequence, It also lists the resolution that will be available.

---

