---
title: "Can no longer boot windows"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-01-17
I installed Ubuntu and now have a dual boot install with 4 partitions.

They are in this order

NTFS file system(for my files)|Vista|Ubuntu|Swap file

After i resized and moved partitions i can no longer boot vista.


Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=d682287b-b981-4e06-9331-757e11fc1761 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

This is my fdisk-l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcff3aaff

Device Boot Start End Blocks Id System
/dev/sda1 1 21130 169726693+ 7 HPFS/NTFS
/dev/sda2 * 21131 28208 56851200 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 28209 30238 16299360 83 Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4 30238 30401 1315440 5 Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5 30238 30401 1315408+ 82 Linux swap / Solaris


And here is some of mymenu.lst

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1


Any ideas on what i need to do.

I have been trying to read up on thisbut i have no idea

---

### Post by meindian523 on 2008-01-17
Substitute the results of UUID="<something>" obtained by ```
blkid
``` for each partition in fstab and menu.lst.Looks like you have done too much foo stuff with your partitions.

Would like to add that this query is an epitome of excellence in providing enough data and what the OP did before the problem occurred,therefore the solution is just as simple.

---

### Post by dstew on 2008-01-17
How did you resize your partitions? If you resize a Vista partition with a program other than the Vista partition tool, you can damage it. It looks like that might have happened to your /dev/sda2 partition, which seems to be your bootable Vista partition.

---

### Post by bruce2000 on 2008-01-17
> **thedon_1 said:**
> I installed Ubuntu and now have a dual boot install with 4 partitions.

They are in this order

NTFS file system(for my files)|Vista|Ubuntu|Swap file

After i resized and moved partitions i can no longer boot vista.



Doesn't vista need to be on the first partition?

---

### Post by thedon_1 on 2008-01-17
You reckon it's worth moving vista to the far left?

---

### Post by bruce2000 on 2008-01-17
> **thedon_1 said:**
> You reckon it's worth moving vista to the far left?

It's what I'd try, I think windows expects to be on the 1st partition. Maybe someone else can confirm/refute this?

---

### Post by thedon_1 on 2008-01-17
It would still be /dev/sda2 though wouldn't it?

Or doesn't it matter, it just needs to be on the left?

---

### Post by bruce2000 on 2008-01-17
> **thedon_1 said:**
> It would still be /dev/sda2 though wouldn't it?

Or doesn't it matter, it just needs to be on the left?

Yeh give it a go, move it to the left

btw, you know its a good idea to make backups when working with partitions?

---

### Post by thedon_1 on 2008-01-17
Yep got my stuff on an external drive

---

### Post by zipperback on 2008-01-17
You might want to read over the following link.

I posted links to a few howto's which people have found helpful.

[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

- zipperback
:popcorn:

---

### Post by thedon_1 on 2008-01-17
Already read those links.

I moved the partition to the far left, but still no such luck.

Any ideas?

---

### Post by Lysander10 on 2008-01-17
> **thedon_1 said:**
> Already read those links.

I moved the partition to the far left, but still no such luck.

Any ideas?

If you have backups of everything, and an installation disc for Vista, it may, unfortunately, be easiest to just reinstall the entire system. If you don't have backups of everything, try to use an Ubuntu Live CD to move your files onto a flash drive. Changing your partitions around is always a risky business... try to plan ahead, and setup your partitions as you need them when you're installing the system next time.

---

### Post by thedon_1 on 2008-01-17
If i reformat the partition using Vista disc, is it pretty much 100% that when i get the GRUB loader re installed, it will boot?

---

### Post by Lysander10 on 2008-01-17
> **thedon_1 said:**
> If i reformat the partition using Vista disc, is it pretty much 100% that when i get the GRUB loader re installed, it will boot?

Well... nothing is ever 100%, but it's a more certain solution than anything else.

---

### Post by meindian523 on 2008-01-17
Did you try replacing the UUIDs?What were the results?

---

