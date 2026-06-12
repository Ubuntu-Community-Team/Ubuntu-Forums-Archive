---
title: "Formatting ext3 issues"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by TURNER on 2008-02-19
I think iam going insane, been trying for ages now to format an external scsi drive (currently formatted fat 32) to linux ext3..

ok...first I check fdisk -l

the drive is present and already has a partition

Device Boot  start   end       id  system

/dev/sdb1     1         12162  b   W95 FAT32

so...then I mkfs.ext3 /dev/sdb1

it goes through the process and doesnt give any errors. however when I check fdisk -l again I get the same read out that the drive is formatted FAT32...

Any ideas???

---

### Post by Bachstelze on 2008-02-19
That's normal, the identifier of a partition is idependent from the filesystem there is on it. To thange the partition id to "Linux", do a *sudo fdisk /dev/sdb* and follow the instructions (from the top of my head, you type "t" to change a parittion's type, the "Linux" partition type is 82).

---

### Post by TURNER on 2008-02-19
thanks for the feedback, i truly hope that it is such a simple resolution...

you were right...t is the correct option in fdisk...however now it tells me that no partiion is defined....which it quite obviously is....:confused:

---

### Post by TURNER on 2008-02-19
sorry its me being dumb..../dev/sdb :) without the partition

---

### Post by oedha on 2008-02-19
have you try gparted ? 
sudo apt-get install gparted

---

