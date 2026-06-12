---
title: "How to mount my Windows partition."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by adds2one on 2006-08-09
Hello, 

I just formated my entire hard drive and did a fresh install. I partitioned my 60GB drive into a 10GB NTFS partition for WinXP, a 10GB FAT32 partition to share and move things between WinXP and Linux, a 28GB ext3 partition for /home, a 2GB linux swap partition and a 10GB ext3 / partition.

I installed WinXP and then Ubuntu. Everything is great Except that when I go into Places->Computer and click on my Windows partition I get this message:

```
UNABLE TO MOUNT THE SELECTED VOLUME: 
error: device /dev/hda1 is not removable 
error: could not execute pmount


```

I looked in /etc/fstab and my Windows partition isn't there. I know that my Windows partition is /dev/hda1. Do I just need to add a line for this partition to /etc/fstab and create a directory for it to mount to such as /media/Windows?

If that is what I need to do what do I put into /etc/fstab? This is as far as I can do on my own as I don't understand the <ptions> <dump> and <pass> sections: 
 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda1       /media/Windows   NTFS

Can anyone help me with this?

---

### Post by Jagot on 2006-08-09
Read this:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

### Post by adds2one on 2006-08-09
Awesome, thank you!

---

