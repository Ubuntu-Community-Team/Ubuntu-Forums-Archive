---
title: "partition space"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-07
I have an 8 gig partition just sitting on my hard drive wasting space.  How can I safely merge it with my current active ubuntu partition.  With only 20 gigs on the disk, I don't have much to spare anyway.

---

### Post by jpkotta on 2006-10-07
First, back up your data.  Then use a live CD ("desktop" CDs from Dapper or newer) and use gparted to clear the empty partition.  Then resize the partition before it (that's about all you can do, with any partitioning software AFAIK).

Another option is to just format it as it is and mount it so you can use the space.  I have extra partitions too, so I do this in /etc/fstab:
```
/dev/sda1       /archive        ext3    defaults,noatime         0       0
```
and use it for backups, .isos, etc.

---

### Post by lemonsCC on 2006-10-07
I thought you could merge the two partitions as long as the Ubuntu partition is the leftmost one?

---

### Post by maaronB on 2006-10-07
> **jpkotta said:**
> 

Another option is to just format it as it is and mount it so you can use the space.  I have extra partitions too, so I do this in /etc/fstab:
```
/dev/sda1       /archive        ext3    defaults,noatime         0       0
```
and use it for backups, .isos, etc.

This is probably your best option.  You can use the extra 8G for storage and not have to worry about losing it if you need to reinstall Ubuntu.

---

### Post by danbert on 2006-10-09
I did this to use additional space on my hard drive, and it tells me that only root can mount the device.  How do I make it read/writeable for me as a normal user?

---

### Post by CatKiller on 2006-10-09
> **danbert said:**
> I did this to use additional space on my hard drive, and it tells me that only root can mount the device.  How do I make it read/writeable for me as a normal user?

[Unofficial Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_dapper")
[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")
[Mounting Linux Partitions/Drives in Ubuntu]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by saintj0n on 2006-10-09
In terms of ubuntu, I am a low level user...Is there a linux version of the DOS 'format' command?

---

### Post by lemonsCC on 2006-10-09
Thats what he was talking about with Gparted.  It can format and do lots of other things. :p

---

