---
title: "Kernel Update"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-07-18
Noticed there is a new kernel out and found a nice guide [http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)

Is it essential to update the kernel (Is it like windows update fixing security holes)?

I notice once the kernel is updated i have to re-install my graphics drivers, i dont understand why though, will i have to reinstall everything? e.g java, flash, plugins?

:(

---

### Post by linuxnewbie946 on 2006-07-18
I wrote that guide and no it is not essential, it just makes your system faster. You won't have to install everything all over, just your nvidia drivers.

---

### Post by linuxnewbie946 on 2006-07-18
If you don't have an Nvidia card, you have no need to reinstall the drivers.

---

### Post by PriceChild on 2006-07-18
You may not see any difference by building your own kernel, then again, maybe you will.

I used to, but don't bother anymore because i'm 99% it stops some features of ubuntu like the way mounted discs appear on the desktop. Might just have been my other tinkering though.

---

### Post by Dinerty on 2006-07-18
The guide does seem a good one, will think about this one me thinks lol

---

### Post by PriceChild on 2006-07-18
Yeah there's definately no reason why not... i did learn quite a bit :)

---

### Post by linuxnewbie946 on 2006-07-18
I cant take all the credit......... I based it on this thread [http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560)

---

### Post by Dinerty on 2006-07-18
How often to updated kernels get relased?

---

### Post by linuxnewbie946 on 2006-07-18
in the past week, minor releases are almost every day, but major releases ar 2-3 months

---

### Post by givré on 2006-07-18
> **Dinerty said:**
> How often to updated kernels get relased?
Compiling you're own kernel as nothing to do with updating your kernel (like the windows update if you want). 
Each distribution come with a specific kernel, which was build for their need (patch of module, addition of feature...)and is designe to be use by everyone. This kernel is update regulary to fix bugs (the first one for dapper was 2.6.15-23 and now we have the 2.6.15-26) and if you stay with this one you will receive further update of the kernel to make him even more stable.

Now you can choose also to compile your own kernel to profit to the latest one (2.6.17 is the latest, the one of dapper is 2.6.15 based), like you can do for every piece of software of dapper. but you will loose the support and potentiel compatibility with other package (like ndiswrapper, nvidia-glx package...).
But if you know what you are doing and if you have enough skill to do it, you could gain a lot by compiling you're own kernel.
- First you will learn how is working the kernel.
- You will potentialy improve speed (if you choose with attention your modules).
- You will profit of some new driver (even if some of the driver in the dapper's kernel are backported from the 2.6.17 kernel)

Now, and like for everything in linux, you have the choice. 8)

---

### Post by Dinerty on 2006-07-18
> **givré said:**
> Compiling you're own kernel as nothing to do with updating your kernel (like the windows update if you want). 
Each distribution come with a specific kernel, which was build for their need (patch of module, addition of feature...)and is designe to be use by everyone. This kernel is update regulary to fix bugs (the first one for dapper was 2.6.15-23 and now we have the 2.6.15-26) and if you stay with this one you will receive further update of the kernel to make him even more stable.

Now you can choose also to compile your own kernel to profit to the latest one (2.6.17 is the latest, the one of dapper is 2.6.15 based), like you can do for every piece of software of dapper. but you will loose the support and potentiel compatibility with other package (like ndiswrapper, nvidia-glx package...).
But if you know what you are doing and if you have enough skill to do it, you could gain a lot by compiling you're own kernel.
- First you will learn how is working the kernel.
- You will potentialy improve speed (if you choose with attention your modules).
- You will profit of some new driver (even if some of the driver in the dapper's kernel are backported from the 2.6.17 kernel)

Now, and like for everything in linux, you have the choice. 8)

Thank you very much for the explaniation I understand now. I'm going to stick with the official one, everything works and I will get updates that way !

Thanks again

---

### Post by crag277 on 2006-07-18
I know I will have to re-install some things after Ubuntu updates the kernel to 2.6.15-26, but what exactly needs to be reinalled?  I'm not looking for a specific list, just more of an explaination as to what types of software are kernel versio specific.  I know I need to reinstall ATI drivers and ndiswrapper, but are there any other major ones?

Also, is there any need, or any way for that matter, to uninstall the drivers before re-installing them?  Or does each driver install to its own kernel-specific location?

Thanks

---

### Post by OU812 on 2006-07-20
If ubuntu were using lilo, after a kernel upgrade you would need to run lilo from bash. Is there anything extra that must be done to give ubuntu a heads up to the new kernel? Thanks.

john

---

### Post by givré on 2006-07-20
See the sticky post [http://ubuntuforums.org/showthread.php?t=213420](http://ubuntuforums.org/showthread.php?t=213420) ;)

---

### Post by lzfy on 2006-07-20
So when you update your kernel with the official Ubuntu updates do you have te reinstall some stuff too? Or is it only when you update manually.

---

### Post by givré on 2006-07-20
Okay, let make it clear. I understand that this kind of things are not really easy to understand when you come from windows, so i'll try to be clear.

First i think that the term 'mannually updating the kernel' is not appropriate. When you compile a kernel from kernel.org, you install a new kernel.
The difference between the vanilla kernel 2.6.15 (term we give to kernel which are directly from kernel.org) and the ubuntu kernel 2.5.15-26 is that the ubuntu kernel is highly patch. If you had install the vanilla 2.6.15 kernel and install the new 2.6.17 vanilla kernel, you can say that you update your kernel, but if you do that after the ubuntu kernel, it's like installing an other branch of the kernel tree, if you want, which is surely better, but which is quite different, and you probably don't recover some fonctionnality you had with the ubuntu kernel. An easy way to now the difference made in the ubuntu kernel is to look at /usr/share/doc/linux-image-2.6.15-26.


That's say,i highly encourage people to try to compile their own kernel, because you learn a lot, but it's could be a bit tricky, and you could be sure that the first time it will fail. After lot's of experience, you can make it fit your system, so that'll make it stronger and faster, but you will have to pass a lot of time for this result. So if you are newbie, wait a bit, learn a lot, and if you had some time, try it.

So now, what to reinstall after a kernel update. The main rule is:
one module, one driver <-> one kernel.
So if you compile yourself a driver or a module (ex: you download your ATI driver from ati.com and compile it) you will have to redo the operation when you update your kernel, but if you did nothing of that, you don't have to worry. The only thing that you have to pay attention at, is to be sure that you upgrade your linux-image & your linux-restricted-module, because some restricted driver (like the ATI or the nvidia one) are in the second package, and it's why it's recommanded to be sure that linux-arch is install, because that will done that automaticly. It's done by default, but it's better to check that before than to fix it after.

And to be more clear, if you don't have to recompile driver for ATI $ nvidia if you installed them from the repo, it's because linux-restricted-module already contain them.

---

### Post by OU812 on 2006-07-20
Thanks givre. I read everything very quickly. When I have time I'll read it again for better understanding. Nicely done.

john

---

