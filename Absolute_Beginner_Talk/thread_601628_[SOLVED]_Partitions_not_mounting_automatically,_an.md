---
title: "[SOLVED] Partitions not mounting automatically, anymore"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by manishk on 2007-11-03
Hi, I'm very sorry if this sound repetitive...

I have a dual boot system - Gutsy (AMD64) and XP. Everything was fine until I reinstalled XP. 

Now the XP partition (NTFS) doesn't mount automatically, I have to mount it manually through Nautilus everytime.

I have the same problem with another partition that I formatted to FAT32 (it was FAT32 earlier also) before installing XP.

Please help.

---

### Post by overdrank on 2007-11-03
> **manishk said:**
> Hi, I'm very sorry if this sound repetitive...

I have a dual boot system - Gutsy (AMD64) and XP. Everything was fine until I reinstalled XP. 

Now the XP partition (NTFS) doesn't mount automatically, I have to mount it manually through Nautilus everytime.

I have the same problem with another partition that I formatted to FAT32 (it was FAT32 earlier also) before installing XP.

Please help.

Hi I believe this link will help
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
This way you can make a mount point and add it.

---

### Post by manishk on 2007-11-03
Thanks. I'll try this.

---

### Post by manishk on 2007-11-06
All I had to do was change entry in fstab from *UUID.....* to */dev/sda1 *

Thanks a lot.:)

---

