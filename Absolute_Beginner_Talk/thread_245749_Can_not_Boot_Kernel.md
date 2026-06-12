---
title: "Can not Boot Kernel"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Robbyx on 2006-08-28
So far I have failed to run Ub. The CD halts at Booting the kernel. So it succeeds in uncompressing Linux but that is as far as it works, for me.

I am using an ASUS P5B board which uses the Intel Pentium 4. It has 2gig of fast ram, 2 satas, 1 pata and a cd.

What can I do to at least see if I like Ub?

Robin


I am running the latest version of Ub. (Is its kernel 2.4.27 or later?)

---

### Post by bruce89 on 2006-08-28
Ubuntu 6.06.1 uses kernel 2.6.15.  I don't know what the issue could be, but I'm sure somebody else might.

---

### Post by toasted on 2006-08-28
Reccomendations from what Ive read are to use the alternate cd if the live one wont work for you, I have never had to do that though... with the alternate you dont get a preview... you do the install.

Also, check for hardware issues that you may have, run a memory test

---

### Post by steelfanatic on 2006-08-28
Check this thread: 
[http://www.ubuntuforums.org/showthread.php?t=236802&highlight=p5b](http://www.ubuntuforums.org/showthread.php?t=236802&highlight=p5b)

Installer on alternate CD will not work, I did a USB2 external install with Mepis, maybe Ubuntu will work?](*,) 

Some did network install, ALL linux distros have this problem.

---

### Post by Robbyx on 2006-08-28
Does my problem fit the answers so far, for which I thank you. I am able to boot off the CD. At this first attempt I  was not going to install Ub, but run it from the CD. Ub uncompresses Linux successfully presumably to memory and then hangs when booting the kernel. I had tried Xandros and it had the problem of loosing the CD , but is this the same problem with Ub?


One of the answers suggest that I use a generic IDE switch but I am not able to get to the stage where I can put in a command line.

Robin

---

### Post by Robbyx on 2006-08-29
Can  I please have a reply?

Robin

---

### Post by jerry_c on 2006-08-30
Robin,

If you can boot off the cd, mount your hard drive partitions and you can browse and edit them from there, and even download and install a different kernel or a kernel patch. Running from the CD doesn't mount your hard drives. You have to do that manually, partition by partition. Hope this helps.

I'd also suggest trying to find an active thread closest to your problem. It can get pretty lonely starting your own thread and hoping somebody will find you.

Good luck.

---

