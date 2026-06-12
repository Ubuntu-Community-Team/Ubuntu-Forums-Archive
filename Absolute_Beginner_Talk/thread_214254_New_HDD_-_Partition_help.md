---
title: "New HDD - Partition help"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Sonic Alpha on 2006-07-12
Hi there,

I've bought myself a new hdd, which I'm planning to use as my primary drive (I have a number of other HDDs).  I just need help on how to define these drives when I partition them.  I'll be dual booting XP and Ubuntu, so my first batch of partitioning will be done through XP, and I plan to leave an area that hasn't been partitioned, for Ubuntu.  Basically, there will be four partitions: -

60gb - Windows (NTFS)
30gb - Apps (NTFS)
30gb - Storage (NTFS)
40gb - Ubuntu

I know that the Windows partition will be defined as a "Primary", but how would I define the Apps and Storage partitions? (I've read you can't have 4 "primary" partitions).

---

### Post by taurus on 2006-07-12
You need at least two partitions for Linux: / and swap.  Since you can only four primary partitions for one harddrive, you need to make one of them as an extended.  Under that, you can create as partitions as you wish.  On the other hand, if you plan to share files between XP and Ubuntu (your storage partition), I highly recommand you create it as fat32 (vfat) so you can read and write to it under both OSes.  Even though some have claimed that you can write to NTFS now, I wouldn't risk my data on that for now...

---

### Post by Sonic Alpha on 2006-07-12
> **taurus said:**
> You need at least two partitions for Linux: / and swap.  Since you can only four primary partitions for one harddrive, you need to make one of them as an extended.  Under that, you can create as partitions as you wish.  On the other hand, if you plan to share files between XP and Ubuntu (your storage partition), I highly recommand you create it as fat32 (vfat) so you can read and write to it under both OSes.  Even though some have claimed that you can write to NTFS now, I wouldn't risk my data on that for now...

So, if I make an extended partition that is 60gb, I can split it between the apps and storage?

I'm not too bothered about writing to the storage drive, I just have mp3s on there, so as long as it can read I should be fine ;)

And yeah, I know you need a swap drive.  I saw a [video on google]("http://video.google.com/videoplay?docid=-6104490811311898236") that showed how to install, and they made a little partition that was 512mb... is that big enough?

---

### Post by Paerez on 2006-07-12
if you dont mind re-arranging, I would do this:
Primary 1: Windows
Primary 2: Ubuntu
Extended 5: Ubuntu Swap (same size as your ram)
Extended 6: Apps
Extended 7: Storage

You can have up to 4 primary and I think 4 extended.

---

### Post by taurus on 2006-07-12
Yes, you can use extended for both apps & storage.  Regarding your swap space, 512MB should be more than enough if you have 512MB of RAM.  The easiest way is to install XP first.  Then install Ubuntu and use GRUB to boot both OSes.  Don't forget to install GRUB on MBR so read that screen carefully before you click Next!

---

### Post by Sonic Alpha on 2006-07-12
They weren't in any particular order ;)

Thanks for the help :)

> **taurus said:**
> The easiest way is to install XP first.  Then install Ubuntu and use GRUB to boot both OSes.  Don't forget to install GRUB on MBR so read that screen carefully before you click Next!

I take it when I install this time, I will be asked how big I want to make the swap space? (This was an option on the video I linked to)

---

