---
title: "x server failiur"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ~&#730;JaZ&#730;~ on 2007-05-29
Hi! I have a big problem:(, i made na update and after i restarted the mashine i wasnt able to lunch the x server... all i get is a blue screen with an error message saying:

Faild to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

and when I pres yes i get that:

NVIDIA: No matching device device section for instance (busID PCI:0:1:3) found
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): faild to load the nvidia kernel module!
(EE) NVIDIA(0): ***aborting***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

this is all i can get....i have tried the boot cd and i can normally get the graphical interface...so i dont think that there is anything wrong with my graphic card or is it?....I am just a rookie :> so i would appreciate any help pls, 

TNX
Z

---

### Post by nagius on 2007-05-29
hi,

I think you have a graphic driver problems or xorg, log in with you user name on a terminal (ctrl+alt+f6) and type the following sudo dpkg-reconfigure xserver-xorg otherwise try sudo apt-get install nvidia-glx and then sudo nvidia-glx-config enable

cheers

---

### Post by ArtDzot on 2007-05-29
Sorry for my badly English

I have the same problem 

I'm reinstall nvidia-glx-legacy or last legacy driver from nvidia site - but Xserver not start with "nvidia" in xorg.conf, only with "nv"

help pls

---

### Post by ~&#730;JaZ&#730;~ on 2007-05-29
I tried to reinstall the driver but it i get an error saying that he is unable to find the driver...i realy dont know what to do?!...so ...any other suggestions?....I guess I could reinstall faisty.... because the sistem is relatively new...but i still have some date that i dont wanna lose?!:(:(

---

### Post by ArtDzot on 2007-05-29
looks like a bug nvidia-glx-legacy

We have 7 computers with same problem - xserver not start after upgrade kernel

---

