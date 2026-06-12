---
title: "*Exact* Physical RAM amount?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by fmalan on 2006-01-11
Hi

I have an AMD64 with 4GB of RAM. Due to PC hardware design issues, only 3.25 GB of this is currently visible (this is a motherboard issue). Doing cat /proc/meminfo shows:
MemTotal:      3345184 kB
which is 3.2GB (during bootup I get 3407872 kB which is 3.25).

At my company we also have a dual CPU Opteron with 8GB of RAM (running SUSe). When I do cat /proc/meminfo on this machine, I get (among others):
MemTotal:      7153968 kB
MemFree:       2463056 kB
Node 0 MemTotal:      8388608 kB
Node 0 MemFree:      2463056 kB

Can somebody explain what the meaning of this Node 0 memory amount is? Can this PC access all its RAM or not? And why is the memtotal amount on my machine less than the amount reported by the BIOS? (by about 0.05 GB) ?

Thanks!
F

---

### Post by Sef on 2006-01-11
> Can somebody explain what the meaning of this Node 0 memory amount is? Can this PC access all its RAM or not? And why is the memtotal amount on my machine less than the amount reported by the BIOS? (by about 0.05 GB) ?

Node 0 is the ground node.   Likely, but not necessarily, you have a bad ram chip, therefore it can't access all of the ram.  To read more about it, and other possiblities of what is wrong, click on the link below.

[http://www.aplawrence.com/Blog/B1237.html]("http://www.aplawrence.com/Blog/B1237.html")

---

### Post by az on 2006-01-11
[QUOTE=fmalan]Hi

I have an AMD64 with 4GB of RAM. Due to PC hardware design issues, only 3.25 GB of this is currently visible (this is a motherboard issue). Doing cat /proc/meminfo shows:
MemTotal:      3345184 kB
which is 3.2GB (during bootup I get 3407872 kB which is 3.25).

At my company we also have a dual CPU Opteron with 8GB of RAM (running SUSe). When I do cat /proc/meminfo on this machine, I get (among others):
MemTotal:      7153968 kB
MemFree:       2463056 kB
Node 0 MemTotal:      8388608 kB
Node 0 MemFree:      2463056 kB

Can somebody explain what the meaning of this Node 0 memory amount is? Can this PC access all its RAM or not? And why is the memtotal amount on my machine less than the amount reported by the BIOS? (by about 0.05 GB) ?

Thanks!
F[/QUOTE]
On your desktop machine, are you sharing any memory with a video card?

---

