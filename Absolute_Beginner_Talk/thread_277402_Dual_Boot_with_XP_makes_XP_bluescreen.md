---
title: "Dual Boot with XP makes XP bluescreen"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by dvessels on 2006-10-14
](*,) Okay, maybe somebody has heard of this or had it themselves. At one time I had a dual boot with SUSE10.1 on this laptop. I wanted to upgrade from Suse to Ubuntu. Now, when I try to install Ubuntu or Edubuntu, they run so slowly on "live" that I wouldn't dream of attempting to install them permanently. Xubuntu seems to install properly; after installation, it boots up just fine. However, XP gets to the little blue boxes running left to right, then bluescreens--consistently. If I use a partition manager and delete Xubuntu, I can go back and repair the XP install and the MBR and it will resume working as previous to the install.

Any ideas on why it's doing this/what I can do to have a successful, working XP-Ubuntu dual boot----PLEASE????

-Confused:-|

---

### Post by Nytram on 2006-10-14
I had a similiar problem to this, when I tried to dual boot Xububtu with Win ME on an old desktop. The problem seems to be caused by Grub being written to the MBR, as you've noticed. My solution was to install Grub onto a floppy disk instead of the MBR, and this solved the Windows blue screening.

Btw, Ed/Ubuntu runs a lot faster once installed onto an hard drive, as opposed to running off the live Cd.

---

### Post by oliverb on 2006-10-14
Not sure if this would work but ...

I understand you can install GRUB to the partition boot record rather than the MBR. This would allow you to leave the Microsoft MBR in place and hopefully have windows run correctly.

With any luck you might be able to set the Linux partition (with GRUB) as the active partition, so the MS MBR would chain to GRUB then you ought to be able to select Windows from GRUB.

---

### Post by ReaderRat on 2006-10-14
> **dvessels said:**
> ](*,) Okay, maybe somebody has heard of this or had it themselves. At one time I had a dual boot with SUSE10.1 on this laptop. I wanted to upgrade from Suse to Ubuntu. Now, when I try to install Ubuntu or Edubuntu, they run so slowly on "live" that I wouldn't dream of attempting to install them permanently. Xubuntu seems to install properly; after installation, it boots up just fine. However, XP gets to the little blue boxes running left to right, then bluescreens--consistently. If I use a partition manager and delete Xubuntu, I can go back and repair the XP install and the MBR and it will resume working as previous to the install. 
For your **general** info:
Dual Booting - XP & Ubuntu (On One HDD)
          [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
**More specific:**
ReInstalling Windows & Recovering Ubuntu
          [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

