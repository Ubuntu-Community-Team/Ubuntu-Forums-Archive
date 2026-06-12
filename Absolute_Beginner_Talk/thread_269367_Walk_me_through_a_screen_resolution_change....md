---
title: "Walk me through a screen resolution change..."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by FreakinSyco on 2006-10-01
Its seems a common problem and I've searched and tried everything Ive read to no avail.

Heres the contents of my xorg.conf:

```

Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JK [Radeon X800]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
	HorizSync	83
	VertRefresh	75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R420 JK [Radeon X800]"
	Monitor		"DELL 2005FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "800x600" "640x480"
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

Section "DRI"
	Mode	0666

```

After saving I have rebooted: still had no other option than 640x480, tried the ctrl+alt+backspace then ctrl+alt+ "-" or "+": nothing happened no new options.

I had the same issues under kubuntu but it was an easy solution I had to manually identify my monitor and its resolution in the systems settings then log out and restart X (a nice easy button to click in kubuntu).

Ive also tried: sudo dpkg-reconfigure xserver-xorg
Ive gone through and specified my resolutions and STILL they are not available.

What am I missing?

---

### Post by bulldog on 2006-10-01
Take a walk at the beginners page and see how many topic's have the same issue.

Maybe you can read them first??

---

### Post by FreakinSyco on 2006-10-01
Ive been reading for hours. Ive tried everything Ive read to no avail. If its obivous what I'm missing please point me in the right direction.

---

### Post by Fass on 2006-10-01
Tried the fglrx drivers? I've never had any luck with ati or radeon...

---

### Post by FreakinSyco on 2006-10-01
> **Fass said:**
> Tried the fglrx drivers? I've never had any luck with ati or radeon...

That did it. Thanks.

---

### Post by mips on 2006-10-01
> **FreakinSyco said:**
> Ive been reading for hours. Ive tried everything Ive read to no avail. If its obivous what I'm missing please point me in the right direction.

If only you used the search function and looked for **Dell 2005FPW** the answer would have jumped out at you several times.

[http://www.ubuntuforums.org/showthread.php?t=246891](http://www.ubuntuforums.org/showthread.php?t=246891)  Post #3

---

### Post by FreakinSyco on 2006-10-03
> **mips said:**
> If only you used the search function and looked for **Dell 2005FPW** the answer would have jumped out at you several times.

[http://www.ubuntuforums.org/showthread.php?t=246891](http://www.ubuntuforums.org/showthread.php?t=246891)  Post #3

Cool but I have an ATI card. I got it figured out thou. And just by installing the fglrx drivers it jumped to the correct resolution.

---

