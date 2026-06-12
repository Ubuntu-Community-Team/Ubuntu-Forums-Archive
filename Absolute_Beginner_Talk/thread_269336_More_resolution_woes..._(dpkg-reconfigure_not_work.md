---
title: "More resolution woes... (dpkg-reconfigure not working?)"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-01
I've searched the forums and read every thread I came upon that dealt with screen resolution problems (yes, I know there's a lot, I apologize for adding fuel to the fire).

I've run sudo dpkg-reconfigure xserver-xorg multiple times, and the drivers / resolution selections are all correct. I always get this message upon completing it, however:

```
alexander@alex-laptop:~$ sudo dpkg-reconfigure xserver-xorg


xserver-xorg postinst warning: overwriting possibly-customised configurating file; backup in /etc/X11/xorg.conf.20061001151601
```

I used gedit /etc/X11/xorg.conf.20061001151601 and noticed that it was different from my original /etc/X11/xorg.conf, so I copied the contents, and pasted them into my xorg.conf while under sudo. I then saved and restarted the system, but nothing changed.

Originally, I could only select from the 1024x768 resolution, but after the *first* time I ran through dpkg, I was able to access 800x600 and 640x480 (not that those help me though :lol: ).

This is a widescreen laptop, so I'm attempting to get a resolution of 1280x800. The monitor is identified as "Generic Monitor" both previously under Windows and now under Ubuntu.

The following is the important bits in my current xorg.conf file:

```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

Thanks for giving us, the newbies, a helping hand. :) It is appreciated.

---

### Post by bulldog on 2006-10-01
Well basicly the 'warning' you get is that it makes a copy of your xorg.conf because it could have custom settings in it.

The number stands for date and time the copy is made.

Then it creates a new xorg.conf which you overwrite with the 'old' copy,so nothing is changed.:D

---

### Post by sitedesign on 2006-10-01
My xorg.conf file looks like this (I have a widescreen laptop as well and had   a similar problem.
```

Section "Device"
	Identifier	"sis vga"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"1280x800 lcd"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"sis vga"
	Monitor		"1280x800 lcd"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

```

Try taking out your refresh rate settings.

---

### Post by UnknownVariable on 2006-10-01
Thanks for the replies :D

I tried running dpkg again, but everytime it go to the part where it would try to autodetect refresh rates, I'd get sent back to the login screen, so I tried what sitedesign had said and took out the refresh rate settings, rebooted, and now I was able to run dpkg again, and again I got the 'warning'. Rebooted again, and now I have the same screen res. options as before: 1024x768, 800x600, and 640x480. I checked my xorg.conf file and again the refresh rates are back in there. Do take note however, after I took out the refresh rate settings and rebooted, I only had the option of 1024x768 in my preferences.

Still a bit lost as to what's going on -- any other ideas? :)

---

### Post by UnknownVariable on 2006-10-01
Downloaded and ran 915resolution and replaced 1024x768's 32bit/px mode with 1280x800 24bit/px, and that just resulted in 1024x768 disappearing completely, forcing me into 800x600. No luck there, it seems. Anybody else want to take a whack at this?

---

### Post by mips on 2006-10-01
What laptop brand/model do you have.

Could I suggest you go search in the Hardware->Video forum.

---

### Post by UnknownVariable on 2006-10-01
I've got a Gateway MX6124 laptop. I'll go check the video forum now for something that might help me out :)

---

### Post by UnknownVariable on 2006-10-01
I did find [this thread](http://ubuntuforums.org/showthread.php?t=187341&highlight=MX6124) that describes the same problem with the same model of laptop, but it seems the problem was never fully solved, and that the problem only exists with the exact graphics card I'm using. I read through it all and tried some of the xorg edits that were posted, but nothing's worked out so far.

---

### Post by UnknownVariable on 2006-10-01
I saw this in my Xorg.0.log file and thought it might be relevant:

```
[FONT="Courier New"](WW) I810(0): config file hysnc range 45.7143-50.5263kHz not within DDC hysnc ranges.
(II) I810(0): Generic Monitor: Using hsync range of 45.71-50.53 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "1280x800@60" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0):  Built-in mode "1024x768"
(--) I810(0): Display dimensions: (330, 210) mm
(--) DPI set to (78, 92)[/FONT]
```

And for reference, here's part of my current xorg.conf file.

```
[FONT="Courier New"]Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	#HorizSync	28-64
	#VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800@60"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800@60"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800@60"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800@60"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800@60"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800@60"
	EndSubSection
EndSection[/FONT]
```

---

### Post by UnknownVariable on 2006-10-01
HAHA, SUCCESS~!

Here's what I did to solve my problem, if anybody happens upon this thread at a later date.

I used sudo dpkg-reconfigure xserver-xorg and went through the prompt as normal to reset my xorg.conf file. Then, I used 915resolution and changed my 640x480 resolution to a 1280x800 mode. Restarted X, went to the resolution preferences, and I now had the choices of 1280x800, 1240x768, and 800x600. I selected 1280x800, hit apply, and all was well. :)

Thanks everybody for helping me out, have a great evening! ;)

---

