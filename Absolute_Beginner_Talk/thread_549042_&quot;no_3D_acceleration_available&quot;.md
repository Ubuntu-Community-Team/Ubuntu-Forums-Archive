---
title: "&quot;no 3D acceleration available&quot;"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by RedGreen on 2007-09-12
I have had a lot of problems trying to get 3d acceleration working. I have an ATI X1600 series card and tried installing the fglrx drivers (I used this tutorial: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194))

from my Xorg.0.log:
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

I have been playing with things as best I can but I am very new to Linux and Ubuntu so im hoping someone can give me some suggestions on what to do.

Xorg.conf: [http://pastebin.com/m9b17f31](http://pastebin.com/m9b17f31)
Xorg.0.log: [http://pastebin.com/m2ffc06db](http://pastebin.com/m2ffc06db)

---

### Post by mostwanted on 2007-09-12
If you have a backup of your xorg.conf file I would revert to that to start with. There's a script called ENVY which installs and configures ATI drivers automatically, it might work:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

> Envy: It is an application (written in Python and PyGTK) which automates the installation of both ATI and Nvidia's proprietary driver on Ubuntu ...

---

### Post by RedGreen on 2007-09-12
I'm still getting the hang of how things work. Do I need to uninstall or disable my old driver?  If so how would I go about doing that?

---

### Post by mostwanted on 2007-09-12
> **RedGreen said:**
> I'm still getting the hang of how things work. **Do I need to uninstall or disable my old driver?**  If so how would I go about doing that?

No, I don't think that's necessary.

---

### Post by RedGreen on 2007-09-12
I still get this in my Xorg.0.log:

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

However I did not change my Xorg.conf to an earlier version, I was having a hard time figuring out what I did with the backup and I just went ahead without it. There is a command that restores it isnt there? Is it necessary that I change it?

Also, I was a bit confused that glxgears runs (although when I make the window bigger it slows down a lot) could someone explain to me what glxgears is meant to show?

---

