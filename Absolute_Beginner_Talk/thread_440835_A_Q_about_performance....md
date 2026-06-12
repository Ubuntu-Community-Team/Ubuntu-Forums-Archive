---
title: "A Q about performance..."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2007-05-12
Hey Guys,

I just bought a laptop - Toshiba Sattelite a100/500 - and have installed 7.04 on it... however despite this... i get poor performance from both my GeForce Go 7300 and my Core 2 Duo Processor. Is there anyway to modify my kernel to increase performance with my processor? I recall being able to do something like that with red hat 9

---

### Post by Billy McCann on 2007-05-12
make sure you're using a symmetric multi-processor kernel.  

in a terminal run: uname -a

At the end of the kernel name there should be a SMP.

---

### Post by Dev'olution on 2007-05-12
> **Billy McCann said:**
> make sure you're using a symmetric multi-processor kernel.  

in a terminal run: uname -a

At the end of the kernel name there should be a SMP.

```
Linux kristian-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```

Thats the out put i am getting. I'm assuming its the SMP kernel.

---

### Post by Dev'olution on 2007-05-12
Is there any way i can do a benchmark on my machine?

---

### Post by Kobalt on 2007-05-12
Hve you installed the latest drivers for your graphic card ? (these would be nvidia-glx-new, 9755, from Synaptic)
I have no idea about your benchmark though...

---

### Post by Billy McCann on 2007-05-12
You could always compile a kernel from source.  :KS

---

