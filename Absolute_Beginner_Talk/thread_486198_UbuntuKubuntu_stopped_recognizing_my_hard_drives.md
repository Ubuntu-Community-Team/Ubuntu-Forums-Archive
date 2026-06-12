---
title: "Ubuntu/Kubuntu stopped recognizing my hard drives"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Eggnog on 2007-06-27
For some reason, GNOME and KDE both stopped recognizing my two hard drives and only recognize my CD/DVD drive and my floppy drive.  How can I fix this?  i have some files I want to interchange with my FAT32 shared partition but it's no longer recognized.

---

### Post by boralyl on 2007-06-27
What's the output of:
```
sudo fdisk -l
```
By the way, that is a lowercase 'L'

And what are the contents of the file /etc/fstab?

---

