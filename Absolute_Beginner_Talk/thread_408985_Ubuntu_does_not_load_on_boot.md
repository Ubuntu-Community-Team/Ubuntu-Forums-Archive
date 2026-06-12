---
title: "Ubuntu does not load on boot"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by hippykiller on 2007-04-14
I have burned all of the files from the ubuntu 6.10 download on to a disk, I put the disk in the disk drive restart, change boot sequence to read from cd-rom/dvd first, it tries but Ubuntu will not load. Any one got any ideas what I did wrong?

---

### Post by mahy on 2007-04-14
Can you open the CD in your current OS and tell us what files you see?

---

### Post by mikewhatever on 2007-04-14
All of the files? There was supposed to be only one iso file, which you were supposed to burn as image (not as data).
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29)

---

### Post by hippykiller on 2007-04-14
> **mahy said:**
> Can you open the CD in your current OS and tell us what files you see?

Lets see... We have file folders named...

.disk
bin 
casper
disktree
dists
install
isolinux
pics
pool
preseed
programs

and then files named...
autorun.inf
cdromupgrade
md5sum.txt
README.diskdefines
start.bmp
start.exe
start.ini
ubuntu
ubuntu.ico

---

### Post by hippykiller on 2007-04-14
> **mikewhatever said:**
> All of the files? There was supposed to be only one iso file, which you were supposed to burn as image (not as data).
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29)

Im not seeing any .iso's in the whole download.

---

### Post by mikewhatever on 2007-04-14
Haven't you downloaded the iso file, perhaps something called ubuntu-6.10-desktop-i386.iso? They are all and only iso's on Ubuntu download page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by hippykiller on 2007-04-14
> **mikewhatever said:**
> Haven't you downloaded the iso file, perhaps something called ubuntu-6.10-desktop-i386.iso? They are all and only iso's on Ubuntu download page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Oops... Ok yes I have... So I burned the iso to a cd. Then booted my computer to cd-rom/dvd and still nothing. The cd/dvd drive checks the disk and the directly boots to windows.

---

### Post by Bushfire on 2007-04-14
Have you got the correct processor version? You're not running a PowerPC or a 64bit one, right?

---

### Post by hippykiller on 2007-04-14
> **Bushfire said:**
> Have you got the correct processor version? You're not running a PowerPC or a 64bit one, right?

64bit supported c2d... Man I am a nooooob.... And would you believe it I actually put the thing together on my own. I started thinking I was really slick for a minute.

---

### Post by hippykiller on 2007-04-14
> **Bushfire said:**
> Have you got the correct processor version? You're not running a PowerPC or a 64bit one, right?

Well that was not it. I dl'ed and burned the 64bit .iso told it to boot from the disc drive, tried to read disk and then proceeded to boot to window. Any one got any other ideas.

---

### Post by hippykiller on 2007-04-14
Ok so I burned the 64bit edition to a dvd and was able to boot to the splash screen. I checked the disk for errors then rebooted got to the splash screen selected install ubuntu a status bar came up for a few minuets and then a blank screen with a blinking cursor in the top left corner. Is this normal?

---

### Post by hippykiller on 2007-04-14
Ok so I tried i86 on a dvd. Every thing was going fine until a menu poped up saying...  x server failed to load. What is this all about? What now?

---

### Post by mikewhatever on 2007-04-14
Looks like some of the hardware is problematic. Can you post your PC specs
CPU
RAM amount
graphics card
...whatever else you know
Also, try disconnecting any USB/FireWire devices, just leave the keyboard and the mouse.

---

