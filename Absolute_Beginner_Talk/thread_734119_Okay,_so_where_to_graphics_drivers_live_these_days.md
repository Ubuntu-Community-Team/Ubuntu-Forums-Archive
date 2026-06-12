---
title: "Okay, so where to graphics drivers live these days?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by walkeraj on 2008-03-24
It's been about four years since I used linux with a fair amount of regularity, but with the advent of Windows Vista and the death of my venerable Vaio laptop, I decided to go for it and buy a System 76 laptop with Ubuntu pre-installed.

So far it's great, but running the stock gutsy version of wine caused XOrg to crash entirely.  This, of course, was a driver problem.  An upgrade to Hardy fixed it, however this introduced new problems, so I've decided to go back.  This has led to an interesting question for me: **where do the graphics drivers live and what program controls them?**

I learned Linux via Slackware in the late 90s, and, as far as I knew, graphics drivers either lived in or were modules to the kernel.  If you had a card you wanted to use and it wasn't in the stock kernel, it was simply a matter of doing a *make menuconfig* and selecting all of the proper options.  Sure, there was the framebuffer, but it wasn't very fast a lot of the time and was largely experimental.

Linux has come a long way on a lot of fronts since then, and when I asked the support guy at System76 about my drivers, he told me they came in the package *xserver-xorg-video-intel*.  This implies to me that it is XOrg handling the drivers now somehow.  Is that how it works, or does this package basically install a kernel module?

Also, let me know if I have some misunderstanding in the way this works.  I'd be glad to know :).

---

### Post by Sam Lars on 2008-03-24
Yes, there are packages like that, and they install the drivers for Xorg.  If you want to know where they are, you can go into Synaptic, and right click on the package, properties, and there's a tab with the files it has installed.

---

