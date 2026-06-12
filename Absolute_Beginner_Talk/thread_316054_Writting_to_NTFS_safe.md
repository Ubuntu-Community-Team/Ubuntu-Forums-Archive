---
title: "Writting to NTFS safe?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by JesterDev on 2006-12-10
It's been about a year since I've touched Linux (Suse) and pending development projects are bringing me back to Linux again. :)

Last I heard writting to NTFS partitions was considered safe, but still a bit buggy; is this still the case? Sadly I still have to boot windows for a bit longer while I finish off a few projects, and well my life will be easier if I can write back and forth. 

I did, or rather I am at this moment installing 
Ubuntu, and made a 400mb FAT32 Partition just in case.

---

### Post by Kobalt on 2006-12-10
If you can, you should use a FAT32 partition as a sharing between linux and windows, it's a 100% safe solution. Now, if you really need to access and write a NTFS partition, the solution I've tested and used is Ntfs-3g : 
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
It's easy to install, working very well... Now, it is not completely safe to write on NTFS disks from linux, you could possibly lose some datas... The best would be to read a little bit more about Ntfs-3g in the thread I gave you as a link and make your own mind, see if it's worth trying (I think it's worth though).

---

### Post by JesterDev on 2006-12-10
Thank you for the help. I can tell already I'm going to like it here, and I'm going to learn quite a bit.

---

### Post by Kobalt on 2006-12-10
Welcome :rolleyes: !

---

