---
title: "ATI Driver install"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by bobu on 2007-07-09
Hello all,

Installed 7.04 - went pretty smooth, on-line now and everything works great. I am new to Ubuntu and any Linux environment, so I am really pleased it went as great as it did. I am now away from that other OS I was using forever. I cam able to do all \most everything I ever wanted to do except install my ATI Radeon 9700 all-in-wonder pro. I was able to download the installer ran it, installed driver and when I go to restricted drivers manager and enable it - when rebooting I get as far a a blank screen, I then have to go into recover mode , edit xorg.conf and replace the driver section with "ati" instead of the "flgrx" to get it to come back. I have read and tried everything I can think of to make it work - no luck. I added the section at the end with Composite disable as well - no luck. Is it maybe a screnn/monitor freq setting, or just missing something somewhere? here's a c/p of the xorg.conf that works  first & the one that doesn't second. 

WORKING

Section "Device"
	Identifier	"ATI Radeon 9700 Pro"
	Driver		"ati"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9700 Pro"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection




NOT WORKING

Section "Device"
	Identifier	"ATI Radeon 9700 Pro"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9700 Pro"
	Monitor		"Generic Monitor"
	Defaultdepth	16
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by atria on 2007-07-09
Downloaded the installer? Are you trying to install the official one from ATI's website?

---

### Post by bobu on 2007-07-09
Iv'e tried the official one and the one in the script when I installed Envy. actually tried several versions, all do the same thing. the last on i tried was through the Synaptic Package Manager and did a search on Radeon - picked the Video driver for ATI graphics accelerators 7.1.0-8.34.8+2.6.20.5-16.29

---

