---
title: "Advice on Disk Setup"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Markybhoy on 2007-06-03
Hi.

I was thnking on installing ubuntu on my main machine since it worked so well on my laptop.
I need a new hard drive so I was thinking of getting a new 750gig one.

My question is would there be any difference in real world speed terms if I used the 750gig drive for everything,  root , home swap etc.

Or would it be better to use 2 seperate drives,  I have a few spare so could have root and swap on one dirve and /home on the new large drive.

Is it worth the effort to use 2 drives,  would you reckon there would be much real world difference ?

Just trying to get a nice snappy setup.

---

### Post by Marsolin on 2007-06-03
If the 750GB drive is faster then the others, and you aren't looking for extra space, I'd use the one drive, but break it up into three partitions: /, swap, and /home.  / only needs to be ~10GB.

Having a separate /home partition is useful for whenever you need to reinstall the OS.  The new install can completely overwrite the /root partition, and you just point it to the existing /home partition.  That way your personal settings and files are already there once you boot into the new OS.

I did a [post]("http://linuxappfinder.com/blog/preparing_for_system_failure_and_recovering_quickly") about this on my blog a little more than a month ago.

---

### Post by Markybhoy on 2007-06-03
Thanks for the advice,  I think  I will just use 1 large drive and partition it like you mentioned,  also will save some space in my case :)

---

### Post by zvacet on 2007-06-03
You can do that or download Gparted live CD and resize your home partition if you feel like it.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

