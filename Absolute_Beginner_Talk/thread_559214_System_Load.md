---
title: "System Load?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-09-24
Hi, all.

Since installing Ubuntu I've been particularly obsessed with monitoring my system.  I've added the "System Load" monitor to my top panel, and I've noticed that it gets really high when I'm running KTorrent.  By really high I mean it is presently around 3.5, and al I have running is Firefox, Pidgin, Tomboy, and Google Desktop, in addition to KTorrent. The computer is noticeably less responsive when this occurs.  When I turn off KTorrent (i.e. stop all downloads), it seems to fix the problem.

My setup is as follows:

P4 1.5Ghz, 512MB RAM, Ubuntu Feisty 7.04

Is this normal?  What exactly *is* system load, anyway?  

Thanks for your help!

---

### Post by Pumalite on 2007-09-24
Most bittorrents are 'memory hogs'. If you have a lot of downloads and uploads, the is a lot of read and write to the hard drive. That can increase the load on the CPU.

---

### Post by limberlegs on 2007-09-24
I see.  It does also say that my memory is only 55% in use.  I suppose it is hogging other resources as well?

---

### Post by Pumalite on 2007-09-24
Unless you have 4 or at least 2 GB of memory, bittorrents will slow down your computer in general.

---

### Post by jordanmthomas on 2007-09-24
Part of your system load is network load, which is probably what's raising yours while your running a torrent client.  I share a bunch of high-traffic files on my school network and my system load gets up to 4.5 or so sometimes, but my system is usually still pretty responsive.

Ktorrent is actually pretty light and won't eat up your RAM too much in comparison with other clients (I'm looking at you Azureus, you java fiend).  Like you said, you've still got 45% free.

Also, check to make sure Ktorrent hasn't taken up a lot of CPU time

---

### Post by jordanmthomas on 2007-09-24
Here's an article on System Load.
[http://en.wikipedia.org/wiki/System_load](http://en.wikipedia.org/wiki/System_load)

---

