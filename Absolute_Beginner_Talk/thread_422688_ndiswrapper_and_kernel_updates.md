---
title: "ndiswrapper and kernel updates"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-04-25
I've just switched from edgy to feisty on my laptop, which contains the dreaded broadcom 4328 chipset in the wireless.  My friend who initially got my wireless going for me in my Dapper days recommended I just don't update the kernel, because I would have to fix the wireless everytime.  My question is, can I write a bash script that I can run everytime I update  the kernel?  And also, to get the wireless working again, do I just need to ```
modprobe ndiswrapper
``` to inject ndiswrapper into the kernel?  Or do I need to recompile ndiswrapper everytime, then insert the driver into ndiswrapper, then finally modprobe ndiswrapper?
 
On a side note, I feel like a big boy just considering writing a bash script to solve a problem.  It will be my first.

---

### Post by joft on 2007-04-25
Hmmm, in fact, the ndiswrapper kernel module is part of every linux-image-* package. So upgrading to a newer kernel version, means you also get an upgraded ndiswrapper module, so, yes, it should suffice to just modprobe ndiswrapper. The recompilation of the module is done by Ubuntu's kernel team ...

---

### Post by xboxbman on 2007-04-25
> **joft said:**
> Hmmm, in fact, the ndiswrapper kernel module is part of every linux-image-* package. So upgrading to a newer kernel version, means you also get an upgraded ndiswrapper module, so, yes, it should suffice to just modprobe ndiswrapper. The recompilation of the module is done by Ubuntu's kernel team ...

dope. thanks for the response

---

### Post by theotherjoey on 2007-05-07
Can you tell me how you got it working with that chipset in the firstplace? I have a new HP dv6000 with a 4328, and I can't figure it out.

---

