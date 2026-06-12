---
title: "[SOLVED] Delete Windows Partition"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by enazguy on 2008-04-15
i recently installed windows 98 on my computer because ubuntu seemed to not be working. i got ubuntu to work, and now want to delete the windows 98 partition. any ideas on how to do that?

---

### Post by sdowney717 on 2008-04-15
open a terminal window and type 
sudo gparted
this will let you select and delete create partitions.
just dont delete ubuntu.

---

### Post by Sidewinder1 on 2008-04-15
You may already have gparted on your Live CD (if that's what you used to install ubuntu). Just boot to the live cd and repartition. But as sdowney said be careful not to delete / repartition your ubuntu (probably ext3 or ext2) partition. If you need clarification just ask...

---

### Post by namegame on 2008-04-15
in my experience, if you just deleted a partition using gparted, you will not have access it as it will be "unallocated space." However, you do have the option of expanding your Ubuntu partition into this space, or you can create two separate "drives" for storage purposes, or you could use the space to experiment with other Distros.

---

### Post by ethoxyethaan on 2008-04-15
install gparted

```
sudo apt-get install gparted
```

type this to run the program

```
sudo gparted
```

dismount the Windows partition and format it to your likings.

---

### Post by enazguy on 2008-04-15
thanks i downloaded and installed gparted fine.

---

### Post by canadastitan on 2008-04-16
Hi I Deleted my windows partition on my Western Digital 500 gig MYBOOK AND SET 3 NEW PARTITIONS 1=  /dev/sdb1/   ..EXT2..463 GiB Primary ..2= /Ddev/sdb2/..1.36 GiB.Linux Swap ..3= /dev/sdb3/ ..1.36 GiB.extended
I had previously set label to msdos..
The problem is when i try to mount the external usb drive i get error message
(( Cannot mount volume) The volume uses the EXT3 file system which is not supported by your system)
..Which is very strange as I am running ubuntu 7.10 and my main hdd is the ext3 format ,but i set format on external hdd  to ext2 using (sudo gparted)..I actually need the external to be EXT2..??  IS THIS A BUG IN UBUNTU..Or did I do something wrong..??

---

