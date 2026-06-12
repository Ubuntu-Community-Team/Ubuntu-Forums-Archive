---
title: "[SOLVED] How to have permission to the window partition?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-11
How do you have permission towards your windows partition, because the partition on my linux is running out of space and i would like to be able to access it so i can move my videos to my other partition
Thanks!

---

### Post by irish_flu on 2007-08-11
Assuming you have Windows XP with the NTFS filesystem, search these forums for "mount NTFS" and "ntfs-3g".

By default in Ubuntu you can mount NTFS drives, but they're read-only.  NTFS-3g is a driver (which you can install through Synaptic) that lets you write to them.

---

### Post by bren on 2007-08-11
run the following in terminal


sudo apt-get install ntfs-3g

then run 

ntfs-config

you can now access ntfs drive

---

### Post by kinngg on 2007-08-11
Thanks to the both of you! i can now copy and paste files! thanks!

---

