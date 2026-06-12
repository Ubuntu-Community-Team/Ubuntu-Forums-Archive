---
title: "Partitioned Hardrive mistaken for CD-Drive"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by CajunPirate on 2008-01-14
Totally new, but excited by this.  Running Feisty Fawn, on a 30 gig Dell Inspiron, weak, but fun to mess around on.

Exposition: I partitioned the hardrive on install: 10 gig for "Filesystem" and 20 gig for storage.

Problem: Filesytem is accessible and has hardrive icon.  The other is named "CD-ROM 1" and reads "Unable to Mount Volume: mount: special device /dev/hdc does not exist" when clicked.

How can I mount the 20 gig and get Ubuntu to recognize it as storage space?
Any help is appreciated!

---

### Post by Tekno_Cowboy on 2008-01-14
First make a directory in /media/ with whatever name you want it to be
sudo mkdir directoryname

example

```
sudo mkdir harddisk
```

Then mount the drive

```
sudo mount /dev/hdc2 /media/harddisk
```

I'm assuming that hdc2 is the drive from your post. This probably won't work if the partition is in ntfs format.

---

