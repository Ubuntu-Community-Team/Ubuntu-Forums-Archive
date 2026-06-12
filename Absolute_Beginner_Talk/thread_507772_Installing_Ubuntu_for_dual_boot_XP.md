---
title: "Installing Ubuntu for dual boot XP"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ironorr on 2007-07-23
I'm completely new to Linux, and I want to do dual boot with Ubuntu and XP. My goal is to use XP only for gaming, and Ubuntu for everything else (once I get used to it). I plan to reformat and reinstall XP anyway, so I'm curious what would be the best course of action. Should I reformat/reinstall XP first, and then use the Live CD to install Ubuntu? Or is there a better way since I'm reformatting anyway?

Also, my thought was that I would have a partition for the Ubuntu OS, a Swap partition, a very large partition for all the data, and then a partition large enough for XP and any games. I figured that my games would run better if they were installed in the same partition as XP. How does this sound?

Thanks

---

### Post by LaRoza on 2007-07-23
If you are reinstalling XP, here is the easist course of action:

0. Install XP (using entire drive probably)
1. Install Ubuntu, use the "Resize partition and install to free space" option, make the Windows partition small.
2. Wait for installation to complete.

This will give you what you seem to want. (Swap and everything will be done automatically)

You can make a partition for games and data. I would think that Windows games should be installed in the same partition as Windows. If you want to easily share data, make a FAT32 partition.

After you install, you can easily alter the partitions, with GParted, see my sig.

---

### Post by Tsen on 2007-07-23
I actually prefer to keep shared partitions in either NTFS or ext3.  With NTFS-3g, NTFS works pretty well, and there's drivers to make ext2 and ext3 work in Windows seamlessly.   Choose one, the other or both.  It has a definite advantage, since FAT32 has big fragmentation problems and a relatively small max file size (4 GB).

---

### Post by LaRoza on 2007-07-23
> **Tsen said:**
> I actually prefer to keep shared partitions in either NTFS or ext3.  With NTFS-3g, NTFS works pretty well, and there's drivers to make ext2 and ext3 work in Windows seamlessly.   Choose one, the other or both.  It has a definite advantage, since FAT32 has big fragmentation problems and a relatively small max file size (4 GB).

True, FAT32 isn't the best, but it is the simplest if you are willing to put up with its issues.

---

### Post by MQMike on 2007-07-23
Most definitely, you surely want to install XP first, on the first partition.  It makes life much easier when dual booting Ubuntu (using the GRUB bootloader).

---

