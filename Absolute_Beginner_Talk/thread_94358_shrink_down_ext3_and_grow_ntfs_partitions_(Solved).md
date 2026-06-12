---
title: "shrink down ext3 and grow ntfs partitions (Solved)"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by joseftu on 2005-11-23
I finally got a successful dualboot installation, with Grub working right and everything, on my Thinkpad T43.  (Thanks to all the great help from all the great folks here!).

But now I feel like I made a mistake in the original partitioning, and I'm not sure it's possible to fix without starting from scratch.

I attached a screenshot to show what GParted is showing me now...

So here's what I want to do--I want to grow that /dev/sda1 (the ntfs partition where Windows XP is living) to be about 40 gigs, and shrink down the /dev/sda3 (the ext3 partition where Ubuntu lives) accordingly.  If I can get really fancy, I'd like to have a separate /home partition.

I understand that I really should have done all this correctly in the original partitioning at installation time.  Dumb of me not to.  So is there anyway to avoid the consequence (a complete do-over) of my own dumbness?

---

### Post by az on 2005-11-23
You shrink and grow partitoins from their ends, not the beginning.  You need to shrink sda3, create a smaller sda4, move the contents of sda3 to sda4, delete sda3, grow sda1 and then you are done.

Depending on how you do it you will not need to change your fstab.

---

### Post by joseftu on 2005-11-24
Thanks, azz.  You were right, and that would have worked, I think, but I found some other problems in the process, and it worked out better to just wipe out the linux partition and swap and do the install again after growing the ntfs partition.

---

