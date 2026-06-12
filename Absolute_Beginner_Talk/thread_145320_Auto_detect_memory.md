---
title: "Auto detect memory?"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by blackant on 2006-03-16
I am about to upgrade my computer's memory, and I'm wondering whether does ubuntu auto detects the changes or I need to manually do some settings to it?

And if I need to do it manually, what are the steps?
Thanks.

---

### Post by Sendervictorius on 2006-03-16
Your PC should automatically detect the new memory during power-on. It's not an operating system option.

Linux will make maximum advantage of any memory it can find for data caching.

---

### Post by mcduck on 2006-03-16
Memory is of course autodetected. But if you are going to upgrade to 1GB or more, you might want to make sure you are using 686 or K7 kernel to make use of all that RAM.

686 kernel works for all new Intel and AMD CPU's, K7 kernel is for Athlons and later AMD CPU's and SMP-versions of kernels are for multi-CPU/Multicore and hyperthreading CPU's.

To install one, install package called 'linux-686' or 'linux-K7' or which ever fits your setup. You can do that with synaptic, or running 'sudo apt-get install linux-686'. After that boot the machine to load the new kernel, and if everything is working fine you can remove all the 386-kernel packages.

---

### Post by blackant on 2006-03-16
ok.. thanks for the reply.
hopefully it will increase the performance of my linux box. :D

---

### Post by mcduck on 2006-03-16
[QUOTE=blackant]ok.. thanks for the reply.
hopefully it will increase the performance of my linux box. :D[/QUOTE]
I'm sure it will. For basic computer use, memory means more than CPU power. :)

---

