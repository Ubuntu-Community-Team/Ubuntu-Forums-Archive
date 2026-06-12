---
title: "Touchpad doesn't work on cold boot"
date: 2009-04-06
forum: Apple Hardware Users
---

### Post by GF_Sobriquet on 2009-04-06
Hello everyone. I recently installed Jaunty on my Macbook Pro 1,1, and pretty much everything has gone very well so far. However, I am running into an issue with my touchpad. It works normally after a restart, but it does nothing on a cold boot. If I cold boot and then restart, everything works fine.

It may also be worth noting that the mouse doesn't work even at the login screen, but if I constantly move my finger on it while booting it will wiggle a bit when there is just a cursor on the black screen. Any suggestions? Thanks in advance to anyone who takes time to read this!

xorg.conf:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig" 		"true"
EndSection
```

/etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
synaptics
```

I also have syndaemon run on startup so the touchpad turns off while I type.

---

### Post by Unix-Man on 2009-04-07
I'm no expert, but i think your computer might not load the driver when you cold boot because something might have been damaged or corrupted on your Install CD.

Causing the driver only to launch on a restart after a cold boot. 

You should try a cold boot, then log out, then log back in and see if this fixes it. Im sure you can do all this with only the keyboard just hit the power button and use the arrow keys to navigate to the logout button and hit Return. 

let me know what you get, like i said Im no expert on these thing's and this could be completely absurd.

---

### Post by cyberdork33 on 2009-04-07
after a coldd boot, try to modprobe appletouch

---

### Post by GF_Sobriquet on 2009-04-07
I seem to have fixed this by removing the "Touchpad" application from my Startup Applications. Unfortunately this means I have to reset the acceleration/speed settings after every restart.

I'm going to keep playing around with some of this stuff, thanks for the suggestions.

---

### Post by cyberdork33 on 2009-04-08
> **GF_Sobriquet said:**
> I seem to have fixed this by removing the "Touchpad" application from my Startup Applications. Unfortunately this means I have to reset the acceleration/speed settings after every restart.
just add them to your touchpad config...

see 'man synaptics' for options and their description.

---

