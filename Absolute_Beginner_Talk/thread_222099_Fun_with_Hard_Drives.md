---
title: "Fun with Hard Drives"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by MattKemp on 2006-07-24
So I recently (read: a few hours ago) converted over to Ubuntu and I've managed to sort most of my problems by looking stuff up on the Wiki.

When I transferred over I put all the stuff I wanted to keep on a second hard drive, which is of course under a FAT32 filesystem. Is there any way I can get Linux to read this? At the very least, is there any way I can get the data off it then format it to a linux filesystem?

Thanks for any help.

---

### Post by philippe_carlo on 2006-07-24
Don't worry, it's even easy. Just follow these steps (assuming you fat32 partition is hdb1, change as necessary):

(1) Do
```
sudo mkdir /media/data
```

(2) edit /etc/fstab as root as follows:
```
sudo gedit /etc/fstab
```

(3) Add the following line at the bottom (replace hdb1 as necessary)
```
/dev/hdb1       /media/data  vfat    rw,user,auto  0       0
```

(4) Type
```
mount /media/data
```

(5) Open the new disk icon on your desktop.

---

### Post by MattKemp on 2006-07-24
Awesome, thanks very much for your help :D

---

### Post by macogw on 2006-07-24
Hey, I have a question about that.  What if your harddrive ISN'T /dev/hdb1.  What if it's something else?  How do you find out what that something else is?

---

### Post by philippe_carlo on 2006-07-24
Good question:

type "sudo fdisk hda" (or hdb/hdb/hdc, if you want your 2nd/3rd/4th disk)
then you type "p" followed by enter. This prints all partitions with their fs type and device node.

---

### Post by macogw on 2006-07-24
Partitions?  What if you're talking about a totally separate piece of hardware--a removable hard drive?

---

### Post by philippe_carlo on 2006-07-25
Even those have partitions :-) But I guess your question is, how do I know which device a partition is on? If you plug in a USB drive, it becomes /dev/sd?

where the ? can be a,b, c, ... depending on how many other sd? drives there already are. Partitions on those are typically /dev/sd?x where x is a number.

If you plug something in, you can use ```
dmesg | tail
``` to see which device is assigned to it.

You can also get a list of storage devices by typing ```
sudo fdisk -l
```, I think. This will also list the partitions on them.

---

