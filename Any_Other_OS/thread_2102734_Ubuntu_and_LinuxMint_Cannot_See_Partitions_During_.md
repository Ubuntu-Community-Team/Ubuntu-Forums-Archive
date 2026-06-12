---
title: "Ubuntu and LinuxMint Cannot See Partitions During Installation"
date: 2013-01-08
forum: Any Other OS
---

### Post by josiahrulez on 2013-01-08
Hey all, 

So i have a Lenovo ThinkPad Edge E530, with 1x 240GB mSATA SSD and 2x 750GB HDD in Windows Software RAID0.

I have set aside 40GB on the SSD for Linux Mint to be installed, but when i go to install, it cannot see the partitions on the mSATA SSD? Ubuntu 12.10 cannot see the partitions during installation either?


The first image  is my SSD in the Disk Manager on the LiveCD,

And the second image  is during installation, there is no install alongside windows option, only erase disk and manage partitions manually. (The SSD is /dev/scd/)

---

### Post by mikewhatever on 2013-01-08
I am not familiar with Linux Mint, perhaps you had better ask on their forum instead. Anyway, judging by the pictures, it looks like the SSD is recognized as /dev/sdc, and it has 46GB of free space, which is about right. What partition are you looking for? Which file system does it have?

---

### Post by josiahrulez on 2013-01-08
> **mikewhatever said:**
> I am not familiar with Linux Mint, perhaps you had better ask on their forum instead. Anyway, judging by the pictures, it looks like the SSD is recognized as /dev/sdc, and it has 46GB of free space, which is about right. What partition are you looking for? Which file system does it have?

There pretty much the same, except Mint comes packaged with different software and uses Cinnamon Desktop instead of Unity.

And if you look at the second attachment, when i go to choose which partition to install on, it says the 240GB SSD has 256GB free space.

---

### Post by howefield on 2013-01-08
Thread moved to the "*Other OS/Distro Talk*" forum.

---

