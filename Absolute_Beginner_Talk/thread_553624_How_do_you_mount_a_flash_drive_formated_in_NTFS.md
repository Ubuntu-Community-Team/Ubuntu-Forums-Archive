---
title: "How do you mount a flash drive formated in NTFS"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-09-18
I have formated my flash drive to NTFS how do I now mount the USB flash drive.

---

### Post by splintercellguy on 2007-09-18
Install the ntfs-config package in Synaptic, and run the NTFS Configuration Utility. After that, the automounter should be able to mount the NTFS partition to a /media mount point automatically. If this does not work, please post the output of sudo fdisk -l with the flash device plugged in.

---

