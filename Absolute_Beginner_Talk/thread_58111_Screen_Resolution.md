---
title: "Screen Resolution"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-08-18
I have finally set up my internet, but now I cannot change the screen resolution.  It is stuck on the minimum, and when I go to change it I only get one option (which happens to be the same as my current configuration).  When running Windows, my monitor works fine on 1024x768 with an 85 refresh, so I know it isn't a problem with my monitor.  Is there any way I can change this?

Thanks for your help.

---

### Post by aysiu on 2005-08-18
This may help you:

[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+screen+resolution+horizsync+vertrefresh+%2Fetc%2FX11%2Fxorg.conf&btnG=Google+Search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+screen+resolution+horizsync+vertrefresh+%2Fetc%2FX11%2Fxorg.conf&btnG=Google+Search)

---

### Post by amcavoy on 2005-08-18
Alright I have opened up the file in Gedit, but I'm not sure what to do from here.

[i]Section "Monitor"
	Identifier	"MX75"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"MX75"
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
EndSection[/i]

What should I edit?  I would like to use 1024x768 with a refresh rate of 80 or 85.

Thanks again.

---

### Post by aysiu on 2005-08-18
[QUOTE=apmcavoy]
[i]Section "Monitor"
	Identifier	"MX75"
	Option		"DPMS"
EndSection[/i]
[/QUOTE]

See this part? You have to find the proper vertical and refresh ranges for your monitor.

This is what mine looks like:
[i]
Section "Monitor"
Identifier "VG150"
HorizSync 30-62
VertRefresh 50-70
Option "DPMS"
EndSection[/i]

I found that 30-62 and 50-70 thing on my monitor manufacturer's website.

---

### Post by amcavoy on 2005-08-18
Alright, I found that and entered it in.  I just clicked "save" on Gedit.  Is there anything else I should do?  When I go to SYSTEM->PREFERENCES->SCREEN RESOLUTION, it still isn't allowing me to change the resolution.

---

### Post by xmastree on 2005-08-18
You'll probably need to restart the xserver for the changes to take effect.
Ctrl-Alt-Backspace is the easy way, but make sure you've saved anything you're working on first...

---

### Post by amcavoy on 2005-08-19
Thank you both very much.  It worked great.

---

