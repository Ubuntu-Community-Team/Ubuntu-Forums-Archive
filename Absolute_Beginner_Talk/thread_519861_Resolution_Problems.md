---
title: "Resolution Problems"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by yamyogurt on 2007-08-07
I have been having Resolution problems from installation of Feisty. I have gone through almost all the guide to reseting and editing and xorg.conf and nothing works, so I am posting  the monitor/screen section of my xorg.conf hopefully someone will be able to see whats wrong. I have an integrated Geforce 2 and my monitors max resolution is 1024X768. 

> 
Section "Monitor"
	Identifier	"e15t4"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"e15t4"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

I know there is something wrong here. Most of the time when I edit my xorg.conf it boots me up into the console and I have to restore the backup.

---

### Post by Rocket2DMn on 2007-08-07
Manually editing xorg.conf rarely works, have you tried the reconfiguration of the Xserver?
The following command will take you through a setup process which asks you questions about your hardware.  You should read it, not just ENTER your way through in a hurry.
```
sudo dpkg-reconfigure xserver-xorg
```Use TAB to move around and SPACEBAR to select/enable when appropriate.
On the screen resolutions page, enabled your monitor's highest resolution and everything less.  After the configuration is complete, you need to restart X with CTRL+ALT+BACKSPACE (make you save everything first).
Now you should be able to select your max resolution from System->Preferences->Screen Resolution

---

### Post by yamyogurt on 2007-08-07
Wow that worked perfectly I did that a few times before but I just took it for granted I just needed someone to tell me to actually do it all the way through. :guitar:

---

