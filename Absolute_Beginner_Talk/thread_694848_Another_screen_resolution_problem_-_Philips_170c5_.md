---
title: "Another screen resolution problem - Philips 170c5 / Cirrus Logic 5465"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by proedras on 2008-02-12
Greetings, everyone.

I have Xubuntu installed on a Pentium II. Everything works fine, except the screen resolution, which can't be more than 800x600. On the same hardware, in Win98SE I had 1024x768 16bit and worked OK.

So, first I tried to fix this through the menu Settings/Screen and graphics

I see the graphics card (Cirrus Logic 5465) and monitor (Philips 170c5) on the menu, I tried a thousand times of configuring, logged out but no use.

I even tried the terminal Xorg configuration, as shown in other posts, I used everything but nothing changed. I've tried several different values that I found online, about the horizontal/vertical scan, the refresh rate etc but I can't get it done. I found online that the card has a 4mb memory, so I put 4096 when prompted.

Here comes my Xorg:

[I]Section "Device"
	Identifier	"Cirrus Logic GD 5465 [Laguna]"
	Driver		"cirrus"
	BusID		"PCI:1:0:0"
	VideoRam	4096
EndSection

Section "Monitor"
	Identifier	"Philips 170c5 (17 inch)"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Cirrus Logic GD 5465 [Laguna]"
	Monitor		"Philips 170c5"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1024x768@72"
	EndSubSection
EndSection[/I]

Any suggestions welcome. I believe that anyone with the same hardware could help me fix that problem.
Thank you.

---

