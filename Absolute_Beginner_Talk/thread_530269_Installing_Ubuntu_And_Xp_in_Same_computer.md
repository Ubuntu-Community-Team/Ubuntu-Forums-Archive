---
title: "Installing Ubuntu And Xp in Same computer"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by azzla79 on 2007-08-20
hi everyone,
i have a concern with installing ubuntu on my computer! i have setup 5 partitions on my hard drive and have now put ubuntu onto a bootable cd. i have loaded up ubuntu and go to install it but cant see where it is actually getting saved to.  it says that its going to format area and then save etc and im concerned that im going to lose some data from within my XP folders etc.  i have partition 5 on my computer set aside for ubuntu.  how do i access this partition when installing it??

---

### Post by LaRoza on 2007-08-20
> **azzla79 said:**
> hi everyone,
i have a concern with installing ubuntu on my computer! i have setup 5 partitions on my hard drive and have now put ubuntu onto a bootable cd. i have loaded up ubuntu and go to install it but cant see where it is actually getting saved to.  it says that its going to format area and then save etc and im concerned that im going to lose some data from within my XP folders etc.  i have partition 5 on my computer set aside for ubuntu.  how do i access this partition when installing it??

Ubuntu will need two partitions, one for the os, and one for swap. Swap should be around 512 MB and the OS partition should be at least 10GB, if you want to have room for installing programs.

I suggest partitioning your disk with 4 partitions, assuming you are only use the XP partitions at the moment.

The partitions should be:
0. XP - NTFS
1. Ubuntu -EXT3 ~10GB
2. <DataPartition> This is for data you will share between XP and Ubuntu, FAT 32 is a good format if you don't need to use files larger than 4 GB
3. Linux-Swap - 512 MB

---

### Post by maldojr88 on 2007-08-20
homie...u dont even need what the fella wrote up here(what he said is totally right)
u dont even need to partition you harddrive...all u gotta do is put in the live cd...and it will
give u an option for installing linux....it will create the partitions on automatically and there is an option to not overwrite the the data thats already on the hard drive...
it will not delete ur xp stuff

---

### Post by Hobo Joe on 2007-08-20
> **azzla79 said:**
> hi everyone,
i have a concern with installing ubuntu on my computer! i have setup 5 partitions on my hard drive and have now put ubuntu onto a bootable cd. i have loaded up ubuntu and go to install it but cant see where it is actually getting saved to.  it says that its going to format area and then save etc and im concerned that im going to lose some data from within my XP folders etc.  i have partition 5 on my computer set aside for ubuntu.  how do i access this partition when installing it??

Would you mind booting into the live CD and opening the terminal and typing this command?
```

sudo fdisk -l

```
(that's a lowercase 'L', not the #1.) That will tell us what and where your partitions are.

---

### Post by StooJ on 2007-08-20
If you are comfortable enough to create partitions yourself, then I'd guess you'd probably prefer to manually choose what partition is used for what, rather than have the wizard choose for you.

The trick is to know which partition is which. Your XP install will *probably* be located on /dev/hda1 (or sda1 if you have a sata drive)

I found [Gparted]("http://gparted.sourceforge.net/") to be the easiest way of working out which drive is which, before I learned of fdisk and began to use the console.

Once you know where your XP partition is, install Ubuntu on another partition (at least 10gb in size). You can also mount your /home directory on a 3rd partition (as big as you like)

Providing you don't tick the format box beside your XP partition, XP will be safe.

[http://psychocats.net/ubuntu/partitioning]("http://psychocats.net/ubuntu/partitioning") is a great guide on planning your partitions. The site was invaluable to me for a lot of other things too, and is very easy to follow.

---

### Post by Hobo Joe on 2007-08-20
> **StooJ said:**
> If you are comfortable enough to create partitions yourself, then I'd guess you'd probably prefer to manually choose what partition is used for what, rather than have the wizard choose for you.

The trick is to know which partition is which. Your XP install will *probably* be located on /dev/hda1 (or sda1 if you have a sata drive)

I found [Gparted]("http://gparted.sourceforge.net/") to be the easiest way of working out which drive is which, before I learned of fdisk and began to use the console.

Once you know where your XP partition is, install Ubuntu on another partition (at least 10gb in size). You can also mount your /home directory on a 3rd partition (as big as you like)

Providing you don't tick the format box beside your XP partition, XP will be safe.

[http://psychocats.net/ubuntu/partitioning]("http://psychocats.net/ubuntu/partitioning") is a great guide on planning your partitions. The site was invaluable to me for a lot of other things too, and is very easy to follow.

This explains very well how to do it, but before you change the partition size of Windows, make SURE you have empty space on the end of it, and then defrag. Lots of times. If you don't defrag and check that you have empty space, you are risking serious data loss/corruption.

---

