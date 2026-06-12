---
title: "webcam problem (easycam2 package)"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-01-26
i have recently downloaded the easycam2 package to try and install the drivers for my creative instant webcam. sure enough the easycam2 package detects the device and installs ths spca5xx drivers but when i open anything like camorama to view the output of my webcam i get the error message:

Could not connect to video device (/dev/video0)
Please check connection

anyone know what i`m doing wrong or why it is showing me this message. i have had it working twice i think. but i have since done a compete reload to overcome graphics problems quickly and now it wont work at all. 

Any help would be greatly appreciated, Thanks DK

EDIT: yes it is plugged in :D

---

### Post by DiscoKiller on 2006-01-30
Right, i have managed to answer my own question with plenty of hard work and one complete reload under my belt.

This is for anyone experiencing the same problems with easycam, i.e. it installs the driver but programs still wont detect it.

Before you run the easycam package go to the console and type

export CC=/usr/bin/gcc-3.4

this tells the easycam package to use the gcc-3.4 compiler when compiling the spca driver on ur system.

Hopefully i have managed to help someone.

DK

---

