---
title: "book dualusb g3 Screen resolution"
date: 2007-05-22
forum: Apple PPC Users
---

### Post by rogue6 on 2007-05-22
I just installed feisty on my ibook dualusb g3 but i can't stand the 800 x600 resolution
I am a complete linux noobee but i tried out ubuntu a few releases back and was able to modify my xorg.conf
to get better resolutions but can't seem to get it to work now without xserver failing on boot
Can someone help me to get it up to 1024
I've tried several different combinations with my xorg.conf
Can some post there xorg.conf witha working 1024 res.

Thanx

---

### Post by stmiller on 2007-05-22
What is your xorg.conf? Can you post it here? Did you try using 16bit rather than 24bit?

---

### Post by rogue6 on 2007-05-22
Yes i tried 16 bit it didn't work

here's my xorg.conf monitor screen section


Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Color LCD"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by rogue6 on 2007-05-23
Well i figured it out on my own i reconfigured my xserver and chose the 1024x728 in resolutions and it works

sudo dpkg-reconfigure xserver-xorg

---

### Post by saracen on 2007-05-24
can you post your new xorg.conf file?  I tried running dpkg-reconfigure xserver-xorg and when I was done I was stuck in 640x480 :(

---

### Post by rogue6 on 2007-05-24
Hope it works for you Here's my xorg.conf on feisty.


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Thecnologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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

