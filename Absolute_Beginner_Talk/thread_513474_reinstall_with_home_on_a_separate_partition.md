---
title: "reinstall with /home on a separate partition"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by margaf77 on 2007-07-30
I created a partition on a separate hard disk and have home on there. I now have to reinstall due to some major hardware changes. 

How will this work? Will the install see the home partition and use it automatically or do I have to point to it after finishing installing. Also will this preserve all my Thunderbird and Firefox settings?

---

### Post by tszanon on 2007-07-30
> **margaf77 said:**
> I created a partition on a separate hard disk and have home on there. I now have to reinstall due to some major hardware changes. 

How will this work? Will the install see the home partition and use it automatically or do I have to point to it after finishing installing. Also will this preserve all my Thunderbird and Firefox settings?

Yes, everything will be preserved. Just reinstall the system and point that partition as /home, and make sure the partitioner indicates that it will NOT be formatted. I did this a few times recently.

---

### Post by margaf77 on 2007-07-30
> **tszanon said:**
> Yes, everything will be preserved. Just reinstall the system and point that partition as /home, and make sure the partitioner indicates that it will NOT be formatted. I did this a few times recently.

Do I point to it during install or once the install is complete?

And if I do it during install, where and how do I do it?

---

### Post by tszanon on 2007-07-30
> **margaf77 said:**
> Do I point to it during install or once the install is complete?

And if I do it during install, where and how do I do it?
During installation. Once you reach the partitioner, there is where it shall be done.

How to do it depends on how you are going to install the system: using the Live-CD (graphical installer) or using the Alternate CD (text-mode installer). I suppose you are using the Live CD, but, anyway, now I can't help you because I'm not at home. Tell us how you will install it and I'll get back to you later (or someone else will answer this).

---

### Post by aitorcalero on 2007-07-30
> **margaf77 said:**
> Do I point to it during install or once the install is complete?

And if I do it during install, where and how do I do it?

Whitin the instalation you can choose where /home is located, select manual partition (sorry but I do not know the exact name).

All your gnome, desktop, apps, settings will be restored.

---

### Post by margaf77 on 2007-07-30
> **aitorcalero said:**
> Whitin the instalation you can choose where /home is located, select manual partition (sorry but I do not know the exact name).

All your gnome, desktop, apps, settings will be restored.

Thanks!!

---

### Post by ReaderRat on 2007-07-30
Do you mean that you are using 2 (two) hard disks, or just one....not clear?

---

### Post by margaf77 on 2007-07-30
> **ReaderRat said:**
> Do you mean that you are using 2 (two) hard disks, or just one....not clear?

Yes, the /home partition is on a separate hard disk from the ubuntu partition. I also have a hard disk with my XP installation on it. 

In total the system has 5 HDD.

---

### Post by ReaderRat on 2007-07-30
I have just gotten back into Ubuntu, and I would not feel comfortable instructing you in how to partition.
```
sudo fdisk -l
```
Run the above, to list your drives & partitions and paste it here and someone will help you.

---

### Post by sugarland2k on 2007-07-30
To create a /home directory on a seperate partition, etc.  I would recommend a great site,

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck and keep learning...

---

### Post by margaf77 on 2007-07-30
> **ReaderRat said:**
> I have just gotten back into Ubuntu, and I would not feel comfortable instructing you in how to partition.
```
sudo fdisk -l
```
Run the above, to list your drives & partitions and paste it here and someone will help you.

All the partitions are set up already. I just have to reinstall. The /home directory is already on another partition. 

I was asking whether I needed to manually point out where the /home partition resides or would it automatically do this while installing

---

