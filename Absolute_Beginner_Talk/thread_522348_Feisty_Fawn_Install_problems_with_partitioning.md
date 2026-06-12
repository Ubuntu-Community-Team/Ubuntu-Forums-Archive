---
title: "Feisty Fawn Install problems with partitioning"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by riknos on 2007-08-10
Hi all,

I am a complete newbie to Ubuntu and want to dual boot with XP(at least to start with). Booted from live disk from Linux Magazine disk and all went well till the Partitioning stage. I have two 250G SATA disks and have previously had another dual boot working well (with Suse10.2). I used Acronis Disk Director to pre set up partitions on disk 1 and I did the same for this install.

However, the Install Partitioning application only shows partitions and mount points on disk 2 ( /dev/sdb etc.) It does show disk 1 but no partitions or mount points. If I click on the drive description the response is that the install will erase everything on that disk!!!  I've tried Expert mode command line install option and still the same thing occurs. I don't want to install on disk 2.

Please help.

---

### Post by MenZa on 2007-08-10
Try unplugging that disk while you attempt to install it.

---

### Post by riknos on 2007-08-10
Thanks for your quick response. 
Seems a bit extreme but will give it a try. Is this a known bug with the Install application?

---

### Post by jingo811 on 2007-08-10
I don't quite follow you there.  But if you're looking for a Dual Boot (Win XP + Ubuntu) tutorial then try this that I've made recently.
[http://ubuntuforums.org/showthread.php?t=521310](http://ubuntuforums.org/showthread.php?t=521310)

---

### Post by riknos on 2007-08-10
I mean nothing that's been said explains why the Install program doesn't display my disk 1 partitions, only those on disk2.

When I ran the Expert text-only install and search disks option, I noticed the application found and briefly displayed the partitions and mount points on disk 1 as it searched but then did not display them for partitioning options. Why?

---

### Post by Jonnothin on 2007-08-10
Is there anything important on disk 1? Cause if there isn't just make a new partition on the drive with Ubuntu. If there is something important move it to disk 2. Are you still using the other OS and is it on disk 1?

---

### Post by riknos on 2007-08-15
Sorry didn't get back to you sooner. Thanks for your response. 

Yes, I'd like to keep XP and Suse on disk 1 for dual boot just till I am happy with Ubuntu. I guess I could move Suse to disk 2 and then see if Ubuntu install offers freespace on disk 1, which it is not doing at present.

---

