---
title: "1440x900 screen resolution"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-06-20
I'm trying to get my samsung 931BW to go 1440x900 @ 75Hz on ubuntu, but I can't figure out what changes I need to do to my xorg.conf file to allow that to happen. Right now I only have the basic options of 800x600, 640x480, and 1024x768.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-81
	Vertrefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection
```

---

### Post by Hellcom on 2007-06-20
Bump

---

### Post by Happy_Man on 2007-06-20
Change the file to look like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1440x900"
	EndSubSection
EndSection
```

---

### Post by Hellcom on 2007-06-20
Thanks, worked perfectly!

---

### Post by Cereal_Killer on 2007-06-20
I'm in the same boat, but can't get xorg.conf to open and save the work I do.  How do I do this?

---

### Post by Nikron on 2007-06-20
> **Cereal_Killer said:**
> I'm in the same boat, but can't get xorg.conf to open and save the work I do.  How do I do this?

alt+F2 
run the command
gksudo gedit /etc/X11/xorg.conf

And you should be able to edit the file

---

### Post by Cereal_Killer on 2007-06-20
Perfect!  Thank you very much.

---

### Post by Cereal_Killer on 2007-06-20
So, I did all of this editing, but it still won't let me change the resolution to 1440x900.  I know the video card will do it, cause I have a dual boot with win XP, and can set it to this and higher.

---

### Post by Happy_Man on 2007-06-20
You've got to restart X first by pressing ctrl-alt-backspace.

---

### Post by Cereal_Killer on 2007-06-20
I had actually rebooted the computer, and still nothing.  Do I still have to restart x?

---

### Post by Happy_Man on 2007-06-20
No no, rebooting does that..... well, nothing is perfect with xorg.conf.... In fact, I was half-expecting hellcom to come back saying that my fix didn't work.... it's more common for it to not work, than for it to work perfectly, I was shocked.... sorry. If you have a Nvidia card, try using the command ```
sudo nvidia-settings
``` That gives you a GUI for editing, at least.....

---

### Post by Cereal_Killer on 2007-06-20
I have an ATI card.  Tried sudo ati-settings, but nothing.  Any other ideas, anyone?  Please?

---

### Post by Cereal_Killer on 2007-06-20
Well, I figured it out.  In Xorg.conf, at the beginning, it says to run this command if you want xorg.conf to automatically update:

sudo dpkg-reconfigure -phigh xserver-xorg

From there, I selected the ATI driver, which it wasn't selected.  

Tabbed to OK, next screen asked which resolutions to show, and everything the card is capable of shows up.  Good stuff.  Thanks for the help.

---

