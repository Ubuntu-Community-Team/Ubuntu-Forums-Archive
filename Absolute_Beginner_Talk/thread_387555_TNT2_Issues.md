---
title: "TNT2 Issues"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-03-18
EDIT::
Well guys, I have resolved the problem I detailed below, I canged nvidia back to nv, left the res. changes the same and it worked fine first time. Inexplicable, but these things happen.
Il

Original Problem::
Have been trying to get a 1024x768 resolution out of an old TNT2 box which I have been running Xubuntu very hapily on at 1024x768. When I installed Ubuntu however I only can get 800x600 out of it - something which is fairly odd to be honest. Anyway, with a bit of forum searching I got onto this:
[http://ubuntuforums.org/showthread.php?t=376481](http://ubuntuforums.org/showthread.php?t=376481)
And made some alterations to the xorg.conf following the install of the nvidia-glx-legacy driver.

On my main Ubuntu box I have to use fglrx as I have an ATI so this one is a new puzzle I havent had to deal with before. Anyway the method posted above led to:
Resulting in a xorg.conf which looks like this (the relevant sections)
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"AOC Spectrum"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
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
However, when rebooting (the first few attempts resulted in an unusable xorg.conf which led to repeated crashing of the xserver) now, it works fine, but still the only available resolution is 800x600 and on the GUI resolution change, the highest available is 800x600.

Any ideas what is wrong and how to make it work?
Il

---

### Post by Dakiraun on 2007-05-28
I ran into the same issue when turning on the Restricted Drivers for an older box running Xubuntu Feisty at work.  All I needed to do was edit the xorg.conf and add the specific horizontal and vertical display rate capabilities of the monitor attached to it, for example:

Before
```
Section "Monitor"
        Identifier      "StudioWorks"
        Option          "DPMS"
EndSection
```

After
```
Section "Monitor"
        Identifier      "StudioWorks"
        Option          "DPMS"
        VendorName      "LG"
        ModelName       "StudioWorks 775N"
        HorizSync 30 - 70
        VertRefresh 50 - 160
EndSection
```

Once you find your monitor's specs and edit xorg.conf, logout of your X session, then hit **Ctrl+Alt+F2** at the login screen to drop to CLI.  Then just login and restart the Xserver with "**sudo /etc/init.d/gdm restart**" and it should come back up using the new monitor settings. :)

---

