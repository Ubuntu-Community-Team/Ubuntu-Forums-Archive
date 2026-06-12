---
title: "Double swap partition question"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by treesurf on 2007-06-17
I recently set up my laptop to dual boot Ubuntu and Vista.  It's working great!  

Anyways, in the process I have ended up with two swap partitions (don't ask how): /dev/sda5 and /dev/sda6.  When I look at /etc/fstab it only mentions /dev/sda6.  Does this mean that I can safely delete /dev/sda5?  

If so, will formatting it as FAT32 allow me to move files (small ones!) back and forth between Ubuntu and Vista?

thanks!

---

### Post by 5-HT on 2007-06-17
> **treesurf said:**
>    Does this mean that I can safely delete /dev/sda5?  
Yup.

> **treesurf said:**
>  If so, will formatting it as FAT32 allow me to move files (small ones!) back and forth between Ubuntu and Vista?

thanks!Yup. You can also enable Ext2 (will work for Ext3, just not with journaling)  support for windows and NTFS support for Linux (safely is another question though).

---

### Post by treesurf on 2007-06-17
Wow, that was fast.  Thank you.

---

