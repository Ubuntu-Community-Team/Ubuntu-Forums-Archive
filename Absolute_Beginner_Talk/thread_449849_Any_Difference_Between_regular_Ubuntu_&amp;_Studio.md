---
title: "Any Difference Between regular Ubuntu &amp; Studio versions"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2007-05-20
I installed Ubuntu Studio earlier today.  Is there any difference between Ubuntu 7.04 and Ubuntu Studio 7.94 besides the packaging of a lot more multimedia software and a different default theme?  In menu.lst, regular Ubuntu is labelled "Ubuntu, kernel 2.6.20-15-generic", while the studio version is labelled "Ubuntu, kernel 2.6.20-15-lowlatency".  Is there a difference?

Don

---

### Post by earobinson on 2007-05-20
> Why Reduce Scheduler Latency?

Having a large scheduler latency means that the kernel doesn't respond very quickly to I/O events. If you're building a Personal Digital Recorder (PDR), then you are going to be processing the heck out of MPEG audio/video streams and you will want the kernel to schedule your MPEG decoder process as quickly as possible. If somebody misses the juicy bits from their favorite B-movie because the video stream glitched, they're not going to care that it's because the kernel was slowed down by a particularly slow write to the internal disk. They're just gonna be mad that the movie looks jerky.

Another example is companies that are implementing DSL modems with minimal hardware. To reduce the cost of the device they want to do away with the Digital Signal Processors (DSPs) that are used to process the analog signals on a phone line into DSL cells or frames. They do this by offloading the signal processing algorithms to the main processor (similar to the things that the infamous WinModems do). To successfully implement this sort of scheme requires that the interrupt dispatch latency and thread scheduling latency be minimized in the kernel. 

[http://www.linuxdevices.com/articles/AT8906594941.html](http://www.linuxdevices.com/articles/AT8906594941.html)

---

