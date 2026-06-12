---
title: "[SOLVED] Reclaim USB external hard drive free space"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nblue on 2007-10-19
Hello, I just install Ubuntu 7.04 on my external USB Iomega SATA 500 GB. During the installation, I use Manual with the follow partition:
512 MB for swap, 40GB for ext3 and the rest into FAT32 but it only go up to ~30GB. 
So I have around 400GB left as free space. However, after the installation, I only have access to the partitions with Ubuntu and my window xp only have access to the FAT32 partion. The left over free space is gone.
Is there anyway for me to format the left over free space to make it accessable from both Ubuntu and Window ?

Any advise would be greatly appreciated [-o<

---

### Post by JTux on 2007-10-19
Boot into a liveCD and use gParted

---

### Post by dcstar on 2007-10-19
> **nblue said:**
> Hello, I just install Ubuntu 7.04 on my external USB Iomega SATA 500 GB. During the installation, I use Manual with the follow partition:
512 MB for swap, 40GB for ext3 and the rest into FAT32 but it only go up to ~30GB. 
So I have around 400GB left as free space. However, after the installation, I only have access to the partitions with Ubuntu and my window xp only have access to the FAT32 partion. The left over free space is gone.
Is there anyway for me to format the left over free space to make it accessable from both Ubuntu and Window ?

Any advise would be greatly appreciated [-o<

Install the **gparted** package and use it to create a new NTFS partition - or use Windows Disk Manager to create a new NTFS partition.

---

### Post by nblue on 2007-10-20
Thank you very much, that help solved my problem :D

---

