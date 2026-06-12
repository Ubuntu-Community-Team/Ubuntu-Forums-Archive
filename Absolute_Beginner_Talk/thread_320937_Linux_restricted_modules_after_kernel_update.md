---
title: "Linux restricted modules after kernel update?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-18
Hi,

I'm running Edgy Eft and I've compiled the newest vanilla kernel (2.6.19.1). I've read somewhere that after a kernel update one should always reinstall the Linux restricted modules that correspond to the new kernel. To do so I could find the following command:

sudo apt-get install linux-restricted-modules-$(uname -r)

Obviously the last vanilla kernel is not in the Ubuntu repositories so this command doesn't work. But then how can I install the restricted modules for the 2.6.19.1 kernel? Are these really required? My system boots fine with the new kernel (I only have a few lines poping during the boot process but this all goes so fast that I can't read what's written). What are these restricted modules for?

Any suggestion?

---

### Post by Bachstelze on 2006-12-18
You only need to install the Restricted modules if you need them ;) They contain drivers that are non-free and thus cannot be included in the main kernal package. If your system boots fine without them, I guess you simply don't need them.

---

### Post by Jasman on 2006-12-18
If you want propriety drivers for graphics (ATI or NVIDIA), you either need an Ubuntu kernel with restricted modules or you need to look for a thread on compiling modules with your kernel, which means you need to compile again (AFAIK). FYI, the Feisty kernel is currently at 2.6.19 or 2.6.20, and there are restricted modules in the feisty repositories, so this might save you some trouble. On the other hand, it might mess everything up.:(

---

### Post by kilou on 2006-12-18
I would need to compile the kernel anyway because I want to install suspend2 (hibernation) and linux-phc (undervolting) patches..... So no way to install restricted modules for a vanilla (non ubuntu) kernel?? Well I mean no way to compile restricted modules in my kernel myself???

---

### Post by kilou on 2006-12-18
Probably a stupid question but....is it possible to install the restricted modules for 2.6.17.10 (Edgy eft kernel) with the new vanilla kernel 2.6.19.1??????

---

### Post by Jasman on 2006-12-19
I don't know the actual answer to either of these questions, but if you look for threads on compiling ATI or NVIDIA (I think it'd be similar) drivers for a newly compiled kernel, you'll see that the restricted modules package isn't necessary. Basically, I think the restricted modules packages just allow you to run proprietary modules with the stock Ubuntu kernels. I'm sure somebody else could explain this better than I can, but that's the basic idea.

---

