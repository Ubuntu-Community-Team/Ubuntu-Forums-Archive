---
title: "How do I install video card drivers?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by linuxnoobie on 2006-08-13
I had to edit the xorg.conf file in /etc/x11 to properly change my resolution and keep the settings.  While in there I noticed this section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"NEC FE991SB"
	DefaultDepth	24
	SubSection "Display"

Looks to me like my video card isn't recognized.  It is an integrated video card, but its nVidia geforce 6100. So I went to nvidia.com.  I don't know which driver I need.

This one?
[http://www.nvidia.com/object/linux_display_amd64_1.0-8762.html](http://www.nvidia.com/object/linux_display_amd64_1.0-8762.html)

Or this one?
[http://www.nvidia.com/object/linux_display_ia64_1.0-5336.html](http://www.nvidia.com/object/linux_display_ia64_1.0-5336.html)

I downloaded the first one but when I double click on it I get a weird message saying could not open gedit was has not been able to detect the character coding.  Did I download the wrong file?  Do I have to open it up via a different method?  Someone please enlighten me.

---

### Post by meng on 2006-08-13
You'll want to install nvidia-glx, i.e. from the command line
sudo aptitude install nvidia-glx

---

### Post by keypox on 2007-08-29
i have similar question but my box doesnt make it all the way to the desktop,  Monitor turns off after boot.  I have ctrl alt f1 out to try and use vesa drive but that did not work how would i use the command line to install these drivers

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)  

i have a x1900gt btw.  Which ubuntu has no been able to find.

---

