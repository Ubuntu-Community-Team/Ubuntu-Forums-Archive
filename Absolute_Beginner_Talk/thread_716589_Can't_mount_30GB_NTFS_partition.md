---
title: "Can't mount 30GB NTFS partition"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by noiseordinance on 2008-03-06
So I'm doing a dual boot system between XP Pro and Ubuntu with a 3rd partition for storage and for whatever reason, I can't mount the storage partition. Both the XP partition and the storage partition are NTFS, but I just can't browse it. Any pointers?

---

### Post by uberlube on 2008-03-06
Can you use them using root nautilus?

---

### Post by noiseordinance on 2008-03-06
What is that?

---

### Post by uberlube on 2008-03-06
Nautilus is a file manager. If you go into terminal and type 'sudo nautilus' It will open with root privileges. If it is not installed go 'sudo apt-get install nautilus' and then open it.

---

### Post by logos34 on 2008-03-06
If you're running gutsy all you have to do is use **[ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971")** gui (install if necessary) to configure the storage partition to mount.

---

