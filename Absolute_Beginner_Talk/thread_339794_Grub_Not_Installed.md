---
title: "Grub Not Installed???"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Arturius on 2007-01-16
Hi Guys,

First time user of Linux & Ubuntu here, I have had a quick look on the forums & not found what I was looking for, yesterday I formatted my HDD (120gig) 50gig for windows which I re-installed ( I know, but I play WOW & with Burning Crusade out now I want/NEED to be able to play without any problems, other than the ones Blizzard supply ](*,) ) & the rest for Ubuntu, I only found this prog on Friday & I am feeling like a convert already & have managed to gige out 2 disks to mates for them to look at it aswell 8). 

Anyway my problem is that unless I nave the CD in the drive I cant get into either Windoze or Ubuntu, I dont really have a clue yet asto what I am doing with linux but I like the idea of haveing a Legal machine finally (only have XP for evaluation purposes...) 

Any ideas or advice gratefully accepted (or even people telling me I dont look properly)

Thanks

---

### Post by bunabattoir on 2007-01-16
If you loaded windows after ubuntu, then widows has disabled grub in favor of its own boot loader. You will have to re-install grub (prolly to the MBR).

---

### Post by Arturius on 2007-01-16
Sorry, was reading through & realised I probably hadnt explained my self properly, I did a fresh install of XP followed by installing Ubuntu from the live CD, the only way I can now get into either OS is to have the live CD in the drive

---

### Post by bodhi.zazen on 2007-01-16
It sounds as if you need to install GRUB into the MBR.

Here is how:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This how-to will work even though it is titled "Recovering Ubuntu After Installing Windows"

---

### Post by Arturius on 2007-01-16
Thanks for the quick replies, Will have a look at it when I get back home :)

---

### Post by Arturius on 2007-01-17
The above link didnt work so I ended up re-installing both OS's & letting Ubuntu deal with all  the partitions this time, I also removed my card reader & ide hdd, which I think may have been the problem (I realised when I got home that I hadnt even mentioned it) The ide hdd was seen as my C: in windows even though my sata hdd was the one with windows installed on it, it was confusing me at the time anyway so I am not surprised GRUB had issues with it :)

Thanks for the help on this one, I now have another problem but I will read the forums first to see if I can sort it my self first :)

---

