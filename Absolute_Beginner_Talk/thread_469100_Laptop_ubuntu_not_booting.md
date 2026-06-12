---
title: "Laptop ubuntu not booting"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by slyr1143 on 2007-06-09
when i start it up i c the text loaders, then the ubuntu loader, and then 4 sum reason the screen goes black and my laptop stays on plz help how do i fix it, its a fresh install, formatted whole  hard drive

---

### Post by overdrank on 2007-06-09
> **slyr1143 said:**
> when i start it up i c the text loaders, then the ubuntu loader, and then 4 sum reason the screen goes black and my laptop stays on plz help how do i fix it, its a fresh install, formatted whole  hard drive

Hi and welcome could you tell us the version of ubuntu you are installing and some specs on your system.:popcorn:

---

### Post by diatribe on 2007-06-09
when it asks you what you want to boot in grub, select recovery mode or single user whatever the second option is and see where it stalls

---

### Post by slyr1143 on 2007-06-09
ok i have a compaq presario v6000 series widescreen laptop 

512mb of ram

geforce go 6150 video card

80gb hdd 

ubuntu 7.04 desktop edition -  latest from their site

when i boot into recovery mode, it lets me type stuff at the end, as in it will go through all the things, then it will let me type what ever i want, i typed startx but that also just went black

---

### Post by overdrank on 2007-06-09
> **slyr1143 said:**
> ok i have a compaq presario v6000 series widescreen laptop 

512mb of ram

geforce go 6150 video card

80gb hdd 

ubuntu 7.04 desktop edition -  latest from their site

when i boot into recovery mode, it lets me type stuff at the end, as in it will go through all the things, then it will let me type what ever i want, i typed startx but that also just went black

Ok I am assuming that you just installed and have not installed the video drivers yet. You can use this command *sudo dpkg-reconfigure -phigh xserver-xorg* and follow the prompts and if you don't know the answer then stick with the default given. Hopefully this will get you going so you can install the graphics drivers. :popcorn:

---

### Post by slyr1143 on 2007-06-09
i did that , what is the nvidia driver called, 4 sum reason my default was vesa, and that didnt work

---

### Post by overdrank on 2007-06-09
> **slyr1143 said:**
> i did that , what is the nvidia driver called, 4 sum reason my default was vesa, and that didnt work

Hi you can try nv and that may work but if you use the command I posted that will configure automatically. If all else fails the vesa driver should get your graphics going. Good luck !:popcorn:

---

### Post by slyr1143 on 2007-06-09
ok idk, it jsut isnt workng for me, i tried the command u gave me, and that brings up a selection screen, anyway nothing seems to be working, i huess ill just reinstall vista

---

### Post by soapytheclown on 2007-06-12
[http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000](http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000)

quick forum search of v6000 ;)

---

