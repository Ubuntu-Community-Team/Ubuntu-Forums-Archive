---
title: "Need help"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by masterskop on 2007-05-17
my brother had installed xp on a raid array as primary and then loaded ubuntu on a separate drive (EIDE0).  The grub is loaded on the Raid array and he can not boot into windows.  The mbr of windows was hosed.  The grub is still on that drive.  How can one remove the grub?

---

### Post by jimrz on 2007-05-17
> **masterskop said:**
> my brother had installed xp on a raid array as primary and then loaded ubuntu on a separate drive (EIDE0).  The grub is loaded on the Raid array and he can not boot into windows.  The mbr of windows was hosed.  The grub is still on that drive.  How can one remove the grub?

boot from your winXP cd, from the recovery console type
```
fixmbr
```
this will restore your win mbr. reboot as normal and it should take you to xp

---

