---
title: "Weird Graphics problem"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Richard Mathie on 2008-02-06
hello i get this intermittent problem when running Ubuntu 7.10 Gutsy and have the advanced desktop effects running, the graphics will be running fine, for 10mins or several hours, and then suddenly, things will start to get messed up, words, buttons and images in windows get stretched out so its unreadable. and the 3D desktop goes inverted, i can get the system stable again by logging out and then back in again.
i have screen shots

i am running a gigabyte GA-8IPE1000 motherboard
Pentium 4 prosessor
1Gb Ram
nVidia GeForce 6200 256mb graphics card

i have searched the web for this problem, and have tride alot of the things people surgest for Nvidia graphics problems
i have the Nvidia restricted driver installed
i tried installing the Nvidia drivers from the Nvidia website, but that really messed up my system, and so i reinstalled.

when i type  cat /etc/X11/xorg.conf | grep Driver
i get:
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"

any help?

richard

---

### Post by Shinbu-Otaku on 2008-02-06
Do you have beryl installed? The 3D desktop graphics can sometimes muck up the display of other things, so if you do, it may be best to disable it and see if you have the same problem when using the default window manager.

---

### Post by Richard Mathie on 2008-02-07
humm... dont think i have beryl installed.
just compiz ... are they the same thing?

also i dont have xgl, but do have OpenGl

its a shame to keep the effects off, never mind

---

