---
title: "nvidia driver problems"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Merry on 2007-03-05
I installed the nvidia drivers using automatix (shoot me, i know) on my Geforce 2mx and now i can boot into x server. It tells me the display cant be initialized I'm pretty sure its the driver so how would I go about getting rid of it/fixing it through the command line?

---

### Post by PartisanEntity on 2007-03-05
(Assuming you are outside of the desktop environment) sudo nano /etc/X11/xorg.conf

scroll down (using arrow keys on keyboard) until you see the nvidia entry, change it to nv, then ctrl x to save (it will ask you to press enter to save, do so) and then ctrl+alt+backspace to try and restart x-server.

```
Section "Device"
    Identifier     "NVIDIA Corporation NV40M? [GeForce Go 6200]"
    Driver         "**nvidia**"*
EndSection
```

* change to "nv"

This fix will allow you to get back into the desktop environment. I would recommend the use of the [envy script]("http://albertomilone.com/nvidia_scripts1.html") to install 3d drivers.

---

### Post by mikewhatever on 2007-03-05
backup first: cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bk
sudo dpkg-reconfigure xserver-xorg

you'll see the following stuff
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

use nv or nnvidia as your driver

---

