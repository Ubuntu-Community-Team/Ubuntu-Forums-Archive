---
title: "BSD - beyond their &quot;focus&quot;"
date: 2008-04-10
forum: BSD
---

### Post by stream303 on 2008-04-10
One thing to remember about BSD is not to depend solely upon their "focus", that is speed, portability, or security (Free / Net / OpenBSD)

Each one can be tuned or detuned to look just like each other. :)

The other aspect is that after install, you are likely depending on a kernel and userland binaries compiled for the lowest-common denominator architecture, such as 386 when you might be running 686 etc.

In the case of FreeBSD or NetBSD, one typically wants better performance, so you can recompile just the kernel specifically for your architecture, or recompile both the kernel *and* userland utilities.

In the case of OpenBSD, you can also do this, but if you recompile your kernel, it is assumed you know exactly what you are doing, and if you ask for help, everyone assumes you are running the stock kernel.   Running a modified kernel puts you out of the "official" support status, and you must rely on "unofficial" support. :)  So for a newbie to OpenBSD, it is probably best to stick to the stock kernel.

I haven't run *BSD for a few years, so detection of specific architectures may have changed.

I think it was assumed that for the most part, an old rite of passage was assumed that most users would recompile the kernel or enter the magic of "make world".  Sound a bit like Gentoo?

What I find interesting is FreeBSD now offering PPC support, whereas in the beginning the "focus" of FreeBSD was specific to the 386 architecture, whereas Net/OpenBSD were the ones to stick to multi-architecture design goals.

In the end, try all three and see which one, and which community best fits your needs.  Once you learn one, you pretty much get the hang of the other two, although there are some differences.

---

