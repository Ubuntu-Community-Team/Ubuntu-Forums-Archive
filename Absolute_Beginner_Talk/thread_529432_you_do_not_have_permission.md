---
title: "you do not have permission"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by grandsurfy on 2007-08-19
I am new to feisty and have been having trouble with permissions ,I have 3 H/Ds and can not write to the 2 data disks (ntfs file ),If I start nautilus as su I can only access sda,
 sdb & sdc I can read ,but not write.(you do not have permissions etc).having searched the forums I have tried many command line strings, they either do nothing or you do not have permission,Help!!
Duel boot XP & Ubuntu .  loosing hair 3 score years & 9 ,& trying to unsubscribe from Bill:(

---

### Post by HereInOz on 2007-08-19
Try installing ntfs-3g using synaptic.  That will allow read and write capability to NTFS partitions.

---

### Post by jnorthr on 2007-08-19
Yes, think i've seen a recent post about not being able to write to ntfs formatted partitions without another bit of glue. Will try to find the post.

---

### Post by kleo skywalker on 2007-08-19
This might help: [MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions"). Also see [this]("http://ubuntuforums.org/showthread.php?t=528703") thread.

---

### Post by jnorthr on 2007-08-19
Oz looks to be right. Look here for a link to gain more info: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by overdrank on 2007-08-19
> **grandsurfy said:**
> I am new to feisty and have been having trouble with permissions ,I have 3 H/Ds and can not write to the 2 data disks (ntfs file ),If I start nautilus as su I can only access sda,
 sdb & sdc I can read ,but not write.(you do not have permissions etc).having searched the forums I have tried many command line strings, they either do nothing or you do not have permission,Help!!
Duel boot XP & Ubuntu .  loosing hair 3 score years & 9 ,& trying to unsubscribe from Bill:(

HI maybe this will help
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by grandsurfy on 2007-08-19
THANKS GUYS Ureaka ! !:) cant spell either But I can now access my files
thanks again

---

