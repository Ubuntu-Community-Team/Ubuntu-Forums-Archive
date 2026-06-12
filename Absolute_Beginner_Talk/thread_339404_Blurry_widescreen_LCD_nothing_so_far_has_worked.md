---
title: "Blurry widescreen LCD nothing so far has worked"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by mandlebaum on 2007-01-15
I have a Philips 190CW 19 inch widescreen monitor whose native resolution is 1440x900@60Hz, I was able to get it set to this by adding a special modeline, but throughout the past 4 days I haven't been able to get rid of a blur.  The left side of the screen has blur lines running down it, all the fonts are blurry, and the edge of every window looks like a blurred duplicate of itself running to the right.  It's alot like double vision.  I have an Nvidia Geforce 7300 LE video card if that helps.  The auto-adjust button on the lcd doesn't fix anything.  I tried adjusting the phase and clock settings of the lcd monitor and that didn't do anything either.  None of this happens on a CRT monitor, or when the LCD is used on a Windows machine.  Here is the section of my xorg.conf that seems to have something to do with this:

> Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
        Option          "ModeValidation" "NoEdidDFPMaxSizeCheck"
EndSection

Section "Monitor"
	Identifier	"Philips 190C"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	55-75
        Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
        Modeline "1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
        DisplaySize 1440 900
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Philips 190C"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_60.00"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00""1440x900_70.00"
	EndSubSection
EndSection

Thanks

---

### Post by Ixat on 2007-04-12
Hey i have the same wide screen lcd monitor which also took me ages to figure out. I checked your mode line against mine and yours seems to be just that bit different. please try this modeline instead and see how you go!

Modeline      "1152x870" 106.5 1440 1520 1672 1904 900 903 909 934

---

