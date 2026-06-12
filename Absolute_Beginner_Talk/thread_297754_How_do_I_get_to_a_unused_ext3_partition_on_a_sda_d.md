---
title: "How do I get to a unused ext3 partition on a sda drive"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-11-11
Hi
I have a 60 g drive that I have plugged into a USB port.

The drive has 3 partitions  The First is an Edgy System (that I am not currently using) , The second is a Linux Swap and the third is a ext3 partition.

My question is can I use the third partition to store backup files?

If I can use the third partition how do I get to it?

I only see the first partition now.

Thanks for any help

---

### Post by bodhi.zazen on 2006-11-11
You need to mount the partition and add an entry in [fstab](http://ubuntuforums.org/showthread.php?t=283131).

Try```
sudo mkdir /mnt/data
sudo mount /dev/sda3 /mnt/data
sudo chmod 777 /mnt/data
```

fstab: > /dev/sda3 /mnt/data auto auto,users 0 0

---

### Post by kent41 on 2006-11-11
> **bodhi.zazen said:**
> You need to mount the partition and add an entry in [fstab](http://ubuntuforums.org/showthread.php?t=283131).

Try```
sudo mkdir /mnt/data
sudo mount /dev/sda3 /mnt/data
sudo chmod 777 /mnt/data
```

fstab:

I get an err "must specify the filesystem type"
with this command

```
sudo mount /dev/sda3 /mnt/data
```

---

### Post by bodhi.zazen on 2006-11-11
> **kent41 said:**
> I get an err "must specify the filesystem type"
with this command

```
sudo mount /dev/sda3 /mnt/data
```

Can you psot the output of ```
sudo fdisk -l
```
That is a small "L"

---

### Post by kent41 on 2006-11-11
> **bodhi.zazen said:**
> Can you psot the output of ```
sudo fdisk -l
```
That is a small "L"


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546   83  Linux
/dev/sda2            3188        3472     2289262+  82  Linux swap / Solaris
/dev/sda3            3473        7296    30716280    5  Extended

---

### Post by bodhi.zazen on 2006-11-11
It looks like the patition is an empty extended partition.

Use gparted or fdisk/mkfs.ext3 to create and then format a partition. Then mount as above.

```
sudo fdisk /dev/sda
```
Make a partition.
```
mkfs.ext3 /dev/sdax
```Where x is your new partition (likely sda4)

---

### Post by kent41 on 2006-11-11
> **bodhi.zazen said:**
> It looks like the patition is an empty extended partition.

Use gparted or fdisk/mkfs.ext3 to create and then format a partition. Then mount as above.

```
sudo fdisk /dev/sda
```
Make a partition.
```
mkfs.ext3 /dev/sdax
```Where x is your new partition (likely sda4)

Yes that is how I created the partition but I formatted it as FAT 32 is that the problem?

---

### Post by bodhi.zazen on 2006-11-11
No, if it is formatted it should mount.

try:```
sudo mount /dev/sda3 /mnt/data -t vfat
```

---

### Post by kent41 on 2006-11-11
> **bodhi.zazen said:**
> No, if it is formatted it should mount.

try:```
sudo mount /dev/sda3 /mnt/data -t vfat
```

Im sorry but I must leave for 20 minutes I be back . Thanks for the help

---

### Post by kent41 on 2006-11-11
**Bodhi.zazen**

I found the problem with your help. I said that I had created a ext3 partition but in fact I created a extended partition by mistake.

I used a Gparted disk and created a primary partition and your commands worked with no errors. I now have a second usbdisk named usbdisk-1 and I can move files into it.

This is the first time that I have made partitions and I have learned from my mistakes. Thanks for sticking with me.

Thank you soooo much

---

### Post by bodhi.zazen on 2006-11-11
> **kent41 said:**
> **Bodhi.zazen**

I found the problem with your help. I said that I had created a ext3 partition but in fact I created a extended partition by mistake.

I used a Gparted disk and created a primary partition and your commands worked with no errors. I now have a second usbdisk named usbdisk-1 and I can move files into it.

This is the first time that I have made partitions and I have learned from my mistakes. Thanks for sticking with me.

Thank you soooo much

Any time :)

---

