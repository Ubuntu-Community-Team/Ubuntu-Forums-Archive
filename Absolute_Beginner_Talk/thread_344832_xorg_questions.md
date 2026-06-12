---
title: "xorg questions"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2007-01-23
I have 2 xorg questions. First the easier one -- how can I delete backups of my xorg file? I've been trying to get a new monitor set up and I've generated several backups I'd like to rid myself of, but the gui does not allow deletion from the x11 folder.

Second -- how can I get my resolution settings to work properly? When I first installed Ubuntu, I ran the sudo dpkg-reconfigure -phigh xserver-xorg command to set up for my (now old) monitor and all went fine, but now I can't get all the way through the steps. 

I've been trying to get a new widescreen monitor set up, but when I run the reconfiguration utility I get kicked out when I try to finish the second prompt (the one where I pick screen resolutuions). The terminal dialog gives this warning: "overwriting possibly-customised configuration." 

I also wonder if I've made a hash of my xorg file. I've pasted in the pertinent sections below.

After restarting the x server, I do have different resolutions to choose from, but they seem to be one step lower than the ones I picked. I selected 1680/1400, 1050/1050, 1440/900 and 1280/800, but the drop-down menu offers 1600/1200 and 1400/1050, as well as 1280/1024, 1024/768, 800/600 and 640/480. 

I've tried directly editing the xorg file in the terminal window, but when I run sudo nano etc/x11/xorg.conf, the resulting text editor shows an empty file. When I use the GUI to view my xorg file it has the following information pertaining to video output:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X800"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1440x900" "1280x800"
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


And suggestions?

---

### Post by pizzutz on 2007-01-23
Well, I can't answer all of your questions, but here are a couple of things. 

sudo nano /etc/x11/xorg.conf  doesn't work because linux is case sensitive...
sudo nano /etc/X11/xorg.conf


backups can be deleted from the terminal with 

sudo rm xorg.bak

or if you like bungee-jumping, skydiving and other risky activities hit alt-F2 or from the terminal type 

gksu nautilus

---

### Post by bcdeck on 2007-01-23
Case sensitive.. D'OH!   

Thanks, pizzuts.  :)

But... I replaced the resolution options in xorg, rebooted and I still get these choices in the drop-down menu for screen resolution: 1600/1200, 1400/1050, 1280/1024, 1024/768, 800/600 and 640/480.

My xorg now looks like this:

---

### Post by ljpm on 2007-01-23
Did you enter the HorizSync and VertRefresh ranges or were they auto detected. If these values were autodetected they may be wrong. If they are wrong then this may be preventing the higher resolutions.

---

### Post by bcdeck on 2007-01-23
I was kicked out of the autoconfig utility before the point where I could enter refresh rates, and when I manually edited xorg I didn't change them. the first time I edited it I missed the line that starts with "depth 24" (which I assume means 24-bit color), and my values never changed. I finally changed that line, and on reboot I got the "value out of range" message and could see nothing once X started. 

I've gotten that fixed via the recovery mode -- set 1280x1024 as the only resolution and didn't change refresh rates -- and now I can see the gui but my screen also has a "no signal" message in the center. It's as if the display is showing a signal that it doesn't realize it's getting.

So now that I can see the gui and Web-search to find appropriate values, I'm going to try and fix my xorg.conf, which looks like this at the moment:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-89
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X800"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

---

