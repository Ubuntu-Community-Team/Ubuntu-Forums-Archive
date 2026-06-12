---
title: "Permissions for a shared  partition"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by brn on 2006-10-21
Several months ago I aquired a 2nd-hand Dell "Latitude" laptop with WinXP already in place.  Installing Breezy, I partitioned the disk rather badly.  when I later installed Dapper it ignored my /usr and /home partitions and put everything in the woefully small / partition.  I did not much like the way Dapper handled disk partitions so I have re-installed Breezy and hopefully corrected my first clumsy efforts.  Now the 20 GB disk is partitioned like this:

  6 GB - ntsf  - (XT)
  1 GB - FAT32 - /windows (shared)
 10 GB - Ext3  - /
  2 GB - Ext3  - /home
500 MB - Swap  -
500 MB - FAT32 - /dos

My problem:  I cannot write to the shared partition except as root. Permissions are drwxr-xr-x.  Chmod (as root) claims to set all write permissions but it does not happen.  This was not a problem before this reinstallation.  (Yes, I will again try to install Dapper and hope it acknowledges my partitions this time more than last.)

---

### Post by aysiu on 2006-10-21
If you're going to stick with that setup, this should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

With only 20 GB, I would probably partition it this way:

6 GB NTFS
4.5 GB Ext3 /
.5 swap
9 GB Ext3 /home

Then I'd use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write Ext3 from Windows instead of creating a separate shared partition.

By the way, Dapper handles partitions the same way as Breezy--you can choose to manually edit the partition table and mount things the way you want them. If you prefer the text-based installer to the point-and-click one, Dapper has a text-based installer just like Breezy's... it's called the **Alternate CD**.

---

### Post by brn on 2006-10-21
Thanks Aysiu.  It was your excellent tract on partitioning that I followed when I first installed Breezy.  Guessing wildly, I did it all wrong and after installing Dapper, wound up with lots of unuseable disk and no room left in /.

fs-driver doesn't look like my solution.  I very rarely use XT.  It came with a built-in worm that crippled web browsing after a month. I don't much like it anyway.  But I do occasionally need to download some Windows-specific thing with Linux for transfer to the shared partition.  No escape I fear.

Your suggestion for partitioning leaves me curious.  When I reinstalled, my /home directory held about 550 MB.  The root directory, including /usr. was bursting out of 4 GB.  I can't imagine needing more than 2 GB for /home but then again twenty years ago I couldn't imagine needing more than 10 MB for everything.

Thank you again for your terrific support and advice; a really outstanding resource for all of us.

---

### Post by Kateikyoushi on 2006-10-21
You can remove packages from /var/cache/apt/archives it takes up 500MB in my case, with those my edgy install takes up 3.6GB but it depends on what softwares you install and use. 
You could reinstall with a bit bigger / partition if it is a fresh install nothing to loose yet.

---

