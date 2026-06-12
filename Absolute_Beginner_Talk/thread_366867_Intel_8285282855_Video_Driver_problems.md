---
title: "Intel 82852/82855 Video Driver problems"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by dtm on 2007-02-21
Hi,

I am attempting to get Ubuntu working on what is quite possibly the worst laptop ever.

It has an Intel 82852/82855 integrated video card and for the life of me I can't get it to display over 800x600.  I have tried installing the video drivers listed on Intel's linux site, the included intel package, and a package for i915.

I have tried messing with my xorg.conf and switching between i810, vesa and other drivers (none of which work) and still 800x600.

Below are the relevant sections of my xorg.conf as on now:
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by NewOldTimer on 2007-02-21
check this out....[http://ubuntuforums.org/showthread.php?t=351647....hope](http://ubuntuforums.org/showthread.php?t=351647....hope) it helps

---

