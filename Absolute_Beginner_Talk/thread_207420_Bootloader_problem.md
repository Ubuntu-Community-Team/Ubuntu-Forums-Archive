---
title: "Bootloader problem"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Wreath on 2006-07-01
(Sry for my english)
I've encountered a big problem. I had previously a bootloader BootIt NG. But after installing Ubuntu, MBR was overwritten by Grub and everything went wrong beacause GRUB doesn't support EMBR. I restored the BootIt but after that it says that there is no bootable partition when I try to start Ubuntu. The problem is that i can't prevent Ubuntu installer from installing GRUB. I have the Ubuntu alternative CD and after instalation I select to go back and I choose option not to install any bootloader (in this case GRUB) but it doesn't work - the GRUB is installed instead of my beloved ( ;) ) BootIt. Any idea hot to avoid installing GRUB :confused: or how to force GRUB to install to Linux partition instead of installing to MBR :confused: 

My HDD looks like that:
1. Win XP NTFS                                                      Logical
2. Win XP NTFS                                                      Logical
3. Win XP NTFS                                                      Logical
4. Dos     FAT-32                                                    Logical
5. EMBR Entry 16MB FAT-12 (BootIt installs here) Logical
6. Linux ./             Ext3                                           Logical
7. Linux ./Home   XFS                                            Logical
8.Linux Swap       Swap                                          Logical
9.Extended
  -some other volumes in NTFS

I hope you will undestand something from this ;)

PS. BootIt allows to make more than 4 logical partitions. It works like that - When you are booting OS, BootIt sets other  loogical partitions to "unnalocated space" so in that booted OS there are only 4 logical partitions.

HEEEELP!!!! :)

---

