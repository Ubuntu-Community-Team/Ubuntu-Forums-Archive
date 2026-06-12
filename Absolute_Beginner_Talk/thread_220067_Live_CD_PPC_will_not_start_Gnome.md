---
title: "Live CD PPC will not start Gnome"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by laube on 2006-07-20
I downloaded 6.06 ppc, it boots nice, but when Gnome should start, the screen stays black. Switching to terminal mode, running dpkg-reconfigure xserver.xorg shows that the grahic card is identified. 

sudo /etc/init.d/gdm stop stops gdm,
sudo /etc/init.d/gdm start results into error, can not find screen.

What do I wrong? I had the impression, the live-Cd would start easy:-k

---

### Post by TravisNewman on 2006-07-20
Could you provide some specs for us? It would help to know what architecture you're running and what graphics card you're using.

Also, could you drop to the command line after GDM fails, and type:
sudo more /etc/X11/xorg.conf
And post the contents relating to the video card and monitor?

It COULD be a bad burn or download I suppose.

---

### Post by linear on 2006-07-21
What model Mac? For example, the iMac G3 requires some modifications to xorg.conf in order for video to work properly.
 
BTW, with the Dapper Live CD, you need to use **sudo killall -HUP gdm** to restart Gnome. (Not a problem after install.)

---

### Post by laube on 2006-07-21
[QUOTE=panickedthumb;1281995]Could you provide some specs for us? It would help to know what architecture you're running and what graphics card you're using.

Also, could you drop to the command line after GDM fails, and type:
sudo more /etc/X11/xorg.conf
And post the contents relating to the video card and monitor?

I have my doubts on the bad burn. Her is the section:

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 PR/PRO AGP 4x TMDS"
	Driver		"ati"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 PR/PRO AGP 4x TMDS"
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

Regards and thanks for your time
Herbert

---

### Post by laube on 2006-07-21
> **linear said:**
> What model Mac? For example, the iMac G3 requires some modifications to xorg.conf in order for video to work properly.
 
BTW, with the Dapper Live CD, you need to use **sudo killall -HUP gdm** to restart Gnome. (Not a problem after install.)

It is an IMac Blueberry
Powerpc 750 (32.1) (G3) (Newworld)
400 MHz

Thnks for your time
Herbert

---

### Post by laube on 2006-07-21
What are the possible options for the video option at boot time?

I think the issue starts here. 

I just tried live-powerpc video=ofonly :confused: 

First, it starts with the last lines of the screen in white, then a alarm window opens with:

Failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Past that, I get the log-on messages, I would also see in a terminal window, but the lines ending not with the correct line end, so the next line start, where the further line ends. :confused: 

Herbert

---

### Post by laube on 2006-07-22
Problem solved,

found the right nput at 
[http://www.ubuntuforums.org/showthread.php?t=219532](http://www.ubuntuforums.org/showthread.php?t=219532)

Thanks for all who tried to help. 

Herbert
:p

---

