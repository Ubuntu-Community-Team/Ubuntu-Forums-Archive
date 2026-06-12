---
title: "Dual-booting/Partition question"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by harshlanguage on 2007-04-09
I've been thinking about trying to dual-boot Ubuntu on my main rig up at school, and have been playing around with 6.10 for a while now on an older PC I have for use when I'm not up at school.  My main hangup is that I still need to use XP for a few programs, mainly games and Photoshop.  Now, I'm pretty confident I could pull off a dual-boot with no problems, it's just that I would like to have access to a bunch of files on both OSs.  Now, my music collection isn't that big a deal, as a FAT32 partition would solve that, easy.

The only hangup I have is that I may need to share files bigger than 4 GB between XP and Ubuntu.  FAT32 won't do that, and that's where I'm stumped.  I've heard that Linux can see and *maybe* write to an NTFS partition, but I've also heard that that's a very bad idea; one that will likely end in much pain, suffering, blood, and a reformat of XP.  Not cool.  Ideally, I want the XP-only stuff (an NTFS partition on one drive) and the Ubuntu-only stuff to stay isolated, with a common partition or two that both can access.

This will all be installed over 2 hard drives, a 200 GB and a 300 GB.  Space is definitely not an issue here, just the matter of making a partition or two that everyone can share and enjoy, while keeping OS-sensitive stuff seperated in their own little worlds.

---

### Post by rennen01 on 2007-04-10
Hope this helps.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d)

---

### Post by kfrance on 2007-04-10
I've been dual-booting for over a year using Ubuntu and Windows both at home and at school.  I just use a ext3 partition that I share between them.  You don't have to deal with messed up permissions or the file size limit of FAT32.  Install Ext2 Installable File System which can be found here [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html). I haven't had a single problem so far with stability.  The ext3 partition looks like any other drive in windows.  You'll never know the difference in either operating system.  I've never had a file corrupted.  Good luck!

---

