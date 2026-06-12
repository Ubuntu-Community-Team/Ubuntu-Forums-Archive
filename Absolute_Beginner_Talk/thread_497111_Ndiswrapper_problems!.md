---
title: "Ndiswrapper problems!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by t99 on 2007-07-09
Back again unfortunately! 

Im using this guide for my wireless 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

but when i get to this part

sudo apt-get install ndiswrapper-utils-1.9 cabextract

it says



Couldn't find package ndiswrapper-utils-1.9

Is it the wrong utility for feisty?Should it be different?

---

### Post by xxchrisxx555 on 2007-07-09
i have not had success with the ndiswrapper included in ubuntu
i would recomend compiling it

---

### Post by FlowerBoy on 2007-07-10
Hey guys, I also have similar problem, but it says to me this: "Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make", so if anyone can help me I would be very thankful, I'm also newbie in Linux..

---

### Post by djhworld on 2007-07-10
You need to download 

ndiswrapper-utils
ndiswrapper-common

from packages.ubuntu.com

Put them in a folder, cd into it using the terminal, then try installing it :)

---

### Post by S15_88 on 2007-07-10
if that isn't working for you just go to the ndiswrapper site and download ver.19, extract it then change directories to the extracted folder and do ./configure, make, make install, then continue with the guide you were using.

Thanks, Alain

---

### Post by FlowerBoy on 2007-07-10
Ok, I've download it all and did everything and after I run "rmmod ndiswrapper" it says ERROR: Module ndiswrapper does not exist in /proc/modules,

---

