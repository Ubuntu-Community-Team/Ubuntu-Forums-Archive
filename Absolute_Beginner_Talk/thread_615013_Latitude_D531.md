---
title: "Latitude D531"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by illi on 2007-11-16
Hi. I have a problem with Latitude D531. The first one si with graphical card, i have to start ubuntu in recovery mode and startx manualy cause of i run in normal mode there is freeze while starting x. And the second one is wireless card, i can access internet only throught WiFi and i can't setup this because there aren't some official drivers and i can't download some pkg cause i can't connect to internet without WiFi. I tryied download ndiswrapper and compile it but these a error with gcc and libraries like stdio.h and things like that. Thank you if you can help me.

---

### Post by dstew on 2007-11-16
I don't have any advice on your startup problem. As far as getting wifi to work, in order to compile you need to install the package **build-essential**. You can install this from the Synaptic package manager, or using the terminal. The command would be ```
sudo apt-get install build-essential
```
But you can also just install **ndiswrapper-common** from Synaptic, instead of compiling from source.

---

### Post by mbf2k on 2007-11-21
I also have a D531 that I just installed Ubuntu 7.10 on (x86 version). I have already tried the above fix, and did not have any success getting my wireless working. My sound also doesn't work, but I am willing to live with that, I'd just really like to have wireless internet. Any advice would be greatly appreciated!

---

### Post by mbf2k on 2007-11-21
Correction: I am now successfully connected through wireless, I didn't realize how to use the Manual Network Configuration utility to connect to my router. I will poke around for a sound fix.

---

### Post by Manu.Ubu on 2007-12-05
Hello, 
for sound problem have you install ubuntu-backport-module ?
for wifi problem, have you set drivers for broadcom 43xx ?
for X, choise driver VESA for testing and after set ATI driver.

(sorry for my bad english)

Manu

---

