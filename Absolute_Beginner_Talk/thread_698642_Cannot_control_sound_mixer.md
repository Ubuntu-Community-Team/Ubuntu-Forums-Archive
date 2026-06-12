---
title: "Cannot control sound mixer"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by mzakharo on 2008-02-16
Hi, I have built a custom vanilla kernel 2.6.25rc2 - well, everything works, but I have a problem with alsa  - i cannot seem to control it in this kernel. Sound works, but the controls for mute are only accessible if i log back into the 2.6.22-14-generic kernel. Here, I get an error message when I click on a sound icon that goes: (No volume control GStreamer devices found)  Can someone please help?

---

### Post by r4ik on 2008-02-17
Try,

Applications > System Tools > Terminal
sudo apt-get install alsamixer

after you install the mixer run->
sudo alsaconf

reboot

then run-> alsamixer in the terminal.

Good luck !

---

