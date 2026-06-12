---
title: "Can't set my resolution to 1280x960"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Royle on 2007-07-01
I've been trying to set my resolution to 1280x960, it wasn't in the Screen Resolutions in the Preferences, so I tried adding it in xorg.conf .  That didn't work or let me choose it in gnome.  I then tried deleting all other resolutions for 24 bit, and that changed my resolution to 1280x1024, which is not quite what I want.  Does anyone know what I can do to change this?  Any help is appreciated.

part of my xorg.conf
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
	EndSubSection
EndSection

```

---

### Post by overdrank on 2007-07-01
Hi you might try and set you default depth to 16, I have seen threads that it has helped in. 
And remember that any changes that you make could crash your xorg. Good luck :KS

---

### Post by mig5 on 2007-07-01
Make sure that 1280x960 is the first resolution in the list and then add the others afterwards.  That should make Ubuntu use 1280x960 as the default.
Like you have in 16 depth:
Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"

Remember that you have to restart X to see the changes, do ctrl+alt+backspace .

---

### Post by Royle on 2007-07-01
I have Modes "1280x960" "1152x864" "1024x768" "800x600" "640x480" for all depths now, and I tried change the depth to 16 and restarting x, changing the depth to 16 causes my monitor to have no input, and I still can not select 1280x960 as my resolution.

---

