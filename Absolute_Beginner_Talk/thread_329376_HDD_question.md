---
title: "HDD question"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-01-01
I have XP on my computer on a small HDD and have installed a new 120g HDD.
I'm going to put 6.10 on the new drive and wondered if I could, during the installation, partition it so as to have a 60g partition for ubuntu and 60g for storage, for both XP and ubuntu?
Thanks for any help.

---

### Post by scrooge_74 on 2007-01-01
Yes you can, but remember to make that storage partition fat32 so both systems can write to it.

---

### Post by kinematic on 2007-01-01
or you can partition the storage partition as ext3 and install the ext3 driver in windows.
that way you have all the benefits of ext3.

---

### Post by oilchangeguy on 2007-01-01
when you load the live cd follow the prompts to get to the page that lets you load it to you hardrive, you'll be able to set up your partition there. as far as using the other 60gb part for storage i'm not sure it can be done so that both os's can do anymore than see it. i don't know if linux can write to a fat32 partition (you'd have to format it fat32 so both can see it). from xp go to the control panel click on admin. tools, computer management, disk management, and you should be able to see the unpartitioned space. i know from there you can format the partition but i'm not sure if you'll have the option for fat32, may only be ntfs.

---

### Post by scrooge_74 on 2007-01-01
> **kinematic said:**
> or you can partition the storage partition as ext3 and install the ext3 driver in windows.
that way you have all the benefits of ext3.

I like your idea better, I just don't have XP any more so I don't need to do that :p 

[QUOTE=oilchangeguy]

when you load the live cd follow the prompts to get to the page that lets you load it to you hardrive, you'll be able to set up your partition there. as far as using the other 60gb part for storage i'm not sure it can be done so that both os's can do anymore than see it. i don't know if linux can write to a fat32 partition (you'd have to format it fat32 so both can see it). from xp go to the control panel click on services, disk management, and you should be able to see the unpartitioned space. i know from there you can format the partition but i'm not sure if you'll have the option for fat32, may only be ntfs.[/QUOTE]

This can be done since Linux have been supporting FAT32 for a long time, better make all partitioning and formatting from Linux.  And definetly don't use NTFS, it is simpler to do as kinematic says

---

### Post by Milt888 on 2007-01-01
> **kinematic said:**
> or you can partition the storage partition as ext3 and install the ext3 driver in windows.
that way you have all the benefits of ext3.

OK. I'm really new to this, so could you elaborate a little about "partition as ext3", and where the ext3 driver is?
Thanks guys for the help.

---

### Post by benerivo on 2007-01-01
When you install ubuntu, you will have to have a 60GB ext3 partition where ubuntu will be installed on to, another 59GB ext3 partition which you can select to be formatted but with no mount point (ie. none of the ubuntu os will be installed on to it, and it can be used exclusively for data/storage). You will need to have another small partition (say 1GB) formatted as 'linux swap', which is equivalent to the windows swap file. For windows to be able to read / write to the 60GB storage partition you will need to install the driver in windows so that it can read the ext3 format. The software to do this is here...
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Milt888 on 2007-01-01
I finally understand what you guys are telling me.(I'm really green).
Thanks for the link; I think I can get'erdone now.
Many thanks for the help guys.

---

