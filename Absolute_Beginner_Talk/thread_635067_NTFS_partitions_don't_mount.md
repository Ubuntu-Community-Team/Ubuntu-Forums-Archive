---
title: "NTFS partitions don't mount"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Telsadel on 2007-12-08
I have installed Kubuntu 7.10 (as the 2nd OS after Windows XP SP2) on my laptop (Toshiba Tecra S1) - everything works fine - only I cannot mount the NTFS partitions.

What should I download and install to fix it?

Thanks in advance!

---

### Post by vanadium on 2007-12-08
Do you see any error messages?

---

### Post by teryowen on 2007-12-08
post output of:

sudo fdisk -l

---

### Post by Telsadel on 2007-12-08
It says when I try to mount the partions :

hal-storage-fixed-mount-all-options refused uid 1000

---

### Post by logos34 on 2007-12-08
> **Telsadel said:**
> I have installed Kubuntu 7.10 (as the 2nd OS after Windows XP SP2) on my laptop (Toshiba Tecra S1) - everything works fine - only I cannot mount the NTFS partitions.

What should I download and install to fix it?

hmm...they should have been detected by ubuntu install and added to fstab.

[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29)

(-->just the ntfs-config part--even though gutsy comes with ntfs-3g by default, the gui will help you mount the partitions.  Hopefully that will solve your problems).

---

### Post by nikoPSK on 2007-12-08
try ntfs-config

:popcorn:

---

### Post by Telsadel on 2007-12-09
Thanks To You All -- It Is Solved And I Am Happy.... For Now :)

---

### Post by nikoPSK on 2007-12-09
Please mark it as "SOLVED" then :p

---

