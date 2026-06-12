---
title: "Create partition after Ubuntu 7.0.4 install"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by dizzy_fingers on 2007-08-12
Hello again.

I just installed Ubuntu 7.0.4 in one of my hard drives and I want to create a new partition in the same drive that I've installed Linux.


Specificaly:
I have 2 hard drives.
One is FAT32 and is used for Windows XP.

The other one is ext3, **60GB** and I have created 2 partitions in it.
One sized 6GB where I have Ubuntu installed and one 1GB for swap memory.
As you can understand, by mistake, I forgot to create a third partition for the rest of the 53GB.


**So, the main question is: how can I create this partition, in a way that my Ubuntu install is not destroyed, and if possible in FAT32 format so that my Windows can also use it (newbie question: is NTFS editable too by Windows or is it only FAT32?)**


Thanks in advance :).

---

### Post by MenZa on 2007-08-12
You can use GParted to edit your partitions. Install it from the repositories (*sudo apt-get install gparted*). And you can attach some of the left-over space to other partitions, but to do this, they must be unmounted (e.g. in the case of Ubuntu, you cannot have your system running while editing the root partition).

To edit your Ubuntu root partition, you could use something like the [GParted LiveCD](http://gparted.sourceforge.net/livecd.php) and add some of the leftover space to your Ubuntu partition.

And yes, NTFS is editable by Windows *only* (unless you use third-party utilities), but for the best Windows-Linux interoperability, I suggest you use FAT32 on the disk---alternatively ext3, as there are some pretty good ext3 drivers for Windows out there!

---

### Post by mikewhatever on 2007-08-12
Use the live cd. GParted is already there under System>Administration> Gnome Partition Editor.

---

### Post by dizzy_fingers on 2007-08-12
Thank you very much guys.

I installed GParted and created the partition in just 2-3 minutes.

Didn't expect it would be that easy (that's something I've said more than a dozen of times the last couple of days I've been working on Ubuntu :D).

Thank you for the help and the information.

I'll keep that GParted LiveCD advice for the future when my root partition runs out of space.

Have a nice day.

---

