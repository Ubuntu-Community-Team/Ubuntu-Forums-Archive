---
title: "edgy about installing grub"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by klein de usa on 2007-12-08
hi
i'm getting ready to push that button that says install, i'm using ubuntu 7.10 live cd .
i would like to put grub on the second hard drive, 3rd partition.

hd0= xp and ubuntu 6.10 

hd1= 8mb bootit mbr===/dev/sdb0
         20g xp files     ===/dev/sdb1
         20g xp files     ===/dev/sdb2
         ex3 /               ===/dev/sdb3
          linux/sw         ===/dev/sdb4

when i went into the advanced option it gave me (hd0) changing that to (/dev/sdb3) should put grub on the second hard drive on the third partition ? right? 
i'v messed up grub before and it isn't fun at all.

---

### Post by klein de usa on 2007-12-08
hi
i need to correct my self, second hard drive 4th partition /dev/sdb3 sorry

---

### Post by fain on 2007-12-08
I usually put grub on hd0 or sda1/hda1 This over writes the windows boot loader and detects all boot able partitions/disks in your system.

---

### Post by klein de usa on 2007-12-09
hi
i use bootit ng, it does the booting for me i just have to put stage 1 grub in the right partition, sometimes the numbering gets confusing , i pushed install we will see

---

