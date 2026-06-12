---
title: "not automaticallyly fixing this"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by pman41x on 2007-11-23
When I boot I get a stop at 437:  "Not automatically fixing this" and then it will boot up. Sometimes I get 507:cc/53  "Not automatically fixing this" and it just freezes up and I have to shut the power off to reboot . Any ideas as to what what is wrong? Thanks

---

### Post by mellowd on 2007-11-23
We need more information. 

Hardware? Version? What did you last install? Has it ever worked?

---

### Post by Tyche on 2007-11-23
> **pman41x said:**
> When I boot I get a stop at 437:  Not automatically fixing

Could you be a little more specific?  I get the impression that what you're seeing is during the boot sequence, that it's kicking you out of the graphical "loading" bar, but I'm not sure where in the sequence you might be.  And since I don't have the sequence memorized for your computer, I have no idea where 437 is.  Perhaps some information surrounding you're situation would help, too.  For example, have you re-partitioned or re-formatted a partition, or re-installed Liinux on a partition?  I'd really like to help if I'm able, but there just isn't enough information yet.

Thanks.

---

### Post by pman41x on 2007-11-23
Pent four 3.00gig. 1 gig mem. I didn't ever freeze at first, may have done the 437: thing I      don't know because it just went on by that and booted up. The last thing I attempted to load was Blues radio and that failed.

---

### Post by mellowd on 2007-11-23
and the version of linux??

---

### Post by kellemes on 2007-11-23
Do you have a FAT32 partition hanging around?
It's probable fsck is finding errors on the FAT32-disk and not willing/able to fix.
You need to fix this disk using native Windows/DOS **chkdisk.exe**

---

### Post by pman41x on 2007-11-23
Ubuntu version 7.10 installed about a week ago. I had 3 partitions on my hard drive and I used one of them for ubuntu.

---

