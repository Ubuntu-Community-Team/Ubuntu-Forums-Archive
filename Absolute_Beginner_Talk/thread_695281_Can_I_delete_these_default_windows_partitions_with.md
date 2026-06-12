---
title: "Can I delete these default windows partitions without screwing up my computer?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by AlexLinuxUser101 on 2008-02-12
I already deleted the main windows partition, but I have two other partitions...
fat16 7.76/39.19 mb used
and
fat32 3.95/4.64 gb used
Are these windows partitions that I don't need if I am not using windows?  Thanks for the help in advance!

---

### Post by Rocket2DMn on 2008-02-12
Do you have any idea what is on them?  One might be a sort of boot partition, and the other a backup partition.  You can mount them in linux and see what's on them.
```
sudo mount -t vfat /dev/*yourdevice* /media/*yourmountpoint*
```
Where *yourdevice* is the correct partition seen in 
```
sudo fdisk -l
```
and *yourmountpoint* is the directory you created to mount at
```
sudo mkdir /media/*yourmountpoint*
```

If there doesn't seem to be anything on them, you can get rid of them.  You can either wipe using GParted on the Ubuntu LiveCD (System->Administration->Partition Editor) or using the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/").  Always have good backups before editing partitions, esp. if you plan to resize your root partition to use the new space.

---

