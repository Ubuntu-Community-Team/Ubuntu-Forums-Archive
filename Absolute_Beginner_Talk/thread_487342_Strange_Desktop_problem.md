---
title: "Strange Desktop problem"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by flippo0784 on 2007-06-28
I have Ubuntu 7.0.4, and have gotten 2 different distros (Xmission and Uni of Georgia) and when I use the live cd there is a black bar about a quarter inch thick pushing the desktop to the right, making it hard to use Ubuntu comfortably. The same thing happened with Ubuntu 6. I have a Dell 17 inch flat screen monitor from around 2004, and it doesn't do the same thing for Windows..I'm wondering if it's a problem with monitor or something else. I can't seem to change the screen resolution in Linux. Any help greatly appreciated.

---

### Post by farmera2005 on 2007-06-29
What kind of video card are you using.

Its possible that your computer and Ubuntu don't get along without drivers.

---

### Post by flippo0784 on 2007-06-29
I have an Nvidia GeForce Ti4200

---

### Post by NeoLithium on 2007-06-29
You may just need to install the NVIDIA drivers for your computer. There's a link right here: 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04)

That should get you up and running nicely :)

---

### Post by flippo0784 on 2007-06-29
Thanks a lot for the help guys

---

### Post by phr0ze on 2007-06-29
You have a CRT I assume? Either way, monitors remember their 'positions' based on resolution and refresh rates. You need to edit xorg.conf and put in all the correct info. paste below in a terminal to edit xorg.
```
gksudo gedit /etc/X11/xorg.conf
```

Then find the monitor section and make sure it have a horiz and vertrefresh lines like these below...
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-92
	Vertrefresh	50-85
EndSection

```

Then look up your monitor model on google and find the real refresh rates for your monitor and update the numbers above.

Finally, in the section below add the highest resolution to the 24bit line. Such as:
```
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"
	EndSubSection

```

Hit save and restart or press ctrl-alt-backspace.

---

