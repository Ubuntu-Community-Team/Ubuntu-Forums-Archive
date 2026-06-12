---
title: "threading performance, dual quad core"
date: 2007-08-15
forum: Apple Intel Users
---

### Post by agb32 on 2007-08-15
Hi,
I have a dual quadcore mac pro, 3GHz, and have some multi-threaded software that I'm trying to benchmark.

When I run this software on OS X, performance scales nicely with the number of threads, ie using 8 threads means that it is almost 8 times as fast as using 1 thread.

When I try this on ubuntu (latest version), the scaling isn't anything like as nice - I get an improvement between 1-2 threads, and then virtually no more improvement after this.  

Does anyone have any suggestions?  I've tried compiling different kernels, eg turning off preemption, etc, but still cant get the threaded performance up.

Incidently, the software runs faster on Linux than OS X when using 1 thread, but by the time I get to 8 threads, OS X is running faster...

Thanks...

---

