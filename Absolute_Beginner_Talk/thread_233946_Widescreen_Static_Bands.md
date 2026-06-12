---
title: "Widescreen Static Bands"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by niallabrown on 2006-08-10
[SIZE="3"]**I have managed to get Ubuntu to recognise the 1680X1050 resolution of my monitor by editing /etc/X11/xorg.conf**[/SIZE]
[B]
[COLOR="DarkRed"][SIZE="4"]But now I get stacic bands across a portion of the screen shown below:[/SIZE][/COLOR][/B]

How do I fix that?

[IMG]http://www.deafblindresources.org/screen.jpg[/IMG]
[IMG]http://www.deafblindresources.org/screentwo.jpg[/IMG]

[SIZE="4"][COLOR="DarkRed"]The monitor is an:[/COLOR][/SIZE]
Acer AL2032WA 20" Wide-screen

[COLOR="DarkRed"][SIZE="4"]
The following is my current xorg.conf:[/SIZE][/COLOR]


```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer MFM DVI"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"Acer MFM DVI"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x800"
	EndSubSection
EndSection
```


Thanks!:KS

---

### Post by dbw on 2006-08-21
Do you see the static in GDM?  If not, it might be an issue w/ your window manager.  Also, try using [using a custom modeline]("https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration") in your /etc/X11/xorg.conf.

---

### Post by niallabrown on 2006-08-21
Im not sure what a Static GDM is.

I did make the modline with no troubble but it had no effect on the banding but after a coupple of tries it kicked me in to another resoltion that is not the native but displays very well, so I think I will just stay with this one.  Thanks for your help.

---

### Post by dbw on 2006-08-22
Sorry, I meant: do you see the bands when you turn on the computer (in the login manager which is called GDM)

---

### Post by niallabrown on 2006-08-22
It shows the banding during the Ubuntu Login Screen but not during the part where it's loading the system and has the progress bar.

The monitor works on windows using the ATI control panel, however I have not had any luck finding how to get or install the proprietary driver for ATI on Linux that was suggested to me.

---

### Post by dbw on 2006-08-23
Yeah, definately sounds like an X problem - those bootup screens are before X even starts.

You note that you have tried custom modelines, but I don't see any in the xorg.conf that you posted.

In terms of installing ATI's driver, have you tried [this]("http://www.ubuntuforums.org/showthread.php?t=235145&highlight=ati+driver") or the flgrx package in synaptic?

  good luck.

---

