---
title: "problem with x server"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by comradexiactura on 2006-12-11
hey all. im having some trouble installing ubuntu on a different machine. ive installed it before and is running fine but in this install im having some problems. The first problem was i couldnt get into the normal installation and had to go into the graphical safe option. i tryed installing but the installer crashed. I opened the xorg.conf file and changed the"nv" to "nvidia" i had a felling that it was crashing due to the graphics card. That solved that problem. now whn i boot ubuntu from the hard drive it is giving me an error with x server and saying that it isnt configured correctly. im not sure how to fix this or what i should do next any help would be appreciated thank you in advanced

---

### Post by chalex on 2006-12-11
For a temporary solution you can try changing "nvidia" to "vesa".

Before you can tell xorg to use "nvidia" you have to have the "nvidia" module installed.  I don't know how to do this for the latest versions off the top of my head, but perhaps you can do it through Automatix or EasyUbuntu.

There's a whole forum about video problems here: [http://www.ubuntuforums.org/forumdisplay.php?f=138](http://www.ubuntuforums.org/forumdisplay.php?f=138)

---

### Post by comradexiactura on 2006-12-11
ok great thanks a lot ill give that a try

---

### Post by nickburns on 2006-12-11
After you get the error on x-server hit ok a couple time until you get to terminal, then backup you old xorg.conf file with:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

then reconfigure xserver with:

sudo dpkg-reconfigure xserver-xorg

this will reconfigure xserver and make a new xorg.conf file and upon reboot you should be good.

If you ever need to go back to the other configuration do:

sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf

---

