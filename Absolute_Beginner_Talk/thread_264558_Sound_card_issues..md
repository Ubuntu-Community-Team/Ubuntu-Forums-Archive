---
title: "Sound card issues."
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-09-24
This is roughly my third day in Linux, and my third day on the forums begging for help.

I've finally got my internet up and running (hurray!), I've stopped caring about having a dual monitor setup for now (hurray, I guess), and I've started to get everything sorted out. I only have two major issues now, one much worse than the other.

1. The screen resolution is much lower than I'd like it to be. Everything is way too big! I can handle that, though, but if someone has a link to another thread I'd appreciate it.

Now for the major problem:

2. I installed Linux and booted up in it. My sound set up was working fine. I went back to Windows a few times, back and forth (both systems are on different physical drives entirely, for the record), and all of a sudden whoops! No sound! And I mean *no* sound. Not in Linux, not in Windows, not anywhere! It's not just a driver issue, my PC just refuses to accept the fact that it's got sound capabilities.

If it helps, I'm using a HP Pavilion 7950, and the sound card is part of the motherboard. I don't have a seperate sound card that fits (you'd think I would with three scrap computers in the basement.) Any thoughts?

---

### Post by PriceChild on 2006-09-24
Screen resolution, check the topic below this: [http://ubuntuforums.org/showthread.php?t=264556](http://ubuntuforums.org/showthread.php?t=264556)

For the soundcard, have you made ANY hardware changes... i got stumped a couple of days ago after i reailsed linux was tryign to output sound to my tvtuner cards instead of my graphics card :)

---

### Post by theknave on 2006-09-24
> **PriceChild said:**
> Screen resolution, check the topic below this: [http://ubuntuforums.org/showthread.php?t=264556](http://ubuntuforums.org/showthread.php?t=264556)

For the soundcard, have you made ANY hardware changes... i got stumped a couple of days ago after i reailsed linux was tryign to output sound to my tvtuner cards instead of my graphics card :)

Thank you for the screen bit.

As far as hardware changes go, I've not done anything with my computer at all except for install ubuntu and play with ndiswrapper.

EDIT: Actually, about that screen bit, I would think that this would imply that I would have a lot of resolutions to choose from, when I only have two.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage I/II 215GT [Mach64 GT]"
	Driver		"ati"
	BusID		"PCI:0:15:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage I/II 215GT [Mach64 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by theknave on 2006-09-24
Sorry to bump this, but I'd really like the issue resolved.

---

### Post by CatKiller on 2006-09-25
> **theknave said:**
> EDIT: Actually, about that screen bit, I would think that this would imply that I would have a lot of resolutions to choose from, when I only have two.

Are the HorizSync and VertRefresh values the ones for **your actual** monitor? If not, find out what they should be and change them accordingly. Actually, I've just noticed that you've got the same card as one of mine. Can it even do resolutions that high? It's a bit crappy...

/var/log/Xorg.0.log may point you in the direction of why the higher resolutions aren't being made available.

---

