---
title: "Changing mounting points after install"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by ionchannels on 2006-07-23
Hi there, I am quite new to Linux. I have just gone through a quick and painless install of Dapper, but when I was setting up the partitions I assigned a 4 GB partition to mount at /home and a 50 GB partition to mount at root. These are both ext3 systems. Is it possible to reverse these mounting points so that /home has the larger partition and root has the smaller partition?

Thanks,
Christian

---

### Post by ciscosurfer on 2006-07-23
Since you just installed, you won't be losing any data per se, so I would just reinstall Dapper and flip the partitions around (4GB for root and 50 GB for /home).  You can't just flip some settings to make one use the larger partition afaik.

---

