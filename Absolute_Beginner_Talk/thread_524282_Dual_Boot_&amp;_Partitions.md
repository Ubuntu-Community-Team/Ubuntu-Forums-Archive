---
title: "Dual Boot &amp; Partitions"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by shuusef on 2007-08-12
How can I install Ubuntu 7.04 on a partition created in Windows Vista?
Does anyone know of a link/thread that addresses this? plz post

---

### Post by wolfen69 on 2007-08-12
when installing ubuntu, choose the partition that vista created and it will format it in ext3.

---

### Post by p_quarles on 2007-08-12
> **wolfen69 said:**
> when installing ubuntu, choose the partition that vista created and it will format it in ext3.
That's not a very good way to get a dual-boot system. Did you actually read the OP?

Brief instructions for dual-booting Vista and Ubuntu:
1) Defrag the hard drive.
2) Using Vista's partition editor, create the free space that you will use to install Ubuntu.
3) Load the installation disk
4) When you get to the "partition" step, select "use existing free space" to install Ubuntu. 

If you need help with any of these steps, just ask. I've done this on several systems, and am happy to assist.

---

### Post by shuusef on 2007-09-13
Thank-you very much for replying!
I havn't been able to play with Ubunutu, since school started, so forgive me for not responding sooner.

I defragment regularly, and before partitioning I did it again. When I tried to create the partition, I followed a blog post on another website, where I was told to use the volume shrink tool. This only offered to free up 2MB. Is there a better way to create a partition Ubuntu will recognize, and what format should I use?

Do you reccomend using 3rd party software such as Partition Magic?

---

### Post by p_quarles on 2007-09-13
If you can find a third party partitioning app that will work with Vista's file system, go for it.

First, though, I'm a little bit puzzled about why you weren't able to shrink the main partition using Vista's built-in tools. How big is the hard drive, and how much space is used?

---

### Post by Irihapeti on 2007-09-13
I've had the same experience as the OP with Vista's disk management software. This 
[http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/](http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/) 
may be of use.

I ended up using GParted. Vista does object if you adjust its partition from outside, so to speak; it runs a chkdsk and reboots. Once it's done that, all is fine. At least, that's my experience.

Since then, I've been able to use the built in partition manager with no difficulty. I don't know what made the difference.

---

