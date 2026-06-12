---
title: "Unable to mount the selected volume. ?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-12-10
Hi

I burned 3 data dvds (with Nero on a Windows pc), and tried to opened them in Ubuntu. Only one of them could be read in Ubuntu, when I tried the two others I got this message;

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so

When I booted into MS I had no problem to read and used the data on the two other dvds. Can you explain for me what the problem is?

Thanks

---

### Post by waffel on 2007-01-30
Okay I found the solution on another board on this forum.

All you have to do is to change your fstab file

sudo gedit /etc/fstab

and change the /media/cdrom0 string with

 /dev/hda        /media/cdrom0       iso9660,udf user,noauto     0       0

and the problem should be solved.

---

