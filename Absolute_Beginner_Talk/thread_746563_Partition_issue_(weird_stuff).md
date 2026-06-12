---
title: "Partition issue (weird stuff)"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-04-05
I just booted into a Gutsy live CD to restore my GRUB menu (it disappeared after installing XP). When I go to change the boot flags for the separate partitions, GParted tells me that my entire drive is "unallocated." This is very strange, and worst of all, it isn't true. I know for a fact that my drive is partitioned as follows:

*12.0GB as ext3 (this is where Gutsy lives)
*21.4GB as NTFS (this is where the new install of XP lives)
*55.9GB as FAT32 (this is where my media lives, formatted so that XP can read it, too)
*3.7GB as SWAP

If I open Places > Computer, my partitions show up there just fine. What's the deal with GParted? Is it a problem that it doesn't recognize the partitions on my drive? What would I do to go about fixing that?

---

### Post by tamoneya on 2008-04-05
make sure you are giving gparted root access.  It doesnt work well called in normal user mode.  ```
sudo gparted
```.  If that doesnt work you should try using fdisk instead.

---

### Post by doctorbighands on 2008-04-05
I definitely gave it root access. Thank you for the suggestion, though!

---

