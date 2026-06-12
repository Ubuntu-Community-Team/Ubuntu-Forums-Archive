---
title: "XP/Ubuntu - Shared Partition Not Showing in Ubuntu"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by RDonnelly on 2007-12-13
Hi, I recently just got a dual-boot XP and Gutsy going.  I really like it, but I can't access my data partition in Ubuntu.  I can get to it find in XP (it is its own drive), just not in ubuntu.  Any tips to access it?  My windows partition shows up and I can access that one.  Here's my fdisk:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5228    41993878+   7  HPFS/NTFS
/dev/sda2            5229       10091    39062047+  83  Linux
/dev/sda3           10092       19457    75232395    5  Extended
/dev/sda5           10092       18845    70316473+   b  W95 FAT32
/dev/sda6           18846       19457     4915858+  82  Linux swap / Solaris

```

Thanks!
Ryan Donnelly

---

### Post by jken146 on 2007-12-13
Can you post your fstab please?  That's ```
cat /etc/fstab
```

---

