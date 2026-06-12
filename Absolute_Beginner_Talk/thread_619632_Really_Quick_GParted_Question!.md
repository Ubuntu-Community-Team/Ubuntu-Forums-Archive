---
title: "Really Quick GParted Question!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-21
Hey, I'm running the live cd and needing to make a partition for ubuntu so I can dual boot with xp. I selected the drive and click Resize/Move. 

Free Space Preceding (MiB) 0
New Size (MiB)              147346
Free Space following (MiB) 7

Now this may be a stupid question ,but which one is going to be the new partition for Ubuntu? "Free Space following?" And also should I make a small 1 GB partition for the swap?

---

### Post by bluepowder7 on 2007-11-21
how big is your hard drive, and where is the windows partition?

---

### Post by 449 on 2007-11-21
> **bluepowder7 said:**
> how big is your hard drive, and where is the windows partition?

Windows is on the main harddrive, the one I'm about to partition Ubuntu. The main harddrive is 143 GB with 80 GB used and 63 GB free.

---

### Post by bluepowder7 on 2007-11-21
oh, so this is a completely separate hard drive?  in that case, you can just make two partitions on it - a big one for the operating system and your files, and a small one at the end for swap.  so, 145gig or so for the OS and maybe 2gig for the swap.  just two partitions is enough.

actually, since you have two hard drives, you CAN have two swap spaces - one on each drive.  you can make them the same size, a gig or two, and there's ways of instructing the OS to either give priority to one of them, or use them both at the same time.  for example, you might say that the swap partition that's on the windows hard drive is higher priority, since it won't be doing anything else while you're running ubuntu.

---

### Post by 449 on 2007-11-21
Sorry if I was unclear, I have one harddrive and I just don't want to erase anything when I partition it. It's 143GB total, 80GN used, and 63GB unused.

---

### Post by Rev60073 on 2007-11-21
It is possible to "resize" your Windows partition so that you can install Ubuntu, but you have to be careful.

You need to have contiguous blocks of free space at the very end of the Windows partition to resize, so that means, your disk needs to be defragmented.

If you do, no problem resizing them (I've done it). If you have low memory (256 or less), resize the windows partition so that you make free space at the end, and create another partition so that you create swap space as well (one partition for Linux, another for swap).

Good Luck :guitar:

---

### Post by Pumalite on 2007-11-21
The partition for Ubuntu is the new one after you resize.

---

### Post by 449 on 2007-11-21
Ok, great! And if I can get one more question that came up, Do I need to make the swap in Gparted or can I do it with the livecd?

---

### Post by bluepowder7 on 2007-11-21
oh, ok.  my bad!  in that case, yeah you'd best defragment the windows thing first (from within windows), and then slice that thing into two new slices.  if you've got 63gigs of free space, maybe leave a bit of slack for windows, so assume you only have the last 55 gigs available.  from that, the very last 2 gigs or so is your swap partition, and the 53 gigs in between the swap and the windows is your main ubuntu partition.

windows 88 gigs /// ubuntu 53 gigs /// swap 2 gigs

it doesn't really matter in which order you make those last two partitions.  you can make a new ubuntu partition with 2 gigs of space following it, or make a swap partition with 53 gigs of space before it.  make one of those two, then allocate all of the leftovers to the other.

---

### Post by bluepowder7 on 2007-11-21
> **449 said:**
> Ok, great! And if I can get one more question that came up, Do I need to make the swap in Gparted or can I do it with the livecd?

might as well do them both at the same time.

---

