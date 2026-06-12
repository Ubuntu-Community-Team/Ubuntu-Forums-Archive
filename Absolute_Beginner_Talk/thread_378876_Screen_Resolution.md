---
title: "Screen Resolution"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by billie0w on 2007-03-07
Another newbie question.

How can I reset the screen resolution to my monitors required setting?

Under "System>Preferences>Screen Resolution" I get two choices. Bad and horrible. The "better" one is 800x600, the other 640x480. My monitor "requires" 1280x1024, I think it is. It is not very happy with the settings as they are now.

I tried terminal and sax2 but that doesn't seem to be in this release.

---

### Post by taurus on 2007-03-07
> **billie0w said:**
> 
I tried terminal and **sax2** but that doesn't seem to be in this release.

Isn't that program for SuSE?

You need to install a driver for your graphic card before you can go to a higher resolution.  What kind of graphic/video card do you have anyway?

---

### Post by oilchangeguy on 2007-03-07
screen resolution problems are a common issue. go to the top of the page type in screen resolution, press go.  you'll be amazed at the number of threads on the subject. one of them is bound to contain your answer.

---

### Post by Skia_42 on 2007-03-07
put this into your command line (Applications>>>System Tools>>Terminal):
> sudo gedit /etc/X11/xorg.conf
You should be able to find a part near the end resembling this:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection


You can edit the screen resolution manually in the mode box.

---

### Post by billie0w on 2007-03-07
Yes, sax2 is used in SuSE. I've been using SuSE for a little over a year now. I just wanted to see what all the fuss is about over Ubuntu. I have the computer multi-booted with XP, SuSE 10.2, Freespire [ which won't boot after Ubuntu install ] and Ubuntu Edgy Eff. I'm not a complete newbie to Linux, just to Ubuntu.

The graphics is an ATI Express200, I think.

---

### Post by billie0w on 2007-03-07
> **Skia_42 said:**
> put this into your command line (Applications>>>System Tools>>Terminal):

You should be able to find a part near the end resembling this:


You can edit the screen resolution manually in the mode box.

I get:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"HP vs17"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
	Monitor		"HP vs17"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by aliasneo on 2007-03-08
Hi i got the same graphics card and i have the same problem to this i get only 2 choices for screen resoutions 800 x 600 and lower 640 x 480 i cannot work in these resolutions did you find a solution to this i have the same xorg.conf file as you but it doesnt do any good.

thank you

---

### Post by Perfect Storm on 2007-03-08
(Just a very little side note), if you want to use gedit to edit stuff with use gksudo gedit instead (generally rule), or use nano.

---

### Post by glotz on 2007-03-08
How about a quick **sudo dpkg-reconfigure xserver-xorg** ?

---

### Post by Pikestaff on 2007-03-08
> **glotz said:**
> How about a quick **sudo dpkg-reconfigure xserver-xorg** ?

I agree, do that and then make sure you select the right drivers, and when it asks you what screen resolutions you'd like to have, arrow down to find the right ones and press spacebar to select them.  That's what I did when I had the same problem and after I rebooted I was able to choose the right screen resolution, so give that a shot.  Good luck!

---

