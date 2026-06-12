---
title: "Multi-boot how to needed, XP, Edgy etc"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by jiminid on 2007-04-09
Hi, semiNoob here.
Had problems trying to install edgy after mepis as edgy wanted to reformat my mepis partitions. said two roots on same mounting point or something. Anyway, this is what I want to do- I have XP on drive 1 (hda1) I want to install Ubuntu Edgy, Mepis and Mint on drive 2
(hdb). I would really appreciate a step by step on this procedure, need to have separate root and home partitions for each, use one common swap partition. Can wipe whole drive clean to start. :confused: 

Thanks for your help

---

### Post by Kobalt on 2007-04-09
Hello,

you will find all this here : [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Welcome :)

---

### Post by confused57 on 2007-04-09
> **jiminid said:**
> Hi, semiNoob here.
Had problems trying to install edgy after mepis as edgy wanted to reformat my mepis partitions. said two roots on same mounting point or something. Anyway, this is what I want to do- I have XP on drive 1 (hda1) I want to install Ubuntu Edgy, Mepis and Mint on drive 2
(hdb). I would really appreciate a step by step on this procedure, need to have separate root and home partitions for each, use one common swap partition. Can wipe whole drive clean to start. :confused: 

Thanks for your help
You might want to check out this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

If you don't want to install grub IPL to your Window's drive mbr, then you could switch your Linux drive as master & Window's drive as slave:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

There's no problem sharing a common swap partition, but I wouldn't have a common home partition.

---

