---
title: "Dual boot issues after using Partition Magic to change partition size"
date: 2012-12-31
forum: Any Other OS
---

### Post by wordmagic on 2012-12-31
I used Partition Magic 8 in a dual boot system (WIN XPSP3 and Ubuntu 12.04 with GRUB) to increase the size of a partition. Something went wrong with the procedure and while Ubuntu loads OK, when I try to load XP, it goes into the XP screen, then quickly displays a blue error screen, and then goes into a restart loop (Safe boot does not work either and DOS command prompt not accessible too).

Checking the Windows files from Ubuntu i can see that they are all accessible, but running a repair installation of Windows did not lead me to the screen where it spots the Windows installation for repair (this one [http://0.tqn.com/d/pcsupport/1/0/d/0/-/-/xpcl1.jpg](http://0.tqn.com/d/pcsupport/1/0/d/0/-/-/xpcl1.jpg)) instead it gave me a list of partitions.

Any advice would be highly appreciated.

---

### Post by Sef on 2012-12-31
moved to other os talk.

---

### Post by oldfred on 2012-12-31
Do you still have boot flag on Windows NTFS partition? Windows only repairs the active partition which in Linux is the boot flag.

---

### Post by lykwydchykyn on 2012-12-31
I had similar problems, and I tried everything to get XP to boot without success -- until I loaded up testdisk on a live CD.  I can't remember the exact details, but testdisk sorted out some badness in the mbr and all was well after that.

I can't remember if testdisk is on the Ubuntu CD, but I do know it's on the partedmagic CD.  Testdisk is console-based, but it's menu driven and not very hard to use.

---

