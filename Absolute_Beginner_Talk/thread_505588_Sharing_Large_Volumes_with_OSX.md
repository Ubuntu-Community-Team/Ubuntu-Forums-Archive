---
title: "Sharing Large Volumes with OSX"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by cwd on 2007-07-20
i have a 50gb lacie drive and want to copy files to it from my mac. then i want to unplug it from the mac and hook it to my ubuntu server via usb2.

i successfully did this using an ms-dos format, and the drive checks ok on the mac, but on ubuntu I get a buffer overrun and:

sdb: p1 exceeds device capacity

any thoughts on a better format than ms-dos that would be r/w on both osx and linux?

thanks

---

### Post by kngunn on 2007-07-20
How about ext2/3? 

[http://freshmeat.net/projects/ext2fs/](http://freshmeat.net/projects/ext2fs/)

---

### Post by Rocket2DMn on 2007-07-20
If you are running a large drive (maybe a RAID, I know Lacie has some big external ones), you can't run FAT32 which is the classic windows format.  There is also no reason to run NTFS.
You should format it to use ext3 if you can.

---

### Post by cwd on 2007-07-26
I did an ext3 format and for whatever reason, I get a logical block error 980469440. Is there some limit on addressability (how strange)? I've tried two of these disks. LaCie gangs two disks in an internal stripe, but that should be opaque to the host OS.

Thanks

---

