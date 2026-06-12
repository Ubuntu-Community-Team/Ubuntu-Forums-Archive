---
title: "how do i zero an external hard drive"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by wimpytx on 2007-08-03
how do i do this when i dont have write permission and the disk is partitioned into 6 or 7

---

### Post by louistan3 on 2007-08-03
maybe clean the MBR? that takes out the partition table?

just a suggestion :)

---

### Post by heimo on 2007-08-03
> **wimpytx said:**
> how do i do this when i dont have write permission and the disk is partitioned into 6 or 7

Do you want to securely wipe out all the data on external disk, or just empty it and create new filesystem / partitioning? If you're first user on that Ubuntu, you also have root permission which means you have full permissions when necessary (using a sudo command). You could probably use disk partitioner like gparted or qtparted, or if you prefer command line, fdisk to remove partitions, then recreate a new one. If you need a secure zeroing of the disk, you'll need to use other tools like wipe or eraser.

---

### Post by Warren Watts on 2007-08-03
I'm not sure I understand what it is you are asking exactly....

Do you want to re-partition the drive?
Use gparted the Gnome Partition Editor

Or do you want to wipe the drive clean, filling it with zeros, perhaps for security reasons?

---

### Post by Alterax on 2007-08-03
(assuming that your internal drives are IDE, they will be in /dev as hd[1-8])

Your external drive will have its own entry in /dev/.  Try mounting it and using df -a at the prompt to find out what the drive volume number is.  Mine comes up as /dev/sda1, /dev/sda3, and /dev/sda4 (example).

Once you find out, umount the discs.  You don't want them mounted for the next couple of steps.

Next I would use sudo fdisk /dev/sda and proceed to delete each partition on the drive.

Finally, I would use "sudo dd if=/dev/zero of=/dev/sda"  (or /dev/sdb or whatever it is)
Caveat:  MAKE SURE YOU PUT THE RIGHT HARD DRIVE NAME HERE OR YOU WILL HOSE YOUR SYSTEM.

That will overwrite your hard drive with zeroes.  Once this is done, you may do whatever you wish with them:  Make new partitions and give it new filesystems or if you are feeling very adventurous/frisky/paranoid/bored you can store files raw on the unpartitioned drive using dd.

--Alterax

---

### Post by johntelthorst on 2008-03-20
If I unmount the drive, it seems like I wouldn't be able to use fdisk on that drive?

---

