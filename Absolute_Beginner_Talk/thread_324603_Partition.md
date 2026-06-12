---
title: "Partition"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by sameen on 2006-12-24
why is it better to install ubuntu in a primrary partition rather than a logical partition ?

because i already have xp on 1 hdd & i dont want to make another primrary partition

---

### Post by taurus on 2006-12-24
Actually, you can install Ubuntu on logical...  Doesn't have to be on primary partitions.

---

### Post by sameen on 2006-12-24
i read partition magic guide that on linux ext2 format is better than ext3

should i use ext2 for ubuntu ????

---

### Post by taurus on 2006-12-24
Actually, ext3 is better than ext2 since ext3 uses journal which is much better in case power takes out your computer or you have to push the power button to reboot (cold boot)...

---

### Post by smoker on 2006-12-24
i agree with taurus, ext3

here is some info on filesystems if you want to read a bit about it:
[http://www.linux.org.mt/node/15#N100F3](http://www.linux.org.mt/node/15#N100F3)

---

### Post by spockrock on 2006-12-24
> **sameen said:**
> i read partition magic guide that on linux ext2 format is better than ext3

should i use ext2 for ubuntu ????

first problem here is partition magic is an aweful partitioning tool, but as taurus said ext3 is better.

Also can I ask, why you don't want another primary partition, you can have up to 4 of them....

---

### Post by sameen on 2006-12-24
> **spockrock said:**
> first problem here is partition magic is an aweful partitioning tool, but as taurus said ext3 is better.

Also can I ask, why you don't want another primary partition, you can have up to 4 of them....


then which software u recommend

---

### Post by spockrock on 2006-12-24
use either gparted live disc, or the ubuntu live disc, or the alternate installer.

they are free, and work better, granted I am comparing partition magic from like 2-3 years ago to gparted.  but I have had friends who use pm and have experienced the same, and a few examples from people posts on other forums.

---

### Post by gn2 on 2006-12-24
> **spockrock said:**
> first problem here is partition magic is an aweful partitioning tool, 

Sorry, have to disagree, Partition Magic is an outstanding utility for Windows, possibly the best. 

It's not good at creating Linux partitions though but will "clear a space" nicely for you to install to.

---

### Post by mendingo84 on 2006-12-24
actually, gparted gave some error message after having it's job done...but it's harmless...partitionmagik is also ok. Go for ext3, it's better.

---

### Post by spockrock on 2006-12-24
I had pm once free space, to install fc1, sufficed to say, I booted into windows, and windows complained about the partitioning table.  Almost lost my fedora/redhate and windows partitions.  PM insisted that it the partition table was recked and needed a format but windows and fc both saw the partition tables fine. 

using pm for linux seems absurd considering gparted works wonderfully.  I would say the Acronis line of utilities are far superior to PM.

---

### Post by housam on 2006-12-24
I agree with taurus for ext3. Gparted is a great partitioning tool. Read [this link ]("http://community.linux.com/howtos/Partition/index.shtml")before partitioning it may help.

---

