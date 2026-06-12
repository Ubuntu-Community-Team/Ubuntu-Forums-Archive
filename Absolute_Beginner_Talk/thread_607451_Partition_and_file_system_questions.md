---
title: "Partition and file system questions"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by trvllr on 2007-11-08
Hey, I can't seem to find any good threads or tutorials on how to properly partition and mount a second hard drive.   

What I have is a dell server with a RAID array configured to present two logical volumes to the OS.  I'm using Dapper Drake server (I might actually have to be able to buy support for my VMWare Virtual Server, so 6.06 it is) and the first volume configured perfectly during install, no problems.  Now it's time to configure the second volume with a partition, an ext3 file system and get it mounted so that I can drop files to it.  I tried Parted, but it seems to indicate that it can't do ext3.  So I am a bit confused.  

Can anyone point me to the right thread or give me a hand directly?

Thanks

---

### Post by gubemton on 2007-11-09
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Seems straight forward enough.

---

### Post by trvllr on 2007-11-09
Awesome!  Worked perfectly. Thanks for the assist!

---

