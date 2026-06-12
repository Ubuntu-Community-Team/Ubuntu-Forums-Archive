---
title: "What is the difference between various flavors of kernel"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ajain1102 on 2008-01-14
HI, I am quite new to linux/ubuntu and I am currently on Ubuntu Feisty on my laptop. I am also trying Ubuntu on one of my servers. 

One thing that is confusing me (for which I couldn't really find any satisfactory answer from forums) : what is the difference between various flavors of linux kernel? I noticed that there are 3 difference types of kernels that are available : generic, server and lowlatency. 

I am very curious to know what the difference between these flavors? Does it matter if I use the generic kernel on a server machine (that's what I am doing currently)?

Best Regards,

-Arihant

---

### Post by tgalati4 on 2008-01-15
The kernel can be optimized depending on the workload.  Low-latency is helpful for recording music, but results in a laggy mouse.  Server devotes more CPU cycles to I/O so you won't get snappy desktop performance (mouse and X windows).  Generic is for all-around use including desktop.

Unless your servers get slammed with traffic like a new OK GO video, generic will work just fine.

---

