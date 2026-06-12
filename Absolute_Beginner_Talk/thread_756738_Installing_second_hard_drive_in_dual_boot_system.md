---
title: "Installing second hard drive in dual boot system"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by chperry on 2008-04-16
I have a Dell Dimension 4600 with 80GB primary drive that is split between XP pro and Ubuntu.  I want to add a second drive and create two partitions: an NTFS partition for XP and a partition for Ubuntu for file storage.  What is the best way, and tools, to do this?  The drive will be an IDE ATA.

I have installed drives in Dos and Windoze systems before.  I just want to know if there are any "tricks" to making this easy with Ubuntu.

---

### Post by hums07 on 2008-04-16
Partition and format the drive using **gparted**.
Then edit /etc/fstab to make them automounted during Ubuntu start up.
Windows will recognize and assign a letter to the second drive automatically.

---

### Post by maniac_X on 2008-04-16
> **chperry said:**
> I have a Dell Dimension 4600 with 80GB primary drive that is split between XP pro and Ubuntu.  I want to add a second drive and create two partitions: an NTFS partition for XP and a partition for Ubuntu for file storage.  What is the best way, and tools, to do this?  The drive will be an IDE ATA.

I have installed drives in Dos and Windoze systems before.  I just want to know if there are any "tricks" to making this easy with Ubuntu.

No tricks needed really. Both OS' will see the drive once installed and formatted. All you need to do is install(jumper set to slave preferably), format/partition, viola! you have more space ;)

---

