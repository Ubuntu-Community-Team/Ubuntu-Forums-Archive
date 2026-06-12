---
title: "How to alter my Refresh Rate"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by jas992 on 2007-01-03
Hi,

How do I change my monitors refresh rate? I have tried numerous approaches using the GUI but I am disallowed to increase it above 85Hz on 1024x768 when I know my monitor can run @ 100Hz on that resolution (as it did so in Windows XP). Is there a way to effect this change through the terminal?

Any information would be greatly appreciated.

Yours truly,
jas992.

---

### Post by viciouslime on 2007-01-03
You could edit your xorg.conf directly. Run "sudo gedit /etc/X11/xorg.conf" if you break it though, you won't be able to get back into a gui until you fix it at the command line. So back it up first "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak" that way you can always use the command line to just copy the file back to /etc/X11/xorg.conf and et your gui back.

If you want to know hat you'll have to change in the xorg.conf file post it here (jut copy and paste its contents) and I will try and help you :)

---

### Post by jas992 on 2007-01-03
Section "Monitor"
	Identifier	"Philips 109S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce4 Ti4200"
	Monitor		"Philips 109S"
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

---

### Post by viciouslime on 2007-01-03
Ok, this thread should be able to help you [http://www.ubuntuforums.org/showthread.php?t=83973]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

