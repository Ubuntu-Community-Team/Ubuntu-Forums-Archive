---
title: "screen resolution stuck at 640 x 480."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by modulistic_terror on 2007-02-03
i dont know what happened  i just switched on the computer and blam the bars at top and bottom of the screen are huge and i can barely see half the content of web pages (due to such a small resolution). i have been to system> preferences>screen resolution but the drop down menus dont work.

any idea what could be causing this?

---

### Post by modulistic_terror on 2007-02-03
i used the "sudo gedit /etc/X11/xorg.conf" command i found in another forum and this is the info i was given.

Section "Monitor"
	Identifier	"C5DZ"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade/i1"
	Monitor		"C5DZ"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

---

