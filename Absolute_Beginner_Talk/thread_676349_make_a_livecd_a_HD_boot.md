---
title: "make a livecd a HD boot"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by adi82 on 2008-01-23
i have a live cd of BackTrack3 and dont want to star from cd anymore (boot from HHD) but to make a dual boot as i have Ubuntu7.10.
any help?

---

### Post by mmb1 on 2008-01-23
I'm not familiar with backtrack, but you should find an "install" option somewhere in the Live CD's interface, what specifics do you need help with?

---

### Post by adi82 on 2008-01-23
> **mmb1 said:**
> I'm not familiar with backtrack, but you should find an "install" option somewhere in the Live CD's interface, what specifics do you need help with?
yea you right and gives me 3 hd1,(winXp),hd2(ubuntu),hd3(recovery)

if i chose hd1(XP) nothing happen because it is only readable and cant write on that partion.if i chose hd2 wich is my ubuntu i am afraid that is going to delete ubuntu.

---

### Post by mmb1 on 2008-01-24
Alright, you're going to have to create a new partition to install Backtrack on.  Go into synaptic, and  search for a program called "gparted", you can use it to downsize your windows partition, or if you've got enough space, you can make an entirely new partition.

If you need anything, feel free to ask.

---

### Post by adi82 on 2008-01-24
> **mmb1 said:**
> 
If you need anything, feel free to ask.

this is totally an other question
i did chages somewhere about wich will be the first in line on the boot menu
now i cant get from ubuntu in the pertion of windows.i get an error message(picture)

and...
is this right

> adi@adi:~$ sudo fdisk -l
[sudo] password for adi:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60116011

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3490 28033393+ 7 HPFS/NTFS
/dev/sda2 6306 7296 7953088+ c W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3 3491 6183 21631522+ 83 Linux
/dev/sda4 6184 6305 979965 5 Extended
/dev/sda5 6184 6305 979933+ 82 Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by mmb1 on 2008-01-24
Can you still boot into your windows partition?

(I'm no booting expert, by the way, so you may have to consult someone else, sorry)

---

### Post by adi82 on 2008-01-24
> **mmb1 said:**
> Can you still boot into your windows partition?

(I'm no booting expert, by the way, so you may have to consult someone else, sorry)

never mind it was easier than posting (didnt understood how was deleted)
just added in boot/grup/menu.lst :

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1



and did chkdsk/f

anyway thank you

---

