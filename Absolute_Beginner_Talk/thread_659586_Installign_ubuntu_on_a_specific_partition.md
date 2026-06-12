---
title: "Installign ubuntu on a specific partition"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by childofstrings on 2008-01-05
Hey guys,
Quick noob question about installing Ubuntu. I just set up a new slave drive and I want to put Ubuntu on a specific partition so the rest of the drive can be used for storage of my windows stuff. How should I go about doing this in the install process that comes with the live cd?

---

### Post by Rocket2DMn on 2008-01-05
I'm not sure if you are able to format a partition with ntfs out of the box with Ubuntu, but to get started you can surely partition the drive to put Ubuntu on it and leave X gigs left unformatted.  You CAN format with FAT32, but if NTFS is what you want, you can format the remaining space from within windows to NTFS.
You will need to install ntfs-3g to read/write that partition from within Ubuntu.

---

