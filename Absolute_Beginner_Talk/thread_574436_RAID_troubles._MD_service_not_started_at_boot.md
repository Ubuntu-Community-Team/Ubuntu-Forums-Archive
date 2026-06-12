---
title: "RAID troubles. MD service not started at boot?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Bebbe on 2007-10-12
My RAID 1 arrays are not reassembled when rebooting. I believe it is due to the md service not starting. I'm on Ubuntu 7.10 AMD64 beta.

I have setup my arrays as follows using mdadm
/dev/md0 = /dev/sda1 /dev/sdb1 
/dev/md0 = /dev/sda2 /dev/sdb2
/dev/md0 = /dev/sda3 /dev/sdb3

As long as i manually start md service using
```
sudo modprobe md
```
and then manually assemble the arrays using
```
sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
```
everything works just fine.

How can I make sure the md service starts at boot?

---

