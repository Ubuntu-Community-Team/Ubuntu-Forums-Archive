---
title: "Will dual booting with Vista ruin Vista?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-06-04
Hi everyone,

I'm running a Vista machine and want to dual boot with Ubuntu 7.04 off of a single hard drive. However, I've read in a few places that Vista requires its own special bootloader and that during the Ubuntu installation process GRUB replaces Vista's bootloader, which causes Vista to be unable to boot. Is this true?

If not, setting up the dual boot system is as simple as running the installation from the LiveCD and letting it automatically do the partitions and there's no danger, right?

Thanks in advance!

Plinydogg

---

### Post by jonward0690 on 2007-06-04
Well you should manipulate Win Vista partitons just with Win don;t use Gpartitoner on them.

---

### Post by rsambuca on 2007-06-04
You should be fine as long as you use the Vista partitioner to shrink the Vista partition itself.  If you use the gparted partitioner on the ubuntu installer, you will run into problems.  

The grub bootloader should recognize the vista bootloader and set it up for chainloading automatically for you.

---

### Post by oilchangeguy on 2007-06-04
haven't you already got a thread going on this?
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by plinydogg on 2007-06-04
Thanks people! And oilchcangeguy, you're right, I should have perhaps continued that earlier thread. The reason I didn't is because I thought the question had changed: on the other thread it was just a general "which way is better" inquiry; while this thread asked a more specific question (does ubuntu install a bootloader that makes it impossible to boot Vista). 

So, what you all are saying is that I should resize the partition using Vista's "shrink partition" option and then, when installing Ubuntu choose the manual partition option (instead of the automatic partitioning)?

My main problem is that (as I think I mentioned on the other thread), Vista's build-in "shrink partition" function says that I cannot shrink the volume at all (it literally says 0 mb!). I have no idea why this is the case since I have 30+ GB free on the drive!?!?!

---

