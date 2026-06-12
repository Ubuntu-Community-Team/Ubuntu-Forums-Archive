---
title: "What is swap?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-08-16
I was just wondering, what is swap, and how important is it to Ubuntu?

---

### Post by Sbarton on 2007-08-16
This is just one site for info on swap!
[http://www.webopedia.com/TERM/S/swap.html](http://www.webopedia.com/TERM/S/swap.html)
regards

---

### Post by heimo on 2007-08-16
> **Romanus81 said:**
> I was just wondering, what is swap, and how important is it to Ubuntu?

I'd say it's extension of your RAM memory to hard disk. Like pagefile in Windows. RAM is very fast compared to hard disk, so swapping (putting stuff from RAM to hard disk) is "expensive", slow. However smart swapping can improve your systems performance as rarely used stuff doesn't use your valuable RAM. It's a good idea to have a swap partition or file, but it's not completely necessary if you have tons of memory and will never run out of it.

EDIT: disk -> file

---

### Post by Chaotic Thought on 2007-08-16
You can think of RAM being managed in two sections in Linux: (1) used by programs (2) used by the cache

Of course, there's also a third section "unused", but that is not so important in Linux, because Linux will try to use as much RAM as available.

Suppose you have 5 GB of RAM, and are using 1 GB for running programs. Then Linux probably will use (up to) 4 GB for cache. So, in theory, Linux has saved in the cache the last 4 GB of disk data that you accessed. For example, if you're playing your 4 GB collection of MP3s using "repeat mode", then eventually Linux will remember all of that music data in RAM and will no longer need to fetch it from the hard disk again. That's a simplification, but it's the basic idea.

Anyway, when you run a new program, it needs additional RAM, so Linux can get the additional RAM in two ways: (a) throw away some of the cache, (b) swap programs that aren't doing anything to disk

Most people assume option b is slower, but Linux will sometimes prefer to swap programs out rather than throw away the cache. It's debatable at which is better, it depends on the circumstance. For example, if your computer is acting as music jukebox and continuously playing the same 4GB of music from your disk, then it would be better to swap out some unused programs so that your player can avoid disk I/O.

---

