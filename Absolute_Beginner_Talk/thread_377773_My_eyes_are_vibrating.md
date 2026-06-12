---
title: "My eyes are vibrating"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-03-06
Contrary to the Ubuntu scrn res aplet, my monitor tells me the present res is 60hz.

Monitor is Dell P990 UltraScan Color Monitor.

Horizontal scan range 30 kHz to 96 kHz
Vertical scan range 48 Hz to 120 Hz
Optimal preset resolution 1024 x 768 at 75 Hz or 85 Hz
Highest preset resolution 1600 x 1200 at 75 Hz
Highest capable resolution 1600 x 1200 at 75 Hz

I understand my task is to find, and then edit the xorg.conf by including some of the above data.

Please could someone be more pedestrian about the cli procedure.

---

### Post by Shatrat on 2007-03-06
Well I think your monitor section of /etc/X11/xorg.conf should look like this;
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

```
But I haven't messed with this myself since I've had an LCD monitor for quite a while, and never really cared about refresh rate anyway.

You can edit that file using "sudo nano /etc/X11/xorg.conf" or "gksudo gedit /etc/X11/xorg.conf"

---

### Post by christhemonkey on 2007-03-06
Ok, try placing a modeline (given you one for your optimum preset resolution or another from here:[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)) in your xorg.conf.
```
gksudo gedit /etc/X11/xorg.conf 
```

Then look for the section starting with Monitors and add this in there:
```
     HorizSync     30-96
     VertRefresh    48-120
     Modeline "1024x768@85" 100.94 1024 1056 1432 1464 768 782 793 807
```

Then make sure that the "1024x768" resolution is listed in the Screen section.
Then restart X with Ctrl+Alt+Backspace.
Now you should have your nice optimum resolution!

---

### Post by nnjond on 2007-03-06
More complications!

gksudo gedit /etc/X11/xorg.conf  -yeilds this at 1st:

nnjond@nnjond-desktop:~$ gksudo gedit /etc/X11/xorg.conf
(gedit:15741): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

But then xorg.conf opens. My Monitor edition now looks like this, but the problem is unchanged.


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ULTRASCANP99"
	Option		"DPMS"
 	HorizSync     30-96
     	VertRefresh    48-120
     	Modeline "1024x768@85" 100.94 1024 1056 1432 1464 768 782 793 807
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"ULTRASCANP99"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection

---

### Post by taurus on 2007-03-06
Did you either reboot or restart X with <Ctrl><Alt>Backspace so the new changes would go in effect?

---

### Post by nnjond on 2007-03-06
qbooted and restarted.

---

### Post by macogw on 2007-03-06
nnjond@nnjond-desktop:~$ gksudo gedit /etc/X11/xorg.conf
(gedit:15741): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
^^^
that can be ignored.  happens all the time for no reason that i'm aware other than to scare people

---

