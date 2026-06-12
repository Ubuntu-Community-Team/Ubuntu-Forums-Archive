---
title: "editing files on a windows NTFS partition"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by williambrodie on 2007-05-27
Is there any way of editing/deleting files on a windows XP-SP.2    NTFS partition?

---

### Post by taurus on 2007-05-27
Yes, but you need to install ntfs-3g driver first if you want to write to ntfs filesystem.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Happy_Man on 2007-05-27
> **taurus said:**
> Yes, but you need to install ntfs-3g driver first if you want to write to ntfs filesystem.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)


Or, you could open a terminal (Applications -> Accessories -> Terminal) and type
```
sudo apt-get install ntfs-3g ntfs-config
```

---

