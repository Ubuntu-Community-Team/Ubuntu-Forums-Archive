---
title: "How to decrease screen resolution?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by d98rolb on 2007-03-03
I have worked with v6.10 a while now with dualboot and I both like and dislike it. The startup and desktop is a bit slower than Win XP. The plan is to leave Windows but it may not be as easy as I think... Anyway in Windows I have 1024x768 85Hz resolution.
Ubuntu give me 1280x1024 and I think this is too high for my Sony Multiscan200ES monitor.
I have an old Nvidia Geforce 2 MX graphic card.
The first thing I tried was to change the resolution from the system menu. 
I could change to 1024x768 but 60 Hz was the only choice.
And it result in "Out of scan range" from the monitor.

I have tried a lot of things but it only results in that the xserver refuse to start.
The spec for the monitor is:

HSync 30 - 70 KHz. Windows use 68,68 KHz

VSync 50 - 120 Hz. Windows use 85 Hz

I also look in the xorg.conf file, here is the interesting part of it:

[FONT="Fixedsys"]Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-114
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Depth		24
		Modes		"2288x2288" "2288x1830" "1280x1024" "1152x921" "1024x768" "832x624" "800x640" "800x600" "767x2784" "720x400" "640x480" "255x2610"
	EndSubSection
EndSection[/FONT]

In theory it should be simple, just change the monitors limits, but the sxerver won't start then so I have to restore from the backup in the console. I have also tried things like

[FONT="Fixedsys"]sudo dpkg-reconfigure xserver-xorg[/FONT]

without result.

Regards Roland

---

### Post by Scorpuk on 2007-03-03
Before trying this please make a backup copy of your xorg.conf file :-)


Change the following line

```
Modes "2288x2288" "2288x1830" "1280x1024" "1152x921" "1024x768" "832x624" "800x640" "800x600" "767x2784" "720x400" "640x480" "255x2610"
```

to 

```
Modes "1024x768" "800x600" "640x480"
```

and see what happens after a reboot.

---

### Post by d98rolb on 2007-03-11
Det fungerar bra nu med 1024x768 75Hz. Jag undrar dock lite om det går att höja till 85 Hz som i Windows.

---

