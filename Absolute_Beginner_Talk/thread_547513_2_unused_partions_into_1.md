---
title: "2 unused partions into 1?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-09-10
I have a 320GB hard drive with 2 unused partitions. Can I combine those two into 1?

---

### Post by Sef on 2007-09-10
First back up your files or hard disk.  

Then use [GParted]("http://GParted.sourceforge.net") to combine them.

---

### Post by vanadium on 2007-09-10
As this is the Beginners forum, I will elaborate a bit. As a preliminary note, the partitions can only be joined if they are in a contiguous space on the disk, i.e., there should be no other partition in between.

* You can load gparted typing "gksudo gparted" at the command line (or after pressing Alt+F2).
* On the top right corner, be sure the drive you want to address is selected
* Make sure the partitions you want to join are not mounted. If they are, you need to  unmount them first. You can do this by right-clicking them in gparted.
* You will need to delete the right-most partition.
* Then, you can enlarge the remaining partition to fill the freed space. When done, click the "Apply" button to apply the changes to disk.

If both "unused" partitions were listed in /etc/fstab, you will need to remove the entry for the partition that does not exist anymore. If none were mounted in /etc/fstab, then you might want to add an entry for your enlarged partition such that it is automatically available after startup.

---

