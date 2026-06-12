---
title: "[SOLVED] Partition Question"
date: 2007-08-03
forum: Apple Intel Users
---

### Post by negatifzeo on 2007-08-03
Hi all, Im on an intel macbook here. I've got a couple of questions regarding partitions. First, it's my understanding that in order to move files betwen my ubuntu partition and my mac partition I need to make a partition that can be read by both os's. What format does this partition need to be in to accomplish this? Second, what software should I use (mac or linux)/how do I resize partitions? Thanks!

---

### Post by loserboy on 2007-08-03
Fat32 is a good file system (for a shared partition)


when you boot into the livecd and click the install icon, one of the steps it will bring up GParted (partitioner)

---

### Post by cyberdork33 on 2007-08-03
osx can read ext3 (ubuntu default) and ubuntu can read hfs+ (osx default) no need for third partition

---

### Post by TravMan63 on 2007-08-03
You did state 'read' from other partitions - so cyberdork33's info would work.

If you want to read AND write - FAT32 works with Ubuntu... I'm not sure about MAC - but I bet it's good.

Gparted...

Good luck

---

### Post by cyberdork33 on 2007-08-03
fat32 works best because it has no permissions structure, but you can READ and WRITE hfs+ with Ubuntu.

---

### Post by negatifzeo on 2007-08-04
> **cyberdork33 said:**
> fat32 works best because it has no permissions structure, but you can READ and WRITE hfs+ with Ubuntu.
Well I can't write MY hfs+ with ubuntu! CAn you tell me how I can set mine up so that I can? And what software should I use to resize partitions?

---

### Post by cyberdork33 on 2007-08-04
> **negatifzeo said:**
> Well I can't write MY hfs+ with ubuntu! CAn you tell me how I can set mine up so that I can? And what software should I use to resize partitions?
It has to be non-journeled to be mounted with write permissions.

In OSX, 
```
$ diskutil enableJournal /dev/disk0s2
$ diskutil disableJournal /dev/disk0s2
```

I am guessing for the disk designation. You might have to change it to the correct value. you can use 'diskutil list' to find the different partition names. Make sure that you use the enable command first as there is a bug that cause it to not actually disable.

---

