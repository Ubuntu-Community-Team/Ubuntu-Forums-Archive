---
title: "Ubuntu sees my raid hd as 2 drives"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Josey on 2007-12-14
I have my one 466gb drive set to raid0 but the partition editor thinks it is 2 devices.
dev/sda
and
dev/sdb
please help

---

### Post by disturbedite on 2007-12-14
do you have two partitions on that drive?

---

### Post by Josey on 2007-12-14
no it is all unallocated

---

### Post by dstew on 2007-12-14
You probably have a "fake" RAID, not a true hardware RAID. In these cases, you have to jump through some hoops to install Ubuntu. See [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

