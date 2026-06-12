---
title: "Mac OS broken when switching from Ubuntu"
date: 2013-01-09
forum: Apple Hardware Users
---

### Post by confusedyoda on 2013-01-09
"So dear experts, I have a MacBook Extended Journaled HFS+ (500GB)" OS 10.6.8--that is partitioned with an EFT to the Ubuntu partition. I tried to switch to my Mac partition (which I have been doing for a year or so)  and was not successful today. I put in my Mac OS disk to get into Disk Utility to see what was happening. "Invalid B-tree node" was the comment.  So back into Ubuntu to run GParted. I ran it twice for the Mac partition (took many hours) and got this information: Warning: Unable to detect file system! Possible reasons are: -The file system is damaged    -The file system is unknown to GParted    -There is no file system available (unformatted)    -The device entry/dev/sda2 is missing.  I have searched forums and read about "recovery" options. Help!
(Just a thought: to pull my hard drive, set it on the shelf, wait for a solution in the future TADA!)

---

### Post by confusedyoda on 2013-01-20
After extensive research and trials, I ended up wiping my entire hard drive, repartitioning with Mac OS 10.6.8 and Xubuntu. I also discovered that my computer was on and in my Ubuntu partition, when I tried to restart thinking that my computer was off. The Ubuntu partition did not respond to the mouse movement, and return key and space bar action. I should have waited for more time to pass for that partition to "wake". (The Mac partition responds immediately.) So consequently, my actions caused my Mac OS partition to crash. Fortunately, my Ubuntu partition, through all of this, continued to work. Hopefully, this Quick Reply will help others to be more patient waking their  4+ yr. old MacBook.

---

