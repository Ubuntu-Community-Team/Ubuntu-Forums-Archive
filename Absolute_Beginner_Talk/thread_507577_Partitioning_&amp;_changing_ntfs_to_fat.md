---
title: "Partitioning &amp; changing ntfs to fat"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-07-23
I have seven partitions on my 160gb drive as follows:

/dev/hdb1        fat32            3.25gb
               2        ntfs             40.34gb
               3        extended 105.39gb
               5        ntfs              52.02gb
               6        ext3             49.23gb
               7        linux swap     2.14gb
               4        ntfs               70.60 _**MB**_
 
This is the result of my original setting up of Ubuntu. It looks to me as though I need to do some drastic reorganisation here, any advice, or do I just reformat and start again. My xp pro I think is on 1 but as it does not appear on the boot menu I can only access it from the super grub disk. I have the xp and ubuntu disks.
Incidentally, except xp, everything works perfectly including the problem beryl.
I just feel that the hard drive is a bit of a mess and the 52 gb ntfs partition is not accessible to ubuntu.
Thanks in advance for any help.
Thanks in advance for any help..

---

### Post by ravsas3 on 2007-07-23
you forgot to mention your problem with xp, mate.
you can't see that in boot menu or what?
instead of removing linux just for booting into xp. you can use 'dd' to copy just the boot 512 bytes and put that in file and restore your 'ntldr' to  MBR and provide this link as an option for booting into linux

---

### Post by Benbow on 2007-07-23
Sorry, had to check on the flood situation here in the uk, family live in Worcester.
XP doesn't appear in the boot menu. I don't understand your last paragraph-- "*instead of removing linux just for booting into xp. you can use 'dd' to copy just the boot 512 bytes and put that in file and restore your 'ntldr' to MBR and provide this link as an option for booting into linux*"
could you explain please.

---

