---
title: "Installing Ubunto"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by Napasik on 2005-09-08
Hi!
As many other people im new to the Linux OS. I read that Ubuntu is very noob friendly so I downloaded the .ISO file..
My concern is that I have to partions: C:\[NTFS] With Windows on it: And D:\[FAT32] With games,programs etc on it..

I want to able to have Dual boot, but what disk do I put Ubunto on ? the C:\NTFS or D:\FAT32 ?

Thanks for answers.

---

### Post by wellery on 2005-09-08
I think you could use either. Do note that linux can only write to fat32 and not ntfs but it can read ntfs.

Follow this guide:

[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)

and then this:

[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

---

### Post by Napasik on 2005-09-08
Thank you!
So the disk doesnt have to be totally empty, but can have some files on it without effecting the installation?

---

### Post by swamytk on 2005-09-08
Ubuntu can't be installed in exiting windows partition. Do you have free space in your hard disk of minimum of 4 GB (bare min 2GB)? if it is so, then you boot your system with ubuntu install CD. While installing it will ask for the partition preference, you select "remaining free space" (something like this) option to install the ubuntu on this free space. Be careful to do this (better take a backup of data on windows, if you are really new to this kind of work)

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=Napasik]
I want to able to have Dual boot, but what disk do I put Ubunto on ? the C:\NTFS or D:\FAT32 ?
[/QUOTE]

Neither. You will have to use the isntaller to shrink one. Linux needs its own parition...it can't be installed on FAT or NTFS. Its easy.

You should read this:

[http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/](http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/)

---

### Post by az on 2005-09-08
Pick either one.  You will need to have a bare minimum of a little more than two gigs to install, but perhpas four gigs would be better.  You will need to have that much free space on one of the disks so that you can free up some room on the disk to install.  Look here:

[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by Napasik on 2005-09-08
Okey.

I have ONE harddisk with TWO partions:

1. With Windows, approx 10GB : NTFS
2. Games,programs, files etc: 30 GB : FAT32

So I CAN install Ubuntu onto the 2nd Partion without having to create new partions ?

---

### Post by swamytk on 2005-09-08
Dear Napasik,

If yours is 40GB, you can't install as it is now. Either you have to make some free space with a partition resize tool or you have to delete D: partition (use that partition for linux installation)

---

### Post by Napasik on 2005-09-08
:)
Now im online with Ubuntu, it was very much like the windows partion setup so very easy to understand!
Thanks for every answer, even though we had some trouble understanding eachother :)

---

