---
title: "Installer problems"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by wajvpitt on 2006-09-18
I'm new to Linux, but I'd really like to give Ubuntu a go.  I don't want to give up yet...

I've just put a very cheap box together - Sempron 64 3000 w. 256mb cheap old slow RAM in an MSI SFF case.  I've just installed Windows XP 64 on a 10 gig partition.  Ideally I'd like to install Ubuntu on another 10 gig partition and then leave the remaining 60 gigs for data.  Eventually I'm going to get a big external HDD for data.  I've just been reading about problems reading and writing NTFS in Ubuntu, but I'm nowhere near that stage yet...

My problems start with the Live installation.  The disk works fine and the on-disk version of Ubuntu loads up fine.  It is painfully slow, even the cursor, but I suppose that is to be expected.  

When I click on the 'install' icon, nothing happens.  

I've tried adding some bits to the 'boot:' command to simplify it (I have a Seagate HDD - it said something about that) but the same thing seems to happen.  

I've just been looking at various pages with lots of complicated information but I think my problem is simpler than any of that - any ideas?  Is it possible?  

I'll keep looking now, but my patience is running out.

---

### Post by insane_alien on 2006-09-18
give the alternate-CD a whirl. it lacks a GUI install but it will get the job done a tad quicker. for the 60GB data partition you could use the ext3 filesystem and get drivers so XP can access it.

---

### Post by Perfect Storm on 2006-09-18
You might try the alternate installing version of Ubuntu as there can be problem with the live CD.

It's slow because it run directly from the CD + ram. So the more ram the better it will run.

---

### Post by wajvpitt on 2006-09-18
Thanks for the speedy replies.  
I understand why the GUI from CD is slow - I'm getting some more RAM as soon as I can afford it (poor student...).  

I'm downloading the Alternate CD now.  It's going to take a while - is there a command I can use on the standard CD to bypass the GUI and do a full install?  

Thanks for the heads-up on ext3 - best to get things right from the start!

---

### Post by uno_the_great on 2006-10-01
actually, I managed to quickly and painlessly install the ntfs-3g packages, and add a couple of lines to my fstab file and had my 2 NTFS drives up and running with read/write support after a quick reboot. Just do a search for ntfs-3g, and you should find what you need.

---

