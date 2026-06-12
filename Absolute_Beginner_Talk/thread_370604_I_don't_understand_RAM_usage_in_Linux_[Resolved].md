---
title: "I don't understand RAM usage in Linux [Resolved]"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by CaptSaltyJack on 2007-02-25
I've got 1GB RAM on my Ubuntu box.

```

[FONT="Fixedsys"]
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        759        250          0        110        497
-/+ buffers/cache:        151        858
Swap:         1027         17       1010
[/font]
```

And at the moment, I'm logged out of X, this is a remote ssh session from Windows.  759MB is being used?  Why?  And if there's still 250MB free, why has swap memory started being dug into (17MB of it).  I thought swap was for when you're out of physical RAM?

---

### Post by Kateikyoushi on 2007-02-25
Linux uses memory because it is much faster than hard disk and it is just a waste if left unused so it cashes there. the +/- line displays the actual memory usage without the cache.
So you use 151MB and cache 858.

The boot process starts some things which won't write to the disc till you quit also login  etc isn't needed so it gets written to swap because even disc cace has a chance of being used more often.

---

### Post by aysiu on 2007-02-25
Read this:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by tgalati4 on 2007-02-25
Linux memory usage is a trade secret.  All memory gets used so don't worry about it.  Linux immediately fills memory with active processes and caches data up to near max.  The swap space is used for all sorts of things.  Your concern should be when pageouts start climbing, then you will need more ram.  1gb is OK.  2 gb is better, 4 gb is max for most 32-bit systems.

Unless you are doing video editing or 3D animation, 1 gb will satisfy 80% of your computing needs.  Memory management is pretty solid in Linux.  Basically don't worry about it.

The command vmstat will give more detailed memory information.  As long as swapouts is small you won't suffer a performance drop.  Over time, the swap drive will fill up, but again as long as you are not in continuous swapping mode don't worry about it.

I find that I need to reboot about once every 3 months on my machines.  Mostly due to software updates.  If I delay the updates I can get away with 6 months to a year between reboots.  

My laptops typically go for 2 weeks between reboots.  They seem to get balled up more often.

---

### Post by CaptSaltyJack on 2007-02-25
Makes sense.  I'm just noticing a little bit of lag opening up some apps in GNOME, but I suspect it has more to do with Beryl running, and not having the best 3D card.  I have a GeForce 6200LE, which uses the dreaded TurboCache feature. (sucks up your RAM because the card hardly has any onboard memory)  I'll have to upgrade that soon.

Thanks for the info, guys

---

