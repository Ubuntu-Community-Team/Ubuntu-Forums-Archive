---
title: "Going from dual boot to Ubuntu alone - Howto do it"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Cloudedbrains on 2007-05-24
Ok at present I use a dual boot sytem of XP and Ubuntu feisty :)

I dont use XP at all now so how would I best go about getting Ubuntu alone on my pc :confused:

I have ordered the disks as I installed via Wubi will it be hard to sort this out :(

Could I download it to a cd/dvd and use that or what ;)

---

### Post by apunc1 on 2007-05-24
Are Ubuntu and Windows actually on different partitions of your hard drive? It's my understanding the Wubi simply installs Ubuntu as if it were another Windows program on your same Windows partition...

---

### Post by ggaaron on 2007-05-24
Format the XP disc?=) If you don't have any data you'd like to keep on that drive then use for example gparted (or mkfs.ext3/mkfs.reiserfs) to reformat that partition.

---

### Post by Cloudedbrains on 2007-05-24
I set Wubi to install Ubuntu to its own partitions on the same drive as XP but XP is on its own partition with a my document partion (total of drive 250gig) ??

Would using the XP discs to format then installing Ubuntu work ??

I would rather re-partition if I go Ubuntu alone as they are badly setup for Ubuntu !!

I've backed up the windows documents and my images etc etc to dvd !!

So in basica simple steps whats the best way to format/parition/install Ubuntu alone !!

I have an AMD 2400+ chip, 512mb dd ram, dvd-+rw !!

---

### Post by apunc1 on 2007-05-24
> **Cloudedbrains said:**
> 

I would rather re-partition if I go Ubuntu alone as they are badly setup for Ubuntu !!

I've backed up the windows documents and my images etc etc to dvd !!

So in basica simple steps whats the best way to format/parition/install Ubuntu alone !!

I have an AMD 2400+ chip, 512mb dd ram, dvd-+rw !!

if you want to set up Ubuntu only then download the .iso for ubuntu here
[http://us.releases.ubuntu.com/](http://us.releases.ubuntu.com/)

pick the live cd because it gives you a live environment and is easier to install if you need more guidance

choose to manually partition drives to set up partitions if you want a separate /home partition for your settings and personal files
use the guide here
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Cloudedbrains on 2007-05-25
> **apunc1 said:**
> if you want to set up Ubuntu only then download the .iso for ubuntu here
[http://us.releases.ubuntu.com/](http://us.releases.ubuntu.com/)

pick the live cd because it gives you a live environment and is easier to install if you need more guidance

I dont see the option for a live CD under Feisty Fawn - just normal one and alternative install :confused:

> **apunc1 said:**
> choose to manually partition drives to set up partitions if you want a separate /home partition for your settings and personal files
use the guide here
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Thanks thats very good for dual boot but have found the partition setup stuff elsewhere on there  ;)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by dptxp on 2007-05-25
The normal one is Live+Install CD.

Run it Live.

To install click on install icon.

Download using bittorrent.
Burn with Infrarecorder using 'burn image' command on mEnu.

LOad, set boot using CD in bios.

Backup Data and plan partitioning before Install.

12 BG for / (root) ext3 format , 2 GB for SWAP, make more partitions if you wish, format all in ext3, you can use one partition as /home. These all are set in step 4 (or 5?) after you click on install.

---

### Post by Cloudedbrains on 2007-05-25
Thanks

---

### Post by Cloudedbrains on 2007-05-25
I've got the Ubuntu 7.04 iso downloading to burn as an image but once I've got the cd how do I do this to go UBUNTU alone - also will this disk do away with windows for me as well ??

---

### Post by rax_m on 2007-05-25
Yes, because during your install process you can specify your partitions. In other words you can format the whole hd and install ubuntu (I think that's a straight forward option), otherwise you can manually partition and delete any existing partitions and reformat them (like your existing XP drive)

---

### Post by apunc1 on 2007-05-25
> **Cloudedbrains said:**
> I've got the Ubuntu 7.04 iso downloading to burn as an image but once I've got the cd how do I do this to go UBUNTU alone - also will this disk do away with windows for me as well ??

select to partition manually and delete your windows partitions and make your ubuntu / /swap and /home partitions from the freed space.

---

### Post by dptxp on 2007-05-25
Remove/Delete all partitions.

Resize first one, say 12 GB ext3 for / .

Resize the unallocated space for next partition. 

Next ones all ext3.

SWAP last. Keep 2GB.

---

### Post by Cloudedbrains on 2007-05-25
Thanks for ALL the help - I am now typing from Ubuntu alone :o

Will more than likely have a few questions later ;)

---

