---
title: "What is the Amd K7 Kernel everyone is talking about?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-12
I have an AMD Sempron 64 (s754) which is a K8 chip, but people are telling me if I want better performance to get the K7 kernel, Some guy I remember telling me this had a AMD Athlon X2 and said it helped him a lot. So, Im taking that this should help me too? lol :D 

My problem is that my cpu loads easy (its a budget chip so it happens :P) so Im trying to find a way to get better performance.

---

### Post by WalmartSniperLX on 2006-09-12
Its called linux-k7. I found a lot of similar things in Synaptic Package Manager

---

### Post by codejunkie on 2006-09-12
> **WalmartSniperLX said:**
> I have an AMD Sempron 64 (s754) which is a K8 chip, but people are telling me if I want better performance to get the K7 kernel, Some guy I remember telling me this had a AMD Athlon X2 and said it helped him a lot. So, Im taking that this should help me too? lol :D 

My problem is that my cpu loads easy (its a budget chip so it happens :P) so Im trying to find a way to get better performance.

The k7 kernels are optimised specifically for amd k7 processors.
The default ubuntu kernel is optimised for 386 intel processors, it should work fine with newer intel and amd processors, it's just not made specifically for them. 

as for the k7 kernel it's not specifically optimized for your processor either, but you might get better preformance with it than you do with the default kernel since it's compiled for newer processors than the default kernel is. 

to be honest with you i have an amd64 3400+ and i've tried the standard 386 kernel, the k7 kernel, and kernels customised for this processor and i can't notice much difference at all between the 386 & k7 kernels. now the custom built kernels seem to be a little better because they are optmised for my hardware but for what you gain it's not worth the time compiling and tinkering with the kernel.

---

### Post by WalmartSniperLX on 2006-09-13
> **codejunkie said:**
> The k7 kernels are optimised specifically for amd k7 processors.
The default ubuntu kernel is optimised for 386 intel processors, it should work fine with newer intel and amd processors, it's just not made specifically for them. 

as for the k7 kernel it's not specifically optimized for your processor either, but you might get better preformance with it than you do with the default kernel since it's compiled for newer processors than the default kernel is. 

to be honest with you i have an amd64 3400+ and i've tried the standard 386 kernel, the k7 kernel, and kernels customised for this processor and i can't notice much difference at all between the 386 & k7 kernels. now the custom built kernels seem to be a little better because they are optmised for my hardware but for what you gain it's not worth the time compiling and tinkering with the kernel.

Ok thanks :D

---

### Post by 3rdalbum on 2006-09-13
Don't quote me on this, but I think the k7 kernel increases your performance when you use it with the other system optimisations (preload and prelink).

---

