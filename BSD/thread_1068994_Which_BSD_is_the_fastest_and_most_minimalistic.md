---
title: "Which BSD is the fastest and most minimalistic?"
date: 2009-02-13
forum: BSD
---

### Post by SunSpyda on 2009-02-13
I want to know which BSD you all think to be the fastest and minimalistic. When I say 'fastest' I mean how well it uses the capabilities of new hardware and how it performs at SMP and threading.

What do you all think?

---

### Post by Sorivenul on 2009-02-13
> **SunSpyda said:**
> I want to know which BSD you all think to be the fastest and minimalistic. When I say 'fastest' I mean how well it uses the capabilities of new hardware and how it performs at SMP and threading.
As far as using capabilities of new hardware, FreeBSD is the current winner in my book, though all the BSDs are behind Linux in this respect. The main reason I say FreeBSD is because I've had a little hardware trouble with NetBSD and OpenBSD, though NetBSD 5 should fix much of this automatically from what I've read.

As for SMP and threading, it depends. I've experienced little difference between NetBSD and FreeBSD in most of my tests, however, I've read reports that NetBSD lacks a bit in this area, mostly because of its broad range of supported architectures. I know FreeBSD's SMP implementation can be improved even more by enabling the ULE scheduler as opposed to the 4_BSD scheduler. 

As far as OpenBSD is concerned, my expertise is fairly limited. The security features of the base install may have some effect on performance, but probably very little, especially on modern systems. Last I knew, OpenBSD didn't support SMP by default, though it provides a separate SMP-enabled kernel during the install that you may select, with SMP support limited to about 4 architectures.

Hope this helps!

---

### Post by kk0sse54 on 2009-02-13
> **SunSpyda said:**
> I want to know which BSD you all think to be the fastest and minimalistic. When I say 'fastest' I mean how well it uses the capabilities of new hardware and how it performs at SMP and threading.

What do you all think?

Most minimal I'd say is NetBSD, as for fastest in reference to SMP and threading I'd say DragonflyBSD. Best hardware support definitely goes to FreeBSD.

---

### Post by Sorivenul on 2009-02-13
> **C!oud said:**
> Most minimal I'd say is NetBSD, as for fastest in reference to SMP and threading I'd say DragonflyBSD. Best hardware support definitely goes to FreeBSD.
I didn't mention DragonFlyBSD as it isn't one of the "Big 3", and a bit "off the beaten path" for even some seasoned BSD users. That isn't to say it isn't worthwhile. Its SMP support should be amazing though, as SMP, threading, and clustering  are major concerns of the project.

---

### Post by kk0sse54 on 2009-02-13
> **Sorivenul said:**
> I didn't mention DragonFlyBSD as it isn't one of the "Big 3", and a bit "off the beaten path" for even some seasoned BSD users. That isn't to say it isn't worthwhile. Its SMP support should be amazing though, as SMP, threading, and clustering are major concerns of the project.

Personally I've never gotten DragonflyBSD to work and at least on one occasion have had some disasterious consequences. I just thought it worth mentioning since smp was one of the major reasons for the split between FreeBSD and DragonflyBSD.

---

### Post by cardinals_fan on 2009-02-13
DragonFlyBSD!  It was forked from FreeBSD precisely because the author (Matt Dillon) had his own ideas on how to implement SMP support and threading.  The new HAMMER filesystem is very interesting for large systems.  DragonFly is by far the most actively evolving BSD system, which is good if you want some real innovations but bad if you need total stability.  It's still pretty stable though.

NetBSD is my personal favorite, but it focuses on code cleanliness over raw SMP performance.  FreeBSD is pretty good.

---

