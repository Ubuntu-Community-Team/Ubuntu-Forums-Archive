---
title: "Screen Resolution, Not much choice"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by onemind on 2006-12-09
Hi,

I have dual booted windows xp and ubuntu and am just starting to get used to linux. The trouble is, in windows i can set the screen resolution quite high like 1224v1024 but the highest it goes in ubuntu 1224x768 and this is just a bit small for my liking. Is there a way to get a higher resolution?

Thanks :)

---

### Post by shanepardue on 2006-12-09
Have you installed a video driver? what video card are you using?

---

### Post by riven0 on 2006-12-09
> **onemind said:**
> Hi,

I have dual booted windows xp and ubuntu and am just starting to get used to linux. The trouble is, in windows i can set the screen resolution quite high like 1224v1024 but the highest it goes in ubuntu 1224x768 and this is just a bit small for my liking. Is there a way to get a higher resolution?

Thanks :)

First, what is your graphics card? You may have to install the official drivers for it.

---

### Post by onemind on 2006-12-09
Its an old ATI - Radeon 9200 PCI

I read about the drivers on the ubuntu site and typed in some line into the terminal and it said yeas and supposedly that means my drivers are installed. Also, the glx screen savers work nicely.  I went to the ati site and downloaded a 50mb file for my card for linux like i do on windows but i didn't know how or if i could install it.

---

### Post by shanepardue on 2006-12-09
You'll want to install the xorg-driver-fglrx package in synaptic. Once it's 
installed, type the following into a terminal to configure 
your card...

```
sudo cp/etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```
And make sure to choose the fglrx driver in the appropriate driver choosing 
menu. Reboot after all the questions are done by typing "sudo reboot" in the 
terminal.

If for some reason, you lose entrance to ubuntu and get a bunch of error 
messages, push enter a few times til you get to the terminal and type this 
command...

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Then post on here with results!!

---

### Post by onemind on 2006-12-09
Worked like a charm :)

Thank you very much!

---

