---
title: "Ubuntu on MBP: It works, but is it safe?"
date: 2007-05-12
forum: Apple Intel Users
---

### Post by (pr) on 2007-05-12
Getting Ubuntu working on a MBP isn't that hard to do. I love the system and love the play around with it. The system tends to get really hot and the graphics aren't wow. I have a MBP with a 256mb video-card and still not every graphical interface (cf. beryl & emerald) work super-smooth. 

I'm just saying: Yes it works and from a software point-of-view it works superb. But is it safe to use Ubuntu (as primary system) on a Apple/MBP knowing that heat and the graphicsdriver aren't really doing what they should do. 

I love Ubuntu and want to use it, but not in a way that it will ruin my laptop in a near future.

---

### Post by benanzo on 2007-05-12
It's not any less-safe than running demanding tasks on OS X.

There is significant focus in the Linux kernel development community right now to implement some really excellent and robust power-management code for laptops.  This has been a major barrier for many in putting Linux on their machines.  The whole process of kernel development for mobile machines is quite different than it has been for more traditional hardware.  Most-all the code for laptop hardware was actually introduced for use on blade servers (which used laptop components) and while they were concerned about heat and power-consumption, there was not nearly enough effort put into enabling these advanced capabilities (mainly because much of the code was coming from IBM who (understandably) cares much more about getting their blade-server racks up-to-snuff than (re)writing the code for use on laptops.)

I think we're going to see some big improvements in 2.6.22+ kernels soon.
Have a look at the linux-kernel/ACPI mailing list: [http://www.mail-archive.com/linux-acpi%40vger.kernel.org/](http://www.mail-archive.com/linux-acpi%40vger.kernel.org/)

It's really technical, but oh so interesting.

---

