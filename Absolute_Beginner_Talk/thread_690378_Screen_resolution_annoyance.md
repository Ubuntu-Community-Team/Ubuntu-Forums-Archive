---
title: "Screen resolution annoyance"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by kizmet_x on 2008-02-07
Hey guys, running Gutsy 32-bit. My videocard drivers are the nvidia-new-glx. For some reason, this defaults at 1600x1200. I prefer to run at 1024x768.

The login screen stays at 1600x1200. Usually upon booting into the system, it goes into 1024x768. However, every third or fourth boot it boots into 1600x1200 and wont go back into 1024x768 until I reboot, then it works right. My default is checked at 1024x768, and it is set that way in the x config file.

Its not really a big deal, but it is a minor annoyance. Anyone have any idea why its doing this?

---

### Post by emarkd on 2008-02-07
I've never experienced that and don't know why it would happen, but an easy fix is to edit your /etc/X11/xorg.conf file and remove all references to the resolution you don't want it to use.  But please make a backup of that file first.  If something goes wrong your backup will be the best way to fix it.

---

### Post by kizmet_x on 2008-02-07
> **emarkd said:**
> I've never experienced that and don't know why it would happen, but an easy fix is to edit your /etc/X11/xorg.conf file and remove all references to the resolution you don't want it to use.  But please make a backup of that file first.  If something goes wrong your backup will be the best way to fix it.

Tried that, there are no references to any resolutions in that file.

---

### Post by emarkd on 2008-02-07
I think there has to be.  They should be under the Section "Screen", SubSection "Display".  Are you sure you're looking at the right file?

---

### Post by kizmet_x on 2008-02-07
> **emarkd said:**
> I think there has to be.  They should be under the Section "Screen", SubSection "Display".  Are you sure you're looking at the right file?

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

---

### Post by emarkd on 2008-02-07
Sometimes they're saved as Modelines under the "Monitor" section, but if you got that far, I'm sure you checked there as well.

---

### Post by kizmet_x on 2008-02-07
> **emarkd said:**
> Sometimes they're saved as Modelines under the "Monitor" section, but if you got that far, I'm sure you checked there as well.

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

---

