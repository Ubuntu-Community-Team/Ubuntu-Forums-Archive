---
title: "Install XP - too many Partitions taken by XP?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by rwin on 2006-09-29
Hi,

I set up my Ubuntu on a laptop, am satisfied with ubuntu. But i wanted to reinstall XP and now the XP setup says, i can't set a new partition for XP, after i deleted the old one. stittin right in the setup, it's suggesting 'to remove another partition', but it certainly doesn't seem to be an option.

background: i've installed win XP and Ubuntu on the same hdd, ubuntu with the standard 3 partitions, win xp with one.

What can I do? i wasn't forseeing this, i only looked for how to fix grub after installing win.

Has anybody an idea?

THANKS!

Rajko

---

### Post by rwin on 2006-09-29
think someone could get wrong what i wrote, i definetely want to keep my ubuntu, that's making the trouble. but i also will need the xp for some software to run on.

doesn't have anybody a clue?
could boot with the live cd, move my home partition over to root and then be able to temporarily remove the partition that held home in the xp installation process?

think it's probably not making much sense, is it?

Rajko

---

### Post by blx_286 on 2006-09-29
> **rwin said:**
> Hi,

I set up my Ubuntu on a laptop, am satisfied with ubuntu. But i wanted to reinstall XP and now the XP setup says, i can't set a new partition for XP, after i deleted the old one. stittin right in the setup, it's suggesting 'to remove another partition', but it certainly doesn't seem to be an option.

background: i've installed win XP and Ubuntu on the same hdd, ubuntu with the standard 3 partitions, win xp with one.

What can I do? i wasn't forseeing this, i only looked for how to fix grub after installing win.

Has anybody an idea?

THANKS!

Rajko

A little more info please -
What is the size of your hard drive?
How many partitions are on this drive and what type?
How much free space is available on this drive?

---

### Post by jorn on 2006-09-29
Maybe it would help you to take a look at the application "gParted", it's in the Packetmanager. It will give you an overview and can repartition the partitions that are nor in use. If you want to repartition your hole drive, download the gParted live cd. It runs from you memory while the harddisk is unmounted.

---

### Post by geezerone on 2006-09-29
Could you list the disk setup shown with Qtparted for instance?

You are allowed 4 Primary partitions. My first Primary partition is NTFS for windows, then I have an extended partition which contains a logical data NTFS partition for windows data and an /ext3 logical for /home directory. Then I used the next two primary partitions for ext3 swap and /

---

### Post by jorn on 2006-09-29
Or open terminal and paste:
> sudo fdisk -l

---

