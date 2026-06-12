---
title: "Clarification of Prob (I Hope)"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-03-15
A clarification of my problem ( I hope).

I have a 19” monitor. It's spec is:

Horizontal scan range 			30 kHz to 96 kHz
Vertical scan range (Refresh rate) 	48 Hz to 120 Hz
Optimal preset resolution 		1024 x 768 at 75 Hz or 85 Hz
Highest preset resolution 		1600 x 1200 at 75 Hz
Highest capable resolution 		1600 x 1200 at 75 Hz

The Dapper screen pref gui default res is 1280 x 1024. This looks most appropriate  and i can't alter it to lower resolution in the dropdown. The same applet claims my refresh rate is 86 Hz and likewise i cannot change it, -but my screen looks like 60 Hz, which is the reading my monitor displays when i press a button on the cabinet. This is too low and it trails smears when i move windows.

I can lower the the resolution by deleting the 1st settings ( 1280 x 1024  ) from each modes line in the /etc/X11/xorg.conf but i'm sure these are less appropriate settings. Here is the relevant sections from my /etc/X11/xorg.conf

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ULTRASCANP99"
	Option		"DPMS"
	HorizSync 30-96
	VertRefresh 48-120
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

---

### Post by benfindlay on 2007-03-15
have you tried typing ```
sudo dpkg-reconfigure xserver-xorg
``` and re-setting up your monitor resolutions in there?

I would recommend doing this, and choosing "Medium" option when you get there. This will allow you to specify a range of resolutions you would like the monitor to work on, and then pick your optimum resolution and refresh rate!

Hope this helps!

---

### Post by John.Michael.Kane on 2007-03-15
what video card are you using ?

If it's nvidia read the link below.

Make sure you have your CRT/LCD manual.
[**Adjust refresh rate**]("http://ubuntuforums.org/showpost.php?p=1691257&postcount=2")

If you need to setup your ati drivers look here:
[**Ati Ubuntu_Dapper_Installation_Guide**]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

---

### Post by nnjond on 2007-03-15
My pc is new, my monitor is a  trinitron crt.  Don't know anything about video cards. My monitor is fine in Windows.

---

