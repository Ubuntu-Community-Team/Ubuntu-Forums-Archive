---
title: "Rename ReiserFS partion."
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Surreal Killa on 2008-01-30
I formatted my external hard drive with gparted and it auto-labelled it to 'disk' and in Computer it is labelled '232.9 GB Volume: disk'. Anyways, so I want to rename it to 'Data'. So I unmount the volume then go into terminal and put in "sudo reiserfstune -l Data /dev/disk" and it outputs this:

bread: Cannot read the block (2): (Is a directory).
reiserfs_open: bread failed reading block 2
bread: Cannot read the block (16): (Is a directory).
reiserfs_open: bread failed reading block 16

reiserfs_open: the reiserfs superblock cannot be found on /dev/disk.
reiserfstune: Cannot open reiserfs on /dev/disk

I don't understand why it isn't working. I even tried mounting the volume and doing it, and changing the address from /dev to /media but still no luck.

---

### Post by dcstar on 2008-01-30
> **Surreal Killa said:**
> I formatted my external hard drive with gparted and it auto-labelled it to 'disk' and in Computer it is labelled '232.9 GB Volume: disk'. Anyways, so I want to rename it to 'Data'. So I unmount the volume then go into terminal and put in "sudo reiserfstune -l Data /dev/disk" and it outputs this:

bread: Cannot read the block (2): (Is a directory).
reiserfs_open: bread failed reading block 2
bread: Cannot read the block (16): (Is a directory).
reiserfs_open: bread failed reading block 16

reiserfs_open: the reiserfs superblock cannot be found on /dev/disk.
reiserfstune: Cannot open reiserfs on /dev/disk

I don't understand why it isn't working. I even tried mounting the volume and doing it, and changing the address from /dev to /media but still no luck.

/dev/disk is a system generated folder, not something you can - or should - touch.

Find the correct identifier for your volume and use that.

---

### Post by Surreal Killa on 2008-01-30
Ah. I was thinking about that, haha. I suppose it would be sdb1, I will try it. Thanks. :)

---

