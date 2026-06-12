---
title: "System is reading incorrect partition size"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by swkiller on 2007-09-24
hey all,

Ok, so previously I had 2 partitions on my system (my current linux one had 1.2 gigs free).  Well I went to delete the later one in the partition line, so I could grow the size of my Linux partition over the deleted partition.  So I fired up a LiveCD and went into GParted to do just that.  Well when I went to grow my linux partition after deleting the other one, GParted seemed to stall and kept saying it was performing the action (for about 5 minutes), until I get fed up and decided to cancel said action (stupid mistake in retrospect).

So after doing so, I noticed that GParted claimed it actually did just that, and grew my partition size to the new size I wanted.  Well all is fine until I rebooted, and noticed that now in system monitor it says my partition is the same as the old size (as if it never grew), but GParted and QParted say that my partition did grow, and that i magically took up all the new space and am still left with only 1.2 gigs.

Here's the fdisk output

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         871     6996276   af  Unknown
/dev/sda2            5861        7165    10482412+   7  HPFS/NTFS
/dev/sda3            7166        7296     1052257+   5  Extended
/dev/sda4             872        5860    40074142+  83  Linux
/dev/sda5            7166        7296     1052226   82  Linux swap / Solaris


Any idea? :/

---

### Post by reset3x on 2007-09-26
Growing a partition does take a bit of time... Larger partitions take longer... GParted has to move things around and it also checks data integrity during the process... Try again and let it do it's thing...

Hope this helps...

---

### Post by swkiller on 2007-09-26
Wow, I didn't think it would be as easy as going back and resizing it again (good thing it had some free space to size it down, and back up again).

It seems to be working perfectly fine now, thanks :)

---

### Post by reset3x on 2007-09-26
Awesome!!! Great to hear!!! :)

---

