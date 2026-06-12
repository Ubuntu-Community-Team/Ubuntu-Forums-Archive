---
title: "LVM issue"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by randomi on 2006-10-12
If I was to create a logical volume out of two drives and mount it at /home and one day run into problems with the install and have to reinstall Ubuntu, what are the chances I would be able to still use the data on the logical volume and mount it once again in /home after reinstalling Ubuntu?

---

### Post by Ocxic on 2006-10-12
so long as the partition table doesn't get fried, you should be ok. I've managed to do it a couple times without problems.

---

### Post by randomi on 2006-10-12
So in order to avoid those problems I should probably just mount the drives to other locations rather then using an LVM? How stable is an LVM and what are the odds of loosing the partition information?

---

### Post by Ocxic on 2006-10-13
to avoid problems, there are a few things you should do:
1: NEVER power off your computer directly (ie: flip the power switch in the back, unplug the computer), shut it down properly (unless nessaccary).
2: unless your know what your doing avoid the "w" command in fdisk/cfdisk, this command will write any changes you've made to your disk, and don't play with any partion/disk tools/prgrams unless you know what your doing.

other then that, LVM is very stable as far as I'm concerned and I have never had a problem so far....(and yes I've hard powered off my comp several time without lost data or other problems. The odds of acctually losing partition info are low, ussualy things like that happen when you have been messing with the partion table, other then that, a bad disk would be a more likly source then just a random event of something happing to your partitions. 

what do you mean by this???
> So in order to avoid those problems I should probably just mount the drives to other locations rather then using an LVM

---

### Post by randomi on 2006-10-13
> **Ocxic said:**
> 
what do you mean by this???

Mounting the two drives in their own directories. Sorry I wasn't very clear about that. In other words mounting the two drives to /home/data and /home/media or something along those lines.

---

### Post by Ocxic on 2006-10-14
i have found that mounting a drive in your home directory can cause problems, I would suggest another location, but it doesn't really matter where you make your mount points.

---

