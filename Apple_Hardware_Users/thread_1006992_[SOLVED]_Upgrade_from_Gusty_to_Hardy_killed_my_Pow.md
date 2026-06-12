---
title: "[SOLVED] Upgrade from Gusty to Hardy killed my Powerbook G4"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by mattppcintel on 2008-12-09
I had Gusty up and running fine on a Powerbook G4 Ti (550mhz radeon, 512meg) when for some reason I decided to upgrade to Hardy.  The upgrade seemed to go fine but after it finished and I rebooted I cannot get it to load X.  No matter what I do to the xorg.conf file I always get the following:

(EE)RADEON(0): No valid modes. 
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found

I've tried using "dpkg-reconfigure -phigh xserver-xorg" but get the same error trying to start x from the resulting config file.

Does hardy not work on this hardware?  Is something other than the xorg.conf file messed up that I can fix?  Can I revert back to Gusty easily?  I can't get the cd to load anymore (possible bad cd rom drive) so reinstalling does not seem to be an option.

Please help!  This is killing me!

---

### Post by stream303 on 2008-12-10
Downgrading is nearly impossible.  And that dpkg-reconfigure utility has been deprecated, although it still appears in the xorg.conf file as a way to reconfigure - which won't do it in Hardy+.

You might want to take a look at stmillers xorg.conf - perhaps that will be enough to get you back up and running:

[http://ubuntuforums.org/showthread.php?p=2483422#post2483422](http://ubuntuforums.org/showthread.php?p=2483422#post2483422)

---

### Post by mattppcintel on 2008-12-10
So if dpkg-reconfigure is deprecated what can I use to try to automatically reconfigure my xorg.conf file?

---

### Post by mattppcintel on 2008-12-10
> **stream303 said:**
> 
You might want to take a look at stmillers xorg.conf - perhaps that will be enough to get you back up and running:

[http://ubuntuforums.org/showthread.php?p=2483422#post2483422](http://ubuntuforums.org/showthread.php?p=2483422#post2483422)

I tried the changes suggested to no avail.  That got x to "start" but it was completely unusable (The screen started some color then faded gradually with a wide range of colors to mostly black with some colors around the edges).  

It did detect the screen which is an improvement.  I was able to use single mode to get it back to where it was.  I'm trying some mods to the xorg.conf to get it to a usable state.

---

### Post by mattppcintel on 2008-12-10
It's fixed!

I had some help on this but it turns out that if driver specified in the xorg.conf file doesn't work the system defaults to t vesa driver.  Problem is that driver doesn't work either.  According to the following bug you need to use the "fbdev" driver.  Substitute that in for "ati" or "radeon" or whatever you have, make a few other minor changes, and it's fixed.  For clarity here are the specs of this machine so that if anyone with identical hardware has the problem they can use this solution.

Model: Apple PowerBook II G4 Titanium 550MHZ
Video: ATI Technologies Inc Radeon Mobility M6
RAM:   512 MB

Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/155685](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/155685)

New xorg.conf video setup section:
Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11"
	Driver		"fbdev"
	BusID		"PCI:0:16:0"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x768@60"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768@60"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768@60"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768@60"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x768@60"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768@60"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by mkvnmtr on 2008-12-10
Thanks for posting back how you got that to work. That will really help the next guy to come along with that hardware.

---

### Post by milkwood on 2008-12-11
This is mine
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection
```

I think xorg.conf was very complicated before.
But It had been very simplified on my using hardy.
I don't know that's why though.
Anyway I think this thread is significant:p.

---

### Post by mattppcintel on 2008-12-11
Milkwood, what hardware are you running on?  I may try that configuration later to see if it works.  To me it looks like the option "useFBDev" should cure the problem as well, and it's a lot simpler than my config.

---

