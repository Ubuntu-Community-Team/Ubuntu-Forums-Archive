---
title: "linux-headers, linux-image, linux-x86 explanation please"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by r00tuk on 2006-07-07
Hi, I am quite new to linux and I have trying to find out what the following mean, how they relate to each other and when do you need to install them?

linux-686-smp
linux-headers-2.6.15-25-686
linux-image-2.6.15-25-686

Thanks

---

### Post by Hallavej on 2006-07-07
> **r00tuk said:**
> Hi, I am quite new to linux and I have trying to find out what the following mean, how they relate to each other and when do you need to install them?

linux-686-smp
linux-headers-2.6.15-25-686
linux-image-2.6.15-25-686

Thanks

1)
This package will always depend on the latest complete Linux kernel available for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV with SMP support. SMP (symmetric multi-processing) is needed if you have multiple processors.
2)
The kernel headers. You wont need them unless you compile programs yourself.
3)
This is linux. You will always need that. Everything depends on the linux kernel.

---

