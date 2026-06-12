---
title: "Native Resolution Not an Option and 2nd Screen is only Mirroring"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by GeigerBC on 2007-06-30
Since I have a feeling these two problems are related, I'll post them together.  I'm running Feisty Fawn Live CD.

I've got two screen, currently the second one is only a mirror of the first.  I'd like to change that and make the desktop quite wide (similar to how it works in WinXP by dragging screens over and then maximizing them in that screen).  How do I enable to the second screen?

The other problem is under System>Preferences>Screen Resolution I don't have an option for 1280x1020 which is what I use for both screens.  My largest option is 1024x768 at 60Hz refresh rate.  The refresh rate is correct,  How do I get the 1280x1020 resolution to be an option for both screens?

Any help would be appreciated.

---

### Post by alienexplorers on 2007-06-30
You could try adding a modeline line to your "monitor" section of xorg.conf.  A modeline for 1280x1020 at 60hz would be:

> # 1280x1020 @ 60.00 Hz (GTF) hsync: 63.36 kHz; pclk: 108.47 MHz
  Modeline "1280x1020_60.00"  108.47  1280 1360 1496 1712  1020 1021 1024 1056  -HSync +Vsync

---

### Post by GeigerBC on 2007-06-30
Could you direct me to where 'xorg.conf' is located?  Running it in the terminal didn't bring anything up.
Edit - Found this command line to bring up xorg.conf.
> gksudo gedit /etc/X11/xorg.conf

Where exactly would the code you suggested go?  Here is the section of xorg.conf that I think it could be inserted into.

> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
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

I currently have it added right after "Identifier "Generic Monitor"" but it didn't do anything.

---

### Post by alienexplorers on 2007-06-30
It would be put in your monitor section like:

> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
Modeline "1280x1020_60.00" 108.47 1280 1360 1496 1712 1020 1021 1024 1056 -HSync +Vsync
EndSection

---

### Post by GeigerBC on 2007-06-30
I put that in there and hit save, then closed it.  System>Preferances>Screen Resolution still only showed the sizes that were there before.

Thanks again so far.

---

### Post by alienexplorers on 2007-06-30
Sorry I could not help.

---

