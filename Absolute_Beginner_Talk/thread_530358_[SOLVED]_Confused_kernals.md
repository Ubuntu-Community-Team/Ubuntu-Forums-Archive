---
title: "[SOLVED] Confused kernals"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by leedsdevil on 2007-08-20
ok im sure this may be posted in the wrong spot please move to the right one .ok ive read articles on kernals and a bit confused being im still new to Ubuntu. ive built my wife  anice PC its a 1gig pentium it seems to be running ok but i like to make it rite! 1st how do i check to see what kernal im running ( easest way ) i know its to be the 686 kernal and how would i chang it to the right kernal?
                                              many thanks to all

---

### Post by Alex Fernandez on 2007-08-20
uname -r

There is no i686 for Ubuntu there is i386 and generic - most cases you will be using generic now.

---

### Post by leedsdevil on 2007-08-20
so then why is there different kernals out there and what would be the best way tolearn kernals ? thanks

---

### Post by por100pre1 on 2007-08-20
Sometimes there are just kernel updates, a newer version is installed but the old version is not uninstalled, just in case the newer one doesn't work. You can remove older kernels with Synaptic. The i386 is an old kernel, you should use the generic one. There's also a low latency kernel, look for the linux-lowlatency package in Synaptic if you are interested. :)

---

### Post by dptxp on 2007-08-20
> **leedsdevil said:**
> so then why is there different kernals out there and what would be the best way tolearn kernals ? thanks

You may find something useful here on kernels (it is kernels, not kernals, no 'a')
[http://tldp.org/LDP/tlk/tlk.html](http://tldp.org/LDP/tlk/tlk.html)

---

### Post by southernman on 2007-08-20
[http://kernelnewbies.org/KernelHacking]("http://kernelnewbies.org/KernelHacking")

---

### Post by leedsdevil on 2007-08-20
Many thanks to all who reply !:)now i have enought research material to undue the mass confusion Thanks

---

