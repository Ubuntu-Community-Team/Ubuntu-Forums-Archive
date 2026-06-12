---
title: "combining disk space"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by hardipdhillon on 2007-04-18
i have three scsi hard disk, i have created a samba share, it shows only the 36GB capacity that is equal to one harddisk, i want to combine all three harddisk space.

---

### Post by BoneKracker on 2007-04-18
I suggest you use Logical Volume Management (LVM).

It lets you combine multiple physical devices into a volume group.  Then you can partition that volume group into logical partitions.  So you could have a logical partition that spans across all three disks. You will also want to have partitions for your basic Linux install, of course. 

You can search the forums and the internet for information about LVM.

---

### Post by Blondie on 2007-04-18
You could also consider using software RAID0.

---

