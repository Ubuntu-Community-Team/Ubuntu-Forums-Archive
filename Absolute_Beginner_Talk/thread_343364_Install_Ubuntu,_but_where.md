---
title: "Install Ubuntu, but where?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by happy_soil on 2007-01-21
Hello everyone. This is my first post and basically my first try on Ubuntu. Basically a newbie.

I'm thinking of installing Ubuntu on my Windows XP PC. The problem is, I can't decide on what hard drive will I be using to install it. Here's my case:

[list=1]
[*]I'm on Windows XP Professional
[*]1.46 GB of RAM
[*]**Has 2 HDs**
[/list]

[list]
[*]First drive has 2 partitions; 15 GB (<2 GB left) and 134 GB (<15 GB left) in total 160 GB
[*]Second drive has 3 partitions; 25 GB (unused - prepared for Ubuntu install), 74.9 GB and 132 GB (both unused) - in total 250 GB
[/list]

So there, I just can't decide on where I should install it. Also, if, for example, I have installed it anywhere on the second drive, should I change the boot sequence in order for me to choose what OS I use?


Thanks in advance. =)

---

### Post by AirAshby on 2007-01-21
Yeah you will need to install the Grub boot menu on the primary boot drive.

---

### Post by happy_soil on 2007-01-21
Sorry, my knowledge about Linux is not that good atm. What do you mean by Grub? Is that included on the LiveCD?

---

### Post by rj686 on 2007-01-21
Yes grub is included in the LiveCD. He also mean that you need to install it in your main hdd, not the slave hdd ;)

---

### Post by happy_soil on 2007-01-21
Oh ok. I'd go check it out now.

*edit*

I can't find it anywhere on the CD. Am I using the correct CD? Here's the screeny:

[[img]http://filelabs.net/fl1/files/thumbs/ubuntuO730.th.png[/img]](http://filelabs.net/my.php?file=ubuntuO730.png)

---

### Post by teet on 2007-01-21
He doesn't need to install ubuntu onto his main hdd!  He can install ubuntu on his slave hdd without any problems. 

All you need to do is install grub onto your primary boot sector which is the default spot for it.  I think at some point during the install it will ask you "Do you want to install grub to the primary boot record..." all you have to do is say "yes" and it does it for you.

Since you have so much space on your second harddrive, I would suggest installing the root filesystem ( / ) on one partition and home ( /home ) on a separate partition.  You may even want to make a fairly large "shared" FAT32 (a.k.a. vfat) partition so you can share files between windows and linux easily.

-teet

---

### Post by happy_soil on 2007-01-21
Thanks for the quick replies. I can click Firefox, Thunderbird, Abiword, GAIM, and GIMP to install, but for some reason I just can't find any "install Ubuntu" or anything like that on the CD, and the GRUB as well. 

Anyhow, I'll sort it out later this evening. Thanks again everyone. =)

---

### Post by teet on 2007-01-21
> **happy_soil said:**
> Thanks for the quick replies. I can click Firefox, Thunderbird, Abiword, GAIM, and GIMP to install, but for some reason I just can't find any "install Ubuntu" or anything like that on the CD, and the GRUB as well. 

Anyhow, I'll sort it out later this evening. Thanks again everyone. =)

You need to boot from the live CD in order to install it.  You can't install ubuntu from windows.

Personally, I always use the "alternative install CD" instead of the "live CD" to install.

-teet

---

### Post by AirAshby on 2007-01-21
Yeah sorry about not clarifyng my reply having a problem of my own at the moment.

---

