---
title: "Kernel question,"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-01-11
I heard this:
>  10. A new kernel

Ubuntu will install a 386 kernel for x86 machines, which probably isn't what you'd want if you've got a Pentium II or better CPU. The 386 kernel is compiled to work with just about any x86 CPU, but extensions that appear in later CPUs can give your system a boost, if they're taken advantage of. To replace the kernel, open Synaptic or Adept and search for linux-image. You'll see several choices. Pick the one that best suits your CPU -- probably the linux-image-686 package for Pentium II and later CPUs, and linux-image-k7 for later AMD processors. Note that if you're using the AMD64 line (or Intel's x86-64 CPUs) you should be using the amd64 images.

Of course, once you install the new kernel, you'll need to reboot. Another benefit to the 686 kernels is that they have SMP support, which is a bonus for multi-core and Intel HyperThread CPUs.

I have a sony vaio pcg-tr3a lappy with a **1gHz Pentium M** and **512 MB DDR SDRAM**
will getting some other kernel make things faster? 
Synaptic tells me I have the Linux kernel image for version 2.6.22 on x86/x86_64 installed. And also Generic Linux kernel image (2.6.22.14.21)

So, besides updating my hardware to like 1 gig of RAM or something, how can I make my computer go faster?

thanks!!!

sv

---

### Post by Pevichaey5 on 2008-01-11
i download the latest kernel from [kernel.org](www.kernel.org) and compile it urself

then i would disabled some un-needed services

---

### Post by staticvoid on 2008-01-11
> then i would disabled some un-needed services
yeah like bluetooth...

can I majorly screw up my system if I recompile and stuff? is it hard to do?

downloading the latest right now... or do I just need a patch?

btw, thanx for the quick reply!!

:)

sv

---

### Post by nowshining on 2008-01-11
a guide for optimizing for ur particular cpu and how to build and change add/remove - that u'll have to read bout and do on ur own but optimizing for ur particular cpu, then check my site. Give me feedback if u want to, it's in the tips,fixes,howtwos section.

No, not really unless u keep ur current kernel for backup - keep at least one, it will be kept automatically if u get an error at boot press esc at the grub prompt and look for ur old kernel with out the recovery option and hit enter on ur keyboard.

IF u use ATI, NVIDIA cards u'll have to re-install them via command line, maybe if u at most use the one from the ATI, Nvidia site.

it's relatively easy to do, also make sure u either go thru the ftp, http, don't click the download from the main homepage - it's only a patch and the kernel download is not about 5-11mb it's roughly 50-60mb, my site tells u where to download it. :)


oh and the latest stable version is 2.6.23.13 -  2.6.24.xxx and so forth are still in development.

---

### Post by staticvoid on 2008-01-11
reading your howto right now....

yeah, I downloaded the patch and was like "whatever... a kernels gotta be bigger then that" to I clicked  "full" but anyway... i'll just use your howto.

I see you are active on the forums, must be up to date :D

sv

---

### Post by nowshining on 2008-01-12
hehe :)

---

