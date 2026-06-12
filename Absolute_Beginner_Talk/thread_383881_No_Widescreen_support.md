---
title: "No Widescreen support"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by evilbanana on 2007-03-13
Brand new Linux newb right here. I've been trying to get started with linux for a few days and the one big problem that keeps returning is resolution. I have a widescreen 1440x900 monitor and I can't get it to work in native resolution. 

I immediately jumped online and found many threads on these forums but I couldn't find any that helped (and one pretty much destroyed the os.. had to reinstall). Here's what I got:

Video card: Nvidia 6600 GT 
Monitor: Hanns-G JW199D 19-inch monitor operating on 1440x900.

Here's my xorg.conf file: 

```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
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

```

Any help on what to do? Thanks!

---

### Post by pettybone on 2007-03-13
Try this thread. I just fixed my resolution with it. It was easy. You'll get an error after you run the install but just reboot your computer.[http://www.ubuntuforums.org/showthread.php?t=344460]("http://www.ubuntuforums.org/showthread.php?t=344460")

---

### Post by strikeback03 on 2007-03-13
you will probably want to install the nVidia driver, Alberto Milone's page has a good guide.

---

### Post by evilbanana on 2007-03-13
There is no link in your message but I think I know what you're talking about (I saw your thread you posted not that long ago). I think it worked for you because that download installed something to do with Intel graphics (ie. your Inspiron runs on Intel GMA) but I have Nvidia graphics. 

...but, unless anyone has anything better I might just try it. After all, what's the worst that could happen... :)

Thanks for the reply

---

### Post by evilbanana on 2007-03-13
Thanks Strikeback03, I'll go check that out.

---

### Post by evilbanana on 2007-03-13
I tried that Strikeback03 but still no success. Well... it did have 1 effect. Now when scrolling down a webpage in Firefox it is all boxy and slow. It's a bit disorienting... :(

---

### Post by theswan on 2007-03-22
hi all!
i have the same problem as evilbanana. :-(
im using a toshiba m40 laptop, 15.4" LCD, and the display is inappropriate right now. i tried to install latest graphic drivers but still the problem. i hope there is a solution to this,..please update me if im missing something here...

btw, my xorg.conf is similar to evilbanana as well..at least the three sets of resolutions..

---

