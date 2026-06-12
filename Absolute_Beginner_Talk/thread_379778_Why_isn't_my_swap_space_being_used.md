---
title: "Why isn't my swap space being used?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2007-03-08
I just realized that my swap space just isn't being used (and my RAM is working overtime, due to it). when I run top in a terminal, I always have:
Swap:   979908k total,        0k used,

Obviously the system knows the swap is there...just doesn't feel like it should use it. Any suggestiions?

---

### Post by taurus on 2007-03-08
Actually, you want the system to use your RAM since it's much much faster than your swap partition.  When it needs to access your swap partition, it will so don't worry about it.

What's the output of this command from a terminal then?

```
free
```

---

### Post by Henry Rayker on 2007-03-08
I understand about the virtual memory system and the hierarchy of memory system, but the thing is, I'll have 100% memory usage sometimes and everything just sort of grinds to a halt...but I still have no swap being utilized. The output of the free is:

             total       used       free     shared    buffers     cached
Mem:        450728     362060      88668          0      15152     203332
-/+ buffers/cache:     143576     307152
Swap:       979908          0     979908

So it's sitting at around 80% usage right now. I'll try to get one later with more things running, just to check and see what the deal is.

---

### Post by esaym on 2007-03-09
> **Henry Rayker said:**
> I understand about the virtual memory system and the hierarchy of memory system, but the thing is, I'll have 100% memory usage sometimes and everything just sort of grinds to a halt...but I still have no swap being utilized. The output of the free is:

             total       used       free     shared    buffers     cached
Mem:        450728     362060      88668          0      15152     203332
-/+ buffers/cache:     143576     307152
Swap:       979908          0     979908

So it's sitting at around 80% usage right now. I'll try to get one later with more things running, just to check and see what the deal is.

That snapshot there says that your are only using 143576 of you ram.  The rest is simple i/o cache.  I don't know why things would start to run slow for you.  It is probably not due to ram usage.  It could be a buggy program.  

I had a problem on my laptop where things would get slow and jerky but it was because of improper cpu frequency scaling....

No swap usage is normal.  this aint windows

[http://community.smoothwall.org/forum/viewtopic.php?t=21844&highlight=](http://community.smoothwall.org/forum/viewtopic.php?t=21844&highlight=)

---

### Post by V-600 on 2007-03-09
Could someone please just clear up "I/O cache". I have just started dual booting suse 10.2 and when i look at the system resources in KDE (suse) it shows all my memory is taken, with about a 50/40/10 split between used/cached/free. The system monitor in ubuntu shows memory usage at about 40/60 used/free.

As I understand, the cache in suse's memory is for frequently/common processes (not necessary ones and used purely to speed up operations) and can be relinquished when any application needs the memory.

Mentioned earlier i ran "free" in a terminal which states about a 40/55/5 used/cached/free split in memory usage.

Is the cache in Ubuntu the same as in suse and is there any way to show a graphical representation in system monitor (no need, just out of interest).

---

### Post by Crooksey on 2007-03-09
```

$man free
```

---

### Post by igknighted on 2007-03-09
Crooksey, I love your location, thats clever

</offtopic>

---

### Post by V-600 on 2007-03-09
shoulda thought of that first i suppose

---

### Post by esaym on 2007-03-09
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

Simply put, until you start using lots of swap you are fine.

i/o cache= Anything that is read from a cdrom or hard drive (or usb thumb drive or anything else) is stored in the the i/o cache UNTIL an application needs it:KS

---

