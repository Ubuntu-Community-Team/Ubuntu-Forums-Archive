---
title: "gutsy sata problems and black screen"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by strongboww on 2008-02-17
hi,
i wanted to install K/U -buntu on my girlfriends new pc, but unfortunately i experience some problems,

first thing is the black screen, saw a few threads about that, but we will see which solution works, i already tried to delete "splash" and then i saw that obviously the pc has problems with SATA devices the hdd and also the dvd

i connected it to SATA port 1(hdd) and port2 (dvd), for both it said that there is some kind of "xfermode" error, and that it will retry in 5 sec.

also it seems that there are problems with the usb-slots

---

### Post by Jimmyfj on 2008-02-17
Hi strongboww

We need more information on the hardware specs of the computer: 

Which graphics card is installed?
Which version of Kubuntu are you trying to install?
List some specs about that for us and we'll be able to figure it out together.

---

### Post by strongboww on 2008-02-17
system:
Abit IP35
Intel Core2Duo E6550 @stock 2,3 Ghz
Gainward 8600GTS Golden Sample
4 GB of Corsair Value RAM
Samsung Spinpoint 500GB SATAII
Samsung DVD

Screen:
Eizo S2031-WH, normally 1680x1050

i tried to install alternate 64bit, and it worked well, but at rebooting same problem as with normal livecd install


edit: could it be that there are SATA problems because i didtn jumper hdd master? or is there no difference in SATA mode?

---

### Post by strongboww on 2008-02-17
sorry for double-post, 

but i could now sort out the problems with SATA by doing AHCI mode in bios instead of ide

just need to fix the black-screen before log-in and everything is shiny

---

