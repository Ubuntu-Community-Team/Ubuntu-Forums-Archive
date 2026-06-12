---
title: "Synpatics TouchPad"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by mharris5 on 2006-09-21
Hi,
I've been trying to install something similiar to the Synaptics Touchpad available in Windows, for my laptop. So far I came across this link,

[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

which recommends installing qsynaptics or ksynaptics. When I go to install the packages, Ubuntu is unable to find them,

matt@matt-laptop:~$ sudo apt-get install qsynaptics
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package qsynaptics

Is there something I'm missing or is there a similiar package available?

Thankyou,

Matt

---

### Post by ape on 2006-09-21
qsynaptics is in the universe respository.  You need to enable this through Software Properties or by manually editing the /etc/apt/sources.list file and adding 'universe' to the end of your repository entries.

---

### Post by mharris5 on 2006-09-21
Great. Thanks for the help.

---

