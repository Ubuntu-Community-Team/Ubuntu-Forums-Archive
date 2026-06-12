---
title: "External HDD Issue"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by DGortze380 on 2007-10-23
I know this is more of an OS X issue, but I can't seem to find anyone on the other forums that can help.

I've got a new Seagate External Hard Drive that's having a weird problem in OS X. I partitioned the drive in Ubuntu using gparted, there is currently 1 fat32 partition on it (fat32 so I can share files between OS X, Ubuntu and Windows). Anyways, I loaded a bunch of files onto the drive in Ubuntu with no issues. I then booted to OS X with the drive connected and it automounted perfectly, could access everything I put on the drive fine... until I tried to delete a file, OS X froze up, had to power off by hold the power button  ](*,).

Now OS X won't mount my external drive. The drive is fine, it still mounts, reads and writes in Ubuntu but OS X is having weird issues:
1) Boot with drive connected- will not mount, disk utility freezes when I try to open disk utility.
2) Boot with drive disconnected- boots fine, disk utility opens fine. I connect the drive and it isn't recognized. I disconnect the drive and it shows up. So I reconnect and hit mount, says it can't be mounted to run first aid. Disk utility freezes when I run first aid. At this point I check for the drive in the terminal, it is recognized in the /dev directory but when I try to mount from the terminal it says unknown special file or file system. I'm just learning to use the terminal so I may have entered a wrong command, in the /dev directory I used "mount disk1".

Please help me get this disk mounted in OS X.

---

