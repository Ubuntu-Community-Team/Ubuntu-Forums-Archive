---
title: "The longest problem ever!"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by old guy on 2007-04-28
This is my setup:

HD Master IDE-0

1. partition (ntfs) 10 GB windoz
2. partition (fat32) 70 GB data

HD Slave IDE-0

1. swap 512 MB
2. partition (etx3) 9.5 GB feisty
3. partition (ext3) 30 GB data

First when using the windows partition and turning off my computer would do a loud noise even without the case speaker connected. When i try to extract a big rar file from many pieces, some pieces will claim to be corrupt at random (in the fat partition), in both OS's. My Xubuntu installation forced a fdisk very often and discarded "inodes" untill the installation died. Grub had a hard time loading (2-3 minutes) and randomly claimed error 25 and 23 (i think) i checked the list and are disk read errors. So far everything points to a hard disk problem but yet i was too suspicious that 2 hard disks purchased at completely different times would die simultaneously so i replaced the IDE cable and installed Ubuntu feisty. Grub problems stopped and the loud noise stopped too. But logged in in windows the system will freeze at random times. But only all currently running applications, u can actually switch user with super+u and it will work normally (for a while). Ubuntu has no problems so far and u can work normally. I have no clue of wath is happening and i would really thank anyone who read this whole paragraph. Guide me to find my problem please. 

Thanks everyone, this are the best forums ever

---

### Post by Happy_Man on 2007-04-28
Ok, so your problem is your FAT partition is corrupted? And that your Windows install has stopped being nice to you? Well, this is pretty deep. For Windows, being Windows, I think the only thing you can do is to reinstall it fresh. As for your FAT partition, back it up, erase it, and replace it with an ext3 partition. There are drivers for Windows that enable it to read ext3 at [http://fs-driver.org](http://fs-driver.org). Hope this helps!

---

### Post by old guy on 2007-04-28
the ext3 idea is very good, ill apply it, yes i knw its not exactly the more stable OS... but then.. if sda1, sda2, and sdb1 showed errors and signs of corruption, waths the cause of all the problems?

---

### Post by Happy_Man on 2007-04-28
I honestly have very little idea....perhaps your hard drive is physically damaged?

---

### Post by old guy on 2007-04-28
thats wath i think too, thou any hard disk check shows any errors, my second hard disk is working well now and hasnt shown signs of problems, i think it would be safe to assume the hard drive isnt working correctly... now i must get some money... (T.T) thank u so much for all ur help.

But i wont give up just now, Ill try to use the old IDE cable since the freezing problem started when i changed it, ill post the results

---

### Post by old guy on 2007-04-28
same result with the old IDE, ecept that the scream sound returned when shutting down... thanks for ur help, i hav absolutely no idea


EDIT

i got new info:

$ sudo fdisk -l /dev/sda1

Disk /dev/sda1: 10.4 GB, 10487199744 bytes
255 heads, 63 sectors/track, 1274 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

~$ sudo fdisk /dev/sda1

The number of cylinders for this disk is set to 1274.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 2.
Partition 3 does not end on cylinder boundary.
Total allocated sectors 1701990412 greater than the maximum 20482812


can i somehow temporarily save that instalation? i need it working at least for the rest of the weekend

---

