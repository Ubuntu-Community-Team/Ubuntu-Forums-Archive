---
title: "server reboot after 5months caused problems!"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by xen27 on 2005-09-18
urgent help needed!!

i have been running ubuntu server for over a year now. i haven't restarted the server in a long time, and now when i did it this morning i faced a huge problem. 

starting of the linux failed...

i got the following information:

[B]sata_via (xxxxxxxxx) SATA master/slave not supported (0xa2)
starting ubuntu
pivot_root no such file or directory
/sbin/init/: 429: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init!
[/B]

i did not do anything before reboot.. so what caused this and how to fix it?
ideas?

---

### Post by xmastree on 2005-09-18
I had a similar error on my desktop, which is turned off every night. This time I had just removed the DVD-ROM drive and I got a similar error.

As I had been inside it, I figured I might have disturbed something, so I reseated everything I could. Drive (IDE) cables, memory, video card.
Turned it on and it was fine.  :grin: 

So, unplug and replug everything.

---

### Post by xen27 on 2005-09-18
well if i use the utumbu live cd, i can access the data from the sata-disk. so the problem is not in the cables. 

**EDIT***
....but as i did touched the cables third time, it suddenly started working!!!! god damn, it's a miracle :D

thx for the hint.

---

