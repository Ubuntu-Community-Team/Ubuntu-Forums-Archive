---
title: "Backup and burn to DVD"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by snl on 2007-05-12
How can I use Partimage on the SystemRescueCD to backup my whole system if I don't have external HDD. I understand that I cannot write to the partition that I want to backup, so where can I write my backup to?

Also, how can I burn the backup to DVD if it is bigger than one DVD.

Thank you.

---

### Post by jiminycricket on 2007-05-12
If you have another partition on that same drive, you can write to it (although if that drive goes kaput, then your backup is gone too).  Gparted can reallocate your existing partitions for a new drive.

To split data, try this: [http://www.partimage.org/Partimage-manual_Usage#The_splitting_option](http://www.partimage.org/Partimage-manual_Usage#The_splitting_option)

---

