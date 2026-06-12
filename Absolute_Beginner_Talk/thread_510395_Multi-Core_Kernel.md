---
title: "Multi-Core Kernel"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by fattom23 on 2007-07-26
What is the easiest way to add dual-core support to an Ubuntu kernel?  I've been using the 2.6.17-386 kernel, since I've had a lot of severe stability issues with the generic kernel.  Is there an easy way to modify the 386 kernel to support DC?  My first experiment with kernel compilation not only resulted in a kernel panic, but somehow wrecked the rest of my system, also, so I'll probably be re-installing with Feisty (which has given me the worst problems in the past with the generic kernel).  I'm happy to continue the kernel compilation, but only if there's no easier way.  Thanks a lot for any help that you can provide.

---

### Post by jd65pl on 2007-07-26
Dual core is supported by the generic kernel, there is no longer a separate smp kernel for multi-processor systems as they are supported by generic.

You should not need to compile the kernel yourself to achieve multi processor support, it is likely that something else is causing you problems.

Are you certain that both cores are not being used? and how have you determined this?

Also could you provide more detail on stability issues??

Thanks

J

---

### Post by reckless2k2 on 2007-07-26
generic does more or less cover it but you should still grab the smp image from the repos

---

### Post by jd65pl on 2007-07-26
Read:[this]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html") and [this]("http://ubuntuforums.org/showthread.php?t=243896") on kernels

---

### Post by fattom23 on 2007-07-26
My entire goal is to not use the generic kernel.  For reasons that are unclear to me or anyone else, my X session completely locks at random (but frequent) intervals when using the generic kernel.  I don't have any problems with the 386 kernel, but this doesn't allow me to use my dual core (only one processor is recognized).  Basically, I want to enable dual core support in the 386 kernel (or get as close to that as possible.  Sorry if I was unclear initially.

---

### Post by por100pre1 on 2007-07-26
Well, if you really want to try another kernel you can try the low latency kernel:

```
sudo aptitude install linux-lowlatency
```

I use one as part of Ubuntu Studio and works fine to me, hope this helps.

---

