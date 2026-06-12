---
title: "Non-Generic Kernel"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Amadeo on 2007-02-07
I have a Pentium 4 2.26GHz processor, and I was wondering which kernel would be more optimized for my computer.  I notice that the only i686 kernel says that it was obsoleted by the generic kernel, so I assume that means the generic kernel is i686.  When installing new video drivers, it wants to install the i386 kernel.  I don't want to hinder performance, so I'm not sure what to do at this point.

Thanks!

---

### Post by mcduck on 2007-02-07
Generic kernel is the right one. It enables optimizations for your CPU at boot, so we don't need separate kernel versions for different CPUs any more.

Anyway, how are you trying to install the video drivers if it's asking for 386 kernel? I bet there's something wrong with those instructions..

---

### Post by Amadeo on 2007-02-07
Thanks for the info!

I was installing from the repository listed here:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

