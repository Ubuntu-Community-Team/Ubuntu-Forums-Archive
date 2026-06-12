---
title: "Formatting a Mac hard drive to FAT32?"
date: 2005-08-30
forum: Apple PPC Users
---

### Post by Lazyhound on 2005-08-30
Is it possible to use the PPC discs to format a hard drive to FAT32, and where would I instructions on how to go about doing so? Thanks in advance.

---

### Post by stuporglue on 2005-09-24
You could make a partition into a dos format, but you can't partition the whole disk in PC format. OpenFirmware only knows how to boot OSs off of certain types of partitions (UFS, HFS, and HFS+). For a single partition, you'd use mkfs.msdos

That's why yaboot gets it's own partition too -- OF can't boot off of ext3 or whatever you've got Linux using. It boots OF boots yaboot which is smart enough to boot Linux off of ext3.

---

