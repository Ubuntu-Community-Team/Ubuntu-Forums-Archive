---
title: "Right, I'm gonna try Ubuntu"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by mp3guy on 2005-05-29
I just ordered my cd, i'm putting it on a new pc;

Pentium 4 Prescott 2.4GHz
GeForce 3 Ti 500
80GB 7200RPM Hard Drive
512MB Ram
Sony CRX320E CDRW/DVD
Onboard AC'97 Audio

I'm thinking of making a 40GB/40GB split, one partition for each OS. I'd like to use Ubuntu for browsing the internet (it would be connected through a router, it appears as a LAN connection on WinXP), listening to music and word processing etc. I'd like to use WinXP for video editing and playing games. 

Will I be able to install XP first, then Ubuntu afterwards?

---

### Post by davidgypsy on 2005-05-29
[QUOTE=mp3guy]I just ordered my cd, i'm putting it on a new pc;

Will I be able to install XP first, then Ubuntu afterwards?[/QUOTE]

Yes, just read the instructions very carefully as you do the Ubuntu install.

---

### Post by tread on 2005-05-29
I would suggest keeping another partition formatted as fat32, linux cannot write to an ntfs partition so the fat32 would give you a handy way of sharing files between the two operating systems.

You'd need to install Windows first, then Linux.

---

### Post by heltinde on 2005-05-29
Yes you can. But I think 40 GB is to much for Ubuntu since you only wanna use it for browsing and wordprocessing.

First you patition the harddisk (no need to format the partition for Ubuntu), then install XP.
When you install Ubuntu afterwards you choose the free space on hda (linux name for hdd). You need a small partition for a swap file - max 1 GB (2 x your ram). You will be asked where to place the partition - make sure it's in the end, because it'll work faster then. The rest is for your Ubuntu installation.

You need a bootmanager, fx. lilo, but I'm not sure if it automaticly comes with Ubuntu.

---

### Post by tread on 2005-05-29
grub - thats a boot manager .. will be installed by ubuntu.

---

### Post by Leif on 2005-05-29
Don't worry, a boot manager is provided, and it will recognize your existing windows partition so you can boot to whichever one you like. Once you've installed, head off to ubuntuguide.org for invaluable information. Have fun !

---

### Post by Jenda on 2005-05-29
It might be a good idea to first partition the disk with the Ubuntu install CD, then install XP, and then Ubuntu. Correct me if I'm wrong.

---

### Post by poofyhairguy on 2005-05-29
[QUOTE=Jenda]It might be a good idea to first partition the disk with the Ubuntu install CD, then install XP, and then Ubuntu. Correct me if I'm wrong.[/QUOTE]

Yep. Backup everything first.

---

### Post by tread on 2005-05-29
Yep, partition, install xp, then linux. Corrrect order :)

But doesnt the windows installer give you an option to create partitions? I am pretty sure it will .. or it did when I last installed Windows myself (this was Windows 98 :))

---

### Post by thecrimsonking on 2005-05-29
[QUOTE=tread]But doesnt the windows installer give you an option to create partitions? I am pretty sure it will .. or it did when I last installed Windows myself (this was Windows 98 :))[/QUOTE]

Yes W2k and XP both have options to make partitions during install.   I would rather leave the part of the hard drive I want to use for Ubuntu blank instead of having Ubuntu format a Windows formatted partition.

---

