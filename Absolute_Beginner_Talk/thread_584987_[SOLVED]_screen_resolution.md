---
title: "[SOLVED] screen resolution"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-10-21
Could someone please help me change the resolution on my desktop to 1440x900?:confused:

I have tried every command found on threads, and none of them will do it.  I tried to download Envy, but recieved a bunch of code, and an error message saying that if I saved the file it would become corrupt. This is the last major item I have to take care of to get back to where I was i Fiesty. I probably will never do a "clean" install again.
Here is what is in xorg.conf.

Section "Device"
	Identifier	"nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"E19T5W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"E19T5W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
EndSection

---

### Post by Pumalite on 2007-10-21
Have you tried: Driver "nvidia"?

---

### Post by skyjacker on 2007-10-21
> **Pumalite said:**
> Have you tried: Driver "nvidia"? No I haven't Should I back this file up somehow, and if so How?

---

### Post by Pumalite on 2007-10-21
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
gksudo gedit /etc/X11/xorg.conf
Make the change, save,exit and reboot.

---

### Post by skyjacker on 2007-10-21
Pumalite, thanks for your help. I finally got the right resolution. I think it was a combination of things wrong. I could not stop gdm before and for some unknown reason it worked again, and I was able to correct the problem. FIXED and solved. Thanks for your help.:)

---

