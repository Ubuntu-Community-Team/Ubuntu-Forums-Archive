---
title: "dual boot: hard disk partition"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2005-12-15
Dear friends,

Pls help me to do proper partitioning.

I am planning to install Ubuntu 5.10 in a IBM thinkpad R51. 37GB hdd.

I have the following things in mind

1. Dual boot Ubuntu with WIndowsXP
2. Later I want to install Edubuntu 
3. I want to have a common partition for data

Pls advise me partitioning size and type. 

Also I am not sure about which one to install first - ubuntu or XP?

Regards,

Raj

---

### Post by alamba on 2005-12-15
1. XP first, ubuntu next, edubuntu last
2. Create 4 partitions:
       (i) NTFS partition for XP
       (ii) fat32 partition for data
       (iii) ext3 partition for ubuntu
       (iv) ext3 partition for edubuntu
3. You can create these partitions and leave them empty (no formatting) while installing XP.
4. During installation of ubuntu you can choose the partition to install into.
5. Since you will have one fat partition for data you will be able to access it and write to is from all 3 OS

Akshay

---

### Post by rajsarkar on 2005-12-16
Hi,

Thanks for the reply. 

Any suggestion on the size of different partitions? I have 37GB hard drive.

Regards,

Raj

---

### Post by mfarquhar on 2005-12-16
youll also need a SWAP partition
it's very important

37 -512MB to 1GBswap =36GB dived by 3 OS's means

12GB partitions aprox for equal sizes
or give more to windows and Ubuntu depending on what you need them for

definitely install XP first

ps. get a bigger hard drive it'll really help

---

