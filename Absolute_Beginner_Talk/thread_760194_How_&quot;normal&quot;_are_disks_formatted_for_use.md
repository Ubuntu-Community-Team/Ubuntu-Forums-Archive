---
title: "How &quot;normal&quot; are disks formatted for use in software Raid1?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Bob Howland on 2008-04-19
Is is possible to disconnect one of the drives and attach it to another Linux computer and have it be readable? In particular, I'm trying to decide between RAID1 vs. RAID5 arrays, particularly of USB drives, to store several hundred GB of photographs. I would be reading from the drives much more frequently than writing to them.

Thanks

---

### Post by PointyWombat on 2008-04-20
This would only be possible with a RAID 1 and not a RAID 5 setup.  A single disk removed from a RAID 5 set is useless, and RAID 5 is not even recommended unless you have real disk array with an on board hardware RAID controller.

Even with a RAID 1 setup, if you remove that disk, you may be able to read the information on another computer, however this is not an elegant solution either. If the computer is turned off when you sever the mirror, you may be luckier, but returning the disk to the RAID 1 set will also probably require it to re-sync from the left-behind mirror, and you're talking hundreds of GB of data, can take a long, long time. Ultimately, it's probably not a good idea to build a RAID volume of any type out of USB drives. The intent of RAID is not really to enable portability. I'm not even sure it's possible to tell you the truth.

An alternative and more elegant solution to this is to treat them as two separate drives, one primary, and a backup, and use something like rsync to maintain sync between the two.

---

