---
title: "[SOLVED] Problem booting"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by fainaent on 2008-01-14
Ok, I've used linux before but my brother was always the administrator in our house and set everything up. I've got a Sony Vaio AR600, Intel Centrino duo-core 2.0, 2 gigs of ram, and Nvidia 8400. I was trying to follow the AMC(?) tutorial for installing this, but my graphics card is not recognized. This brings me to a black screen with a prompt. I tried ctrl alt f1 to get to the terminal, and tried doing

sudo gedit /etc/X11/xorg.conf

but all I get is 'cannot open display'.  Any help to get me going on this would be much appreciated, thanks!

-Zachary

---

### Post by PeterJS on 2008-01-14
Chicken and the egg, gedit is graphical and needs the graphical interface that you're trying to get working with gedit.

You could try editing it by hand with:
```

sudo nano /etc/X11/xorg.conf

```

Or you can try and have the system generate the file for you:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by fainaent on 2008-01-14
Thanks, that helped me get started :)

Well, I hope I'm not barking up the wrong tree or anything, I'm just trying to emulate some of the solutions I've read. I used dpkg-reconfigure xserver-xorg, and that all seemed to run smoothly. The only thing I wasn't sure about was the BusID for the card...

lspci | grep "VGA" gives me 01:00.0 , but that doesn't seem right, it seems I need some number like 1:0:0

again, I'm really not sure what I'm doing here, the advice is extremely appreciated.

also, lspci | grep xorg.conf doesn't do anything...

-Zachary

---

### Post by PeterJS on 2008-01-14
> **fainaent said:**
> Thanks, that helped me get started :)

Well, I hope I'm not barking up the wrong tree or anything, I'm just trying to emulate some of the  solutions I've read. I used dpkg-reconfigure xserver-xorg, and that all seemed to run smoothly. The only thing I wasn't sure about was the BusID for the card...

lspci | grep "VGA" gives me 01:00.0 , but that doesn't seem right, it seems I need some number like 1:0:0

01:00.0 is an entirely reasonable place for a graphics card to be on the PCI bus. I've got an nvidia, and that's exactly where mine is. Also dpkg-reconfigure (with the glaring exception of screen resolutions) does a pretty good job of guessing the right X settings to at least get to you to 800X600, and able to use graphical tools.

> 
again, I'm really not sure what I'm doing here, the advice is extremely appreciated.

also, lspci | grep xorg.conf doesn't do anything...

-Zachary

I wouldn't expect that too, what grep does is search, and what lspci does is list things on the PCI bus, I wouldn't expect to find a configuration file (or even it's name) buried deep in the hardware listings.

Did you reboot after trying to have X auto configure itself? and what happened?

---

### Post by fainaent on 2008-01-14
I rebooted, and got the same results. After a few minutes of a blank screen an 'x' appears in the middle of the screen. Then a box comes up saying 'Ubuntu is running in low-graphics mode. Your screen and graphics card could not be detcted correctly..." If I continue, I'm brought to the screen with 
checking battery
running local boot scripts

How should I enter the BusID? 01:00.0, 01:00:0, or something else?

*thoroughly confused, and still hoping to see the Ubuntu desktop sometime today :P*

-Zachary

---

### Post by Sef on 2008-01-14
> sudo nano /etc/X11/xorg.conf

You should use ```
gksudo nano /etc/X11/xorg.conf
``` or ```
gksudo gedit /etc/X11/xorg.conf
``` any time [you need a grahpical application]("https://help.ubuntu.com/community/RootSudo").  If you just use sudo, sometimes, you won't be able to get a graphical interface.

---

### Post by dstew on 2008-01-14
Are you trying to run an Ubuntu system that has already been installed to the hard drive, or just run the LiveCD system?

---

### Post by fainaent on 2008-01-14
I'm just trying to boot the Live CD so I can install it.

---

### Post by PeterJS on 2008-01-14
> **Sef said:**
> You should use ```
gksudo nano /etc/X11/xorg.conf
``` or ```
gksudo gedit /etc/X11/xorg.conf
``` any time [you need a grahpical application]("https://help.ubuntu.com/community/RootSudo").  If you just use sudo, sometimes, you won't be able to get a graphical interface.
Hey Sef, I appreciate all the work the forum mods do for us here, the place wouldn't run with out you guys. But I can't help but laugh, isn't it a bit silly suggesting gksudo and gedit over sudo and nano in a thread about getting X to work?

That said give me movement to read the other replies and I'll see what I can do about coming up with a solution.

> **fainaent said:**
> I'm just trying to boot the Live CD so I can install it.
I missed that part the first time.

Ok pressing forward now, in your xorg.conf  there should be a section that looks kinda like this:
```

Section "device"
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

```

What does yours have for the driver and Busid sections?

---

### Post by fainaent on 2008-01-14
> **PeterJS said:**
> 
Ok pressing forward now, in your xorg.conf  there should be a section that looks kinda like this:
```

Section "device"
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

```

What does yours have for the driver and Busid sections?

all I have is
```

Section "Device"
     Identifier    "nVidia Corporation G80
     Driver          "nv"
     BusID          "PCI:1:0:0"
EndSection

```

---

### Post by fainaent on 2008-01-14
bump?

---

### Post by PeterJS on 2008-01-14
That looks right, that's what it should be for the open source driver. The board name is only needed if you've got an SLI setup, and the screen option is for dual monitor support.

You might try changing the driver to vesa, and then try running startx to start the graphical environment. The vesa driver should work with pretty much every card, but it only goes up to 800X600 and doesn't support 3d.

---

### Post by fainaent on 2008-01-14
Excellent, I don't know what was different this time, but I've made it to the desktop, now I'm installing. Thanks a ton!

---

