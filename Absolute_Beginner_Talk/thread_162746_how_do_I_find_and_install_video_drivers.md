---
title: "how do I find and install video drivers"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Dasien on 2006-04-19
I have just installed ubuntu to my dell inspirion 1100 I think it has intel 8245G chipset and I looked on Intel found the drivers but I think they are the wrong format and so I downloaded the suse exstetion (tar.gz) ubuntu will open it but then I am completly lost.

help
thank 
dasien

---

### Post by mostwanted on 2006-04-19
Hmm.. as far as I'm aware Intel video drivers should be installed per default (they're open source and thus included with X), but I might be wrong; I don't have Intel graphics myself.

---

### Post by az on 2006-04-19
What problem do you have with your display?

---

### Post by Dasien on 2006-04-19
I can't resize the screen 640x480

---

### Post by nalmeth on 2006-04-19
APPLICATIONS --> ACCESSORIES --> TERMINAL
sudo dpkg-reconfigure xserver-xorg

the i810 driver should load by default. Select all the other defaults, and when you get to resolution, add the ones you need.

---

### Post by Dasien on 2006-04-19
I just did this and nothing seems to have changed I still can not change from 640x480

---

### Post by az on 2006-04-19
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/29436](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/29436)

Maybe add to that bug report, please.

---

