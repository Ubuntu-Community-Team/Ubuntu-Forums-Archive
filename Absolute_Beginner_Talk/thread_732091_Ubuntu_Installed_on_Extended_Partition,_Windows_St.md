---
title: "Ubuntu Installed on Extended Partition, Windows Still Sees Primary Partition"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by navraj on 2008-03-22
I had a vista/ubuntu dual-boot, but wanted to install xp as well. The first time I tried, XP installer said that the max. number of partitions has been reached (which made sense, I had two primary partitions for vista and two for ubuntu). I could afford to reinstall ubuntu though, so this time I used gparted on the ubuntu liveCD to delete the ubuntu partitions and then created the / and swap as logical partitions on an extended partition. Installation went fine. However, when I try to install XP, it still says that max primary partitions have been reached. Vista's disk management tool also shows both ubuntu partitions as being primary. In gparted though, this is what I see:

/dev/sda1        ntfs
/dev/sda2        ntfs
/dev/sda3        extended
     /dev/sda6   ext3
     /dev/sda5   linux-swap

The last two are within the sda3 extended (I couldn't indent them in text mode on this post)

I don't see what's going wrong here. It seems gparted is seeing the ubuntu partitions as logicals on an extended partition (as I intended it to be), but windows sees all of them as primaries. Any ideas?

---

### Post by Shazaam on 2008-03-22
A little complex but it might work.......
[http://apcmag.com/5485/dualbooting_vista_and_xp](http://apcmag.com/5485/dualbooting_vista_and_xp)

After you set this up resize (shrink) the Windows partitions THEN add an extended partition to hold your linux flavors and /swap.

---

### Post by navraj on 2008-03-22
Yes...I might have to install XP first, then install ubuntu on extended partition. I'll try this out and post here if it worked.

---

