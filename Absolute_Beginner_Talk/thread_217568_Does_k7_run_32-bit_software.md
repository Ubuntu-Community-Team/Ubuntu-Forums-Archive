---
title: "Does k7 run 32-bit software ?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-07-17
I have a 64 bit cpu but currently a 686 kernel
If I download the k7 kernel, will I be able to run 32-bit software ?

Grtz PingunZ

---

### Post by mostwanted on 2006-07-17
K7 is a kernel optimised for AMD x86 CPU's (not x86_64) which means they it's meant for 32-bit systems.

---

### Post by PingunZ on 2006-07-17
So it wont make a speedboost on my amd athlon64 ?

Grtz PingunZ

---

### Post by PingunZ on 2006-07-17
isnt k7 made for athlon64 ?

Grtz PingunZ

---

### Post by Third Thoughts on 2006-07-17
> **PingunZ said:**
> isnt k7 made for athlon64 ?

Grtz PingunZ

Its made for non 64 AMD chips. I have an Athlon XP 2500 and I run a k7 kernel. I don't know whether or not k7 will help out a 64 kernel. The opinions on this thread seem to go both ways. [http://www.ubuntuforums.org/archive/index.php/t-185951.html](http://www.ubuntuforums.org/archive/index.php/t-185951.html)

~Andrew S.

---

### Post by PingunZ on 2006-07-17
I don't seem to need the k7 but k8 ( [link]("http://ubuntufs.wordpress.com/2006/05/21/easy-speed-up-for-ubuntu/") )
sudo apt-get install linux-k8 ==> package not found

---

### Post by Stormbringer on 2006-07-18
PingunZ,
as you obviously installed the 32-Bit Version of Ubuntu on your AMD64 the whole system is 32-Bit already. The most matching kernel you could therefore install is the -K7 one; the -K8 kernel is ONLY available when running the 64-Bit Version of Ubuntu.

I would recommend you to switch from the i686 to the K7 kernel to get the benefits the kernel may provide you (power management, frequency scaling, ...).

And yes, the K7 kernel is able to run 32-Bit software - it's just an optimized compile for AMD Athlon (or later) class processors.

-Storm

---

### Post by PingunZ on 2006-07-18
Ty very much storm

Grtz PingunZ

---

