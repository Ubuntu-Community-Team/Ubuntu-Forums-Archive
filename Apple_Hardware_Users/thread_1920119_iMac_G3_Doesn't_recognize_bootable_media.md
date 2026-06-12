---
title: "iMac G3 Doesn't recognize bootable media"
date: 2012-02-04
forum: Apple Hardware Users
---

### Post by Rexhunt on 2012-02-04
I have an old iMac G3 here running mac os 9 without a problem, however it doesn't get much use... so to improve it's use I'm planning to install cli-Ubuntu 10.04..

The only problem is I can only download Ubuntu CD's from mirror.aarnet.edu.au as it is unmetered on our internet connection. This would be fine if I could find anything other than a few apparently important random files sitting in the /pub/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/cdrom directory... I have got an iso that is labeled ubuntu 10.04 PPC form a while ago so that should be good...

My problem is that the mac will not recognize any form of me putting the media in, usb thumb drive, cdrom, holding c, option, command open firmware and probably a few other things that I've come accross but still haven't solved my problem... The drive is good because I can still boot the 9.1(I think is is) system install/restore disks... Open to any ideas at all!

---

### Post by rsavage on 2012-02-04
People have said resetting the pram/pmu (or whatever it is called on the G3) sometimes helps. 
 
If you want to try some other CDs then try the mini CDs - they are only around 10-20MB to download.  They contain the random important files you were talking about.  You can then point them at your aussie mirror to download the all the packages you need.  
 
Thanks for sharing the existence of the mirror btw.  I wonder how many other ports mirrors are out there that we don't know about?!

---

### Post by Rexhunt on 2012-02-04
Just downloaded the mini image, will let you know how I get on...

---

### Post by Rexhunt on 2012-02-04
The CD is still not recognized by of or mac os... whenever I put the CD in the drive the os asks me to initialize it(format?) which it can't do... so then it spits the disk back out...

EDIT:
Just reset pram, nvram... still no change... is there a way I can check the disk is actually bootablewith virtualbox or something like that?

---

### Post by rsavage on 2012-02-04
Well you can use qemu I guess, but that's going to take you ages to setup.  Have you done the checks here [https://wiki.ubuntu.com/PowerPCFAQ#The_CD_won.27t_boot](https://wiki.ubuntu.com/PowerPCFAQ#The_CD_won.27t_boot) ?  It could be the type of CDs you are buring to.

---

### Post by Rexhunt on 2012-02-05
Just got the installer running now...

I was burning the CD's too fast which was stopping the mac from recognizing them...

I installed k3b to allow me to burn the discs at 10x...

---

