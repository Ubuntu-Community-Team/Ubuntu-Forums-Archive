---
title: "Display resolution options not present"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by nicom on 2007-03-05
I have recently installed Xubuntu on my PII  350MHz machine but am only offered the following screen resolutions, 
   Default
   800x600@60
   800x600@56
   640x480@60
As a result the display is quite distorted on my 17" monitor. My xorg.conf seems to have the right resolutions listed.

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Texas Instruments TVP4020 [Permedia 2]"
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
```

I have tried reconfiguring with 
```
sudo dpkg-reconfigure xserver-org
```
to which I got the reply 
```
Package 'xserver-org' is not installed and no info is available
```

The installation is not standard in that Xubuntu is loaded on hdb2. The other partitions hda1 and hda2 are used for different versions of Puppy, hda3 is for my grub boot. Both Puppy installations work well and Xorg is easily configured with Puppy's Xorgwizard.

Any ideas?

---

### Post by renzokuken on 2007-03-05
the code should actually be

```
sudo dpkg-reconfigure xserver-[color=red]x[/color]org
```

notice the x on the end.

what grafix card/chipset do you have and what driver is your xorg using for it?

---

### Post by nicom on 2007-03-05
Ah, my spelling lets me down once again. I think I wrote it down on paper incorrectly when I found the command in the forum. I will try the correct code tonight when I'm back at the machine.

The video card is an AccelGraphics Permedia 2 AGP 8MB. The machine is a Gateway - not sure of the model.

---

### Post by nicom on 2007-03-06
Success, but not through the use of reconfigure xserver-xorg. I tried that first but was unable to find a suitable driver for the video card. Both Puppy and Xubuntu identify it as glint.

What I did to solve it was compare the xorg.conf files for Puppy and Xubuntu. I noticed that the refresh and sync rates were different so I copied the Puppy values over to the Xubuntu file and I now have good graphics.

Thanks for your help.

---

