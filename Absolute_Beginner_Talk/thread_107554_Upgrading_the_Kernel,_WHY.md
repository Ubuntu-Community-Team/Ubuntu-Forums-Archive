---
title: "Upgrading the Kernel, WHY?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by DJiNN on 2005-12-23
Could anyone tell me .....

A:) How easy it is (Or indeed how difficult) to change the standard 386 Kernel supplied with Ubuntu, to a more modern "686" version? (Sorry if i have used the wrong Terminology when describing the different Kernels) :)

B:) WHY do it in the first place? In other words, is their much of a difference? I'm running a 2.4ghz P4 & would like to have some idea of any improvements tec.

Thanks for your time.

DJiNN

---

### Post by mcduck on 2005-12-23
Easy as anything. Open terminal, type 'sudo apt-get install linux-686', enter your password and wait. When it's ready, reboot. Or if yor CPU supports hyperthreading, install linux-686-smp to enable hyperthreading support.

You'll gain at least support for higher amounts of RAM, so if you have 1GB or more you should definitely upgrade your kernel. SMP-kernels are needed for hyperthreading- or multicore CPUs.

Other than that, the default 386-kernel supports only MMX-multimedia instructions, but 686-one supports MMX, MMX EXT and SSE, and those can make some difference when working with images, sound and video. (I'm not sure about what Ubuntu kernels actually support, but I think this would be close to truth at least ;) )

Anyway, there's nothing to loose. The old kernel stays installed, and if the new one doesn't work for some reason you can always select the old one from Grub menu when booting.

---

### Post by 23meg on 2005-12-23
Check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=85917").

---

### Post by DJiNN on 2005-12-23
[QUOTE=mcduck]Easy as anything. Open terminal, type 'sudo apt-get install linux-686', enter your password and wait. When it's ready, reboot. Or if yor CPU supports hyperthreading, install linux-686-smp to enable hyperthreading support.

You'll gain at least support for higher amounts of RAM, so if you have 1GB or more you should definitely upgrade your kernel. SMP-kernels are needed for hyperthreading- or multicore CPUs.

Other than that, the default 386-kernel supports only MMX-multimedia instructions, but 686-one supports MMX, MMX EXT and SSE, and those can make some difference when working with images, sound and video. (I'm not sure about what Ubuntu kernels actually support, but I think this would be close to truth at least ;) )

Anyway, there's nothing to loose. The old kernel stays installed, and if the new one doesn't work for some reason you can always select the old one from Grub menu when booting.[/QUOTE]


Thanks for the heads up on that mcduck.... just doing it now. Didn't realise that it was/is so straightforward...... :) Fingers crossed for a positive outcome.  I'm mostly (With the exception of an old PIII 500 Laptop) running on recent hardware (I'm converting several machines to Ubuntu) so it's worth doing i think......

Many thanks indeed.......

DJiNN

---

### Post by DJiNN on 2005-12-23
Well, it worked...!! I have 1gb of RAM as well, & the machine seems a lot "Snappier" than it was..... haven't done any benchmarks etc, but it just seems quicker.....

I'm happy anyway... :) Many thanks for the info..........

DJiNN

---

