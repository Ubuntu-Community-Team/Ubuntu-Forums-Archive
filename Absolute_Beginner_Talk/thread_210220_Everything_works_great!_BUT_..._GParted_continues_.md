---
title: "Everything works great! BUT ... GParted continues to frustrate"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-06
Hi, everyone.

I am dual booting XP and Ubuntu Dapper and everything works great, but GParted will still not allow me to change the size of my partitions.

I use the GParted LiveCD for these attempts to resize.

My history steps:

(1)  I installed WinXP on a new, blank hard drive.  I allowed WinXP to fully format all 232GB as NTFS.

(2)  I attempted to install Ubuntu, but received errors regarding resizing the (single) NTFS partition, so ...

(3)  I used GParted LiveCD to reduce NTFS partition from 232GB to about 110GB.  This allowed 122GB unpartitioned and free for my next attempt to install Ubuntu.

(4)  Then I installed Ubuntu -- worked fine -- dual boot is fine.  I now have a Partition1 - NTFS, Partition2 - ext3 , and Memory Swap partition.

(5)  Everything works fine.

(6)  I decided I probably chose poorly to have such a large Ubuntu ext3 partition (110GB), so ...

(7)  I am attempting to use GParted LiveCD now to <a> Decrease ext3 partition size; <b> Increase NTFS partition.  I have tried several order of operations.  Never it works.  It always begins the resize operation, but after a few moments reports that it will be unable to complete the operation.

( 8. )So for now I am stuck with: Part1 - NTFS - 110GB.  Part2 - ext3 - 122GB, Part3 - Swap - 4GB

This is all not a huge thing, I just don't understand why it won't work.  Thanks!

---

