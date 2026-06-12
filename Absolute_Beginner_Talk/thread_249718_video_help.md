---
title: "video help"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Phoenixus on 2006-09-02
I apologize before hand if I sound like a complete noob here guys, but thats cause I am when it comes to linux ha. I just installed ubuntu on my laptop, previously running windows xp. Everything is technically "working" but my video is having problems. When I scroll webpages or anything, it just really chugs along. I have an SiS integrated graphics chipset (661fx). I went to the  SiS download site and downloaded a driver, and it showed it being for linux red hat. Problem is, I'm not really sure what to do with this file. The icon is like a jigsaw puzzle piece, and if I just try to open it, it says "couldn't display and then the file name." What do I need to do?

---

### Post by 3rr0r on 2006-09-02
I know in the help (built in ubuntu) there is an explanation as to how to convert files meant for red hat to be installed and accepted by ubuntu.  Sorry I can't fully explain it, but I'm a noob too so  :)   Hope it helps some.

---

### Post by Phoenixus on 2006-09-02
Well I just checked but this file isn't in a package archive (the .rpm deal). The name of the file is sis_drv.o-410

---

### Post by Osirls on 2006-09-02
Surely there are other package releases?
I doubt they only support Red hat binaries..

---

### Post by LKRaider on 2006-09-03
You don't need to manually install drivers in linux (usually).

The driver for your sis board for instance is already installed/available on your Ubuntu install by default.

Just check if it is enabled on your Xorg config:

  *) Press Alt+F2
  *) Type: gksudo gedit /etc/X11/xorg.conf
  *) Scroll to the line reading: Section "Device"
  *) And verify the driver line reads: Driver "sis"

Even tho you may be already using this driver, please note that SiS does not provide good drivers for linux, and you may have low performance using them, specially for 3d apps (they don't support the DRI extension).

I have a SiS card on my laptop that is from the same series as yours (the 315 series), and this is what my xorg.conf reads for that part:
```
Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection
```

More (extended and technical) info can be found here: 
[SiS/XGI graphics chipsets and X.org/XFree86/Linux](http://www.winischhofer.at/linuxsispart1.shtml#12)
[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/SiS2.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/SiS2.html)

---

### Post by Phoenixus on 2006-09-03
This is what mine reads.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by LKRaider on 2006-09-03
So your card was not autodetected by the install program. Changing the Driver "vesa" (a generic driver) to Driver "sis" should fix your problems.

You can also change the Identifier, tho it is only a description of the driver, to something like this:
```
Identifier "Silicon Integrated Systems (SiS) 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP"
```

---

### Post by Phoenixus on 2006-09-03
How exactly do I do that?

---

### Post by Phoenixus on 2006-09-03
nvm just got it working..thanks guys

---

