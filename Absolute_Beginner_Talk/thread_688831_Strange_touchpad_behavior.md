---
title: "Strange touchpad behavior"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by canthus13 on 2008-02-05
I've recently installed Gutsy on my hp dv6226cl laptop.  Everything seems to work fine, except that whenever I use the button to disable and then reenable the mousepad, a help window opens up.  Anyone have any ideas?

---

### Post by Ripfox on 2008-02-05
Yes, I noticed this on my HP laptop as well...maybe it can be changed under preferences/keyboard shortcuts?

---

### Post by Ripfox on 2008-02-05
Yep just look for "launch help browser" and change it. :)

---

### Post by canthus13 on 2008-02-05
Oh cool... Thanks. I always thought that was just a physical switch that disabled the pad.  I didn't realize it was actually detected as a keypress.  Now I just need to get it to quit trying to mount phantom drives when I'm watching    movies and quit detecting imaginary CDs on bootup....

---

### Post by ubuntu-freak on 2008-02-06
To automatically disable the touchpad while typing, you need to edit or confirm you have "SHMConfig" enabled in your xorg.conf file. Back it up first with (write these down)
 
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**
 
to restore the back up
 
**sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf**
 
Now
 
**gksudo gedit /etc/X11/xorg.conf**


Use the example below and make sure you have the "SHMConfig" line.


```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection
```

 
To automatically stop your cursor moving around when you type, go to System>Preferences>Sessions and add this to your start up list

**syndaemon -i 1 -d**
 
Then **REBOOT**.
 
Hope that helps.
 
Nathan

---

