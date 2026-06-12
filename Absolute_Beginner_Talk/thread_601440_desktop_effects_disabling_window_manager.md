---
title: "desktop effects disabling window manager"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by mookie_jones on 2007-11-03
I think this is whats happeneing, I have a toshiba p25 s509 laptop with a nvidia geo force 5200 card

when i enable desktop effects, it is disabling the window manager..


how can i fix this?

---

### Post by overdrank on 2007-11-03
> **mookie_jones said:**
> I think this is whats happeneing, I have a toshiba p25 s509 laptop with a nvidia geo force 5200 card

when i enable desktop effects, it is disabling the window manager..


how can i fix this?

Hi, I am assuming that you have enabled the restricted driver for you graphics card. You may try and add these to you xorg 
 Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
Under the section device. To edit your xorg use this command 
```
gksudo gedit /etc/X11/xorg.conf
``` Hope this helps. Good luck!

---

### Post by mookie_jones on 2007-11-03
just checked and those are already in there


Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1680	1050

---

### Post by overdrank on 2007-11-03
> **mookie_jones said:**
> just checked and those are already in there


Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1680	1050

Ok do you have emerald installed? You can try alt,F2 and use ```
emerald -- replace
```

---

### Post by mookie_jones on 2007-11-03
ok heres where i stand right now

i am getting some features to work but its not through cssm, its throught the gnome compiz. when i try to change settings for the advanced settings manager, it chokes and does nothing.



when i reboot, im placed back to a 1280 * whatever instead of 1600 * 900 too

---

### Post by overdrank on 2007-11-03
> **mookie_jones said:**
> ok heres where i stand right now

i am getting some features to work but its not through cssm, its throught the gnome compiz. when i try to change settings for the advanced settings manager, it chokes and does nothing.



when i reboot, im placed back to a 1280 * whatever instead of 1600 * 900 too

Ok do you know how much memory is being shared with graphics? You adjust this in some laptops.

---

### Post by mookie_jones on 2007-11-03
i dont know that its shared memory


GeForce FX Go5200 (GPU 0)

---

### Post by overdrank on 2007-11-03
> **mookie_jones said:**
> i dont know that its shared memory


GeForce FX Go5200 (GPU 0)

Ok from what I have found online for the specs is that the max resolution is 1400x 900. And the memory dedicated to the graphics is 32mb. This may not be the exactly your specs but if they are then you may be limited in what resolution and the amount of desktop effects the system can handle.

---

### Post by mookie_jones on 2007-11-03
thats what im working with right now but how can i find out why my advanced effects dont work

---

### Post by overdrank on 2007-11-03
> **mookie_jones said:**
> thats what im working with right now but how can i find out why my advanced effects dont work

Ok this is what I would do. Set my resolution at the 1400x 900 and with the desktop effects turn off, open up CCSM and turn everything to the bare and then add one effect at a time until it crashed then you know how far you can go. :)

---

### Post by mookie_jones on 2007-11-03
ok, 

ive now done that with 2 results

1. I cant use select menu-system-preferences-compizsetting

I have to go to appearance and select advanced.


2. I dont have anything x's or minimization available with my windows

---

