---
title: "ntfs-3g mounts drive but only reads not writes"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by hasaang on 2007-08-14
I installed ntfs-3g to mount my windows hard drives
Here is the setup for clarity
1) IDE HD - 2 Partions 1st) NTFS Vista x64 Ultimate 2nd) ext3 Ubuntu Feisty
2) SATA HD (1 primary partion) - NTFS
3) SATA HD (1 primary partion) - NTFS

For some reason I can mount all of them fine and they all read and write fine except for Disk 2 which reads fine but doesn't write.

Any clues on whats going on?

---

### Post by hasaang on 2007-08-14
Never mind it fixed itself when I renamed all 3 drives in Vista and then rebooted back in Ubuntu.. weird but near as I can figure it I think two mounts with the same name were conflicting or something:confused:

---

