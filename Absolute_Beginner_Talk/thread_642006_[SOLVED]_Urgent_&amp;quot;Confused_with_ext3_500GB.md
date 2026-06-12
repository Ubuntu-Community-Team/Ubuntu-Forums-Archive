---
title: "[SOLVED] Urgent: &amp;quot;Confused with ext3 500GB drive - space &amp;amp; name&amp;quot;"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-16
**Update**
*I've changed the disk to NTFS now as Vista can't read/write to ext3, duh.* well now with NTFS I get 465.8GB and easy to rename.
========================================
========================================

**Original Thread**
I just formated my 500GB (My Book) drive to ext3 using "Partition Editor - **GParted 0.3.3**".

When I bought the drive, it came as a fat32 drive and had some google and other files on it.

first I tried using QTparted *(took 5 seconds)* that did format but later showed up as error, so I used GParted *(took 6.5 minutes)* and it went all well and I mounted the drive now as an ext3 drive.

**Question**

1. The drive in size shows as **465.76**GB, but it shows **7.50**GB used and **458.26**GB unused, how can that be, I just formated the whole drive and have put nothing on it, so what is using the **7.50** GB? (please see picture)

2. It shows a **Lost+Found** folder, I don't know what its for and why it was created, it shows up empty inside. (I'ld prefer it not to be there, can I rid of it?)

3. How can I rename my drive again to **"My Book"**

==================

should I reformat the drive again, did I make any mistakes?

---

### Post by kajillin on 2007-12-16
ive ran into this problem aswell, i couldnt fully partition with g parted so i ran the text based installer again, formatted that way and it cleared the whole drive.

Hope this helps, Cheers

Edit: but it wast an external drie :(, some external drives have untouchable portions with apps, etc..
I know with my external drive there is 4Gb of data that i can never remove, but ive never used a my book (looks descent and not to costly for there terabyte one, might buy one)

---

### Post by MozartlovesUbun2 on 2007-12-16
> **kajillin said:**
> ive ran into this problem aswell, i couldnt fully partition with g parted so i ran the text based installer again, formatted that way and it cleared the whole drive.

Hope this helps, Cheers

Edit: but it wast an external drie :(, some external drives have untouchable portions with apps, etc..
I know with my external drive there is 4Gb of data that i can never remove, but ive never used a my book (looks descent and not to costly for there terabyte one, might buy one)

ah ok

well what can they be putting in 7.5GB, thats a lot!!!

**from 500 to 465 then again 7.5 taken away, thats a lot.**

Is there anyway to recover this?

one nice feature I like about the My Book is that it goes in to idle when not in use, and jumps straight into action if i open a file, nice
my other Toshiba drives are just on all the time regardless of whether in use or not.

anyway i just did search google for answers, no luck.

---

### Post by Keith Hedger on 2007-12-16
u can use e2label to set a volume label

---

### Post by macogw on 2007-12-16
> **MozartlovesUbun2 said:**
> 
1. The drive in size shows as **465.76**GB, but it shows **7.50**GB used and **458.26**GB unused, how can that be, I just formated the whole drive and have put nothing on it, so what is using the **7.50** GB? (please see picture)

2. It shows a **Lost+Found** folder, I don't know what its for and why it was created, it shows up empty inside. (I'ld prefer it not to be there, can I rid of it?)

1.  500 gigabytes (GB) are not the same as 500 gibibytes (GiB).  GParted shows gibibytes.  GiB use proper 1024 multiples (powers of 2) as the measurement.  Hard drive manufacturers use messed up GB which are multiples of only 1000, so they trick you into thinking there's more storage than there really is.  Tradition says 1GB = 1024MB, but the hard drive manufacturers like to round and say 1GB=1000MB.  It finally turned into the IEEE saying to them "fine, go ahead and call 1000 kilobytes a megabyte and 1000 megabytes a gigabyte.  We'll just make up a new name for 1024-based measurements."  The 7GiB is the formatting info that tells the hard drive and OS how everything's laid out / set up.

2.  Lost+Found is where your files go if there's a power outage and the pointers in that beginning 7GiB lose track of where on the disk they're supposed to be pointing because they were mid-write.

---

### Post by MozartlovesUbun2 on 2007-12-16
> **macogw said:**
> 1.  500 gigabytes (GB) are not the same as 500 gibibytes (GiB).  GParted shows gibibytes.  GiB use proper 1024 multiples (powers of 2) as the measurement.  Hard drive manufacturers use messed up GB which are multiples of only 1000, so they trick you into thinking there's more storage than there really is.  Tradition says 1GB = 1024MB, but the hard drive manufacturers like to round and say 1GB=1000MB.  It finally turned into the IEEE saying to them "fine, go ahead and call 1000 kilobytes a megabyte and 1000 megabytes a gigabyte.  We'll just make up a new name for 1024-based measurements."  The 7GiB is the formatting info that tells the hard drive and OS how everything's laid out / set up.

2.  Lost+Found is where your files go if there's a power outage and the pointers in that beginning 7GiB lose track of where on the disk they're supposed to be pointing because they were mid-write.

hmm, well I just did

**sudo   tune2fs -m 0 /dev/sdb1**

is that ok? I mean I now get 459GB as available, is that ok?

---

### Post by MozartlovesUbun2 on 2007-12-16
[http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)

---

