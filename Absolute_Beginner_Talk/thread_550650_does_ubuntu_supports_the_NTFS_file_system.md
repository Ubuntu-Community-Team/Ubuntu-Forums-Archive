---
title: "does ubuntu supports the NTFS file system?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by jadoo_iii on 2007-09-14
does ubuntu supports the NTFS file system? or does anyone knows what particular file systems does ubuntu fully supports?

---

### Post by lisati on 2007-09-14
Yes - the NTFS file system is supported, but it is likely you will have to insall support for it

---

### Post by Steve1961 on 2007-09-14
By default Ubuntu can access and read files on ntfs partitions, and if you use the ntfs-3g driver it can also write to those partitions.  It can also read and write to fat32.  However, you would install Ubuntu to an ext3 partition, you cannot install it to ntfs.

---

### Post by newman on 2007-09-14
It would be really great if you could install ubuntu on an NTFS partition, but unfortunately you can't.

---

### Post by ukripper on 2007-09-14
Here is lil HOWto for ntfs-3G -
For EDGY 6.10
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

For Feisty Fawn -
[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

---

### Post by hyper_ch on 2007-09-14
> **newman said:**
> It would be really great if you could install ubuntu on an NTFS partition, but unfortunately you can't.
Why would that be great?

Instead of writing to ntfs from linux I'd write to ext3 from windoze.

---

### Post by Tyke91 on 2007-09-14
yeah, to be honest, i'd rather install windowz on ext3... installing ubuntu on ntfs would lead to having the defrag every month again :(

---

### Post by newman on 2007-09-14
> **hyper_ch said:**
> Why would that be great?

Instead of writing to ntfs from linux I'd write to ext3 from windoze.

Because NTFS is a superior file system. ext3 is slower and my hard disk is constantly seeking.

---

### Post by Lord Illidan on 2007-09-14
> **newman said:**
> Because NTFS is a superior file system. ext3 is slower and my hard disk is constantly seeking.

Umm...how can you prove that NTFS is faster than Ext3, when you are running different OSes? Probably it is some bloat in Ubuntu..

---

### Post by LowSky on 2007-09-14
This is how i remember how the two file systems work...i could be very wrong, but this is what I remember:

The reason you need to Defrag NTFS is because it moves the files you use often to a place on the hard drive that is easier to find... ext3 doesnt move files to new spots but instead logs the file so it shouldnt be moved unless a user requests it. NTFS/Windows might seem faster but its really makes your hard drive look like swiss cheese instead of just using one block of space it uses 15.

---

