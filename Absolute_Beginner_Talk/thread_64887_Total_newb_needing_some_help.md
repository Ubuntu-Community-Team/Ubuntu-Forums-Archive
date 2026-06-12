---
title: "Total newb needing some help"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by foges on 2005-09-12
Hey guys, im a total newb to linux even though ive tried it out many times before. Ive just downloaded ubuntu 5.10 and installed it. should i have installed 10.04 instead though? if so ill download that and install it, secondly i have a 1600x1200 screen, but the max resolution that i can set it to is 768x1024 so how can i change it (maybe install the ati drivers, need help on that though. thanx:D

---

### Post by krusbjorn on 2005-09-12
Ubuntu 5.10 (codename Breezy Badger) is the unstable (development) version, and will be released in October. You should probably install version 5.04 (hoary hedgehog) if you want a stable system :)

To be able to set higher resolution, open the terminal (ALT-F2 - "gnome-terminal") and type:
sudo dpkg-reconfigure xserver-xorg

You will then go through a stage-by-stage setup to configure your mouse, keyboard, screen etc.

---

### Post by foges on 2005-09-12
thanx a lot ill try it out. how do install the ati drivers btw
and should i be using the 64 bit version (have an amd 64 3500+)? or will i have driver problems and stuff?

---

### Post by krusbjorn on 2005-09-12
I also have an AMD64 CPU, and i tried the 64 bit version first. But there were a lot of problems with cedega, codecs and stuff, so i quickly reverted to the i386 version. The 64 bit version is supposed to be faster, but i honestly didnt notice any difference at all.

Here's how to install ATI drivers (if you're still on Breezy, chances are it wont work):
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

