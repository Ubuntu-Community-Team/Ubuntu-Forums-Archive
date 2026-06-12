---
title: "Problems with sky2 driver after kernel update in feisty"
date: 2007-06-25
forum: Apple Intel Users
---

### Post by wojtekz on 2007-06-25
Hi,

I have an Intel-based mac mini running Ubuntu feisty. My system was running stable until I updated the default kernel (2.6.20-15) to kernel 2.6.20-16 that came with apt-get upgrade. With the new kernel, my network interface (built-in Marvell 88E8053 gigabit ethernet) stopped working. I guess this is due to some changes in the sky2 driver that comes for Marvell ethernet cards.

Does anyone else experience the same problem?

Thanks in advance,
Wojtek

---

### Post by ronocdh on 2007-06-25
> **wojtekz said:**
> Hi,

I have an Intel-based mac mini running Ubuntu feisty. My system was running stable until I updated the default kernel (2.6.20-15) to kernel 2.6.20-16 that came with apt-get upgrade. With the new kernel, my network interface (built-in Marvell 88E8053 gigabit ethernet) stopped working. I guess this is due to some changes in the sky2 driver that comes for Marvell ethernet cards.

Does anyone else experience the same problem?

Thanks in advance,
Wojtek
I heard of lots of MadWiFi breakages during the 15-16 upgrade (it happened to me, too). I've never lost ethernet functionality, but I do rarely use it (just confirmed that it worked, just in case). But then, I'm on a MBP.

This would be an awesome time to compile a list of hardware in all the models and generations of the Apple computers. We could create a thread for listing them out, where users post their hardware and date of purchase and lspci output. Just a thought.

---

### Post by Gen2ly on 2007-06-25
Drivers at times compile against the kernel, madwifi I know for sure is.  Some drivers choose not the be put into kernel.  It's in /usr/lib/modules/kern-version/ if I remember right.

---

