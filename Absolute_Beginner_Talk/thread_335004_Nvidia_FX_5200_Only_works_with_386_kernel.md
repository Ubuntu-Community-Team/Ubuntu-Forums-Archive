---
title: "Nvidia FX 5200 Only works with 386 kernel?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-01-09
I have a 128 MB Nvidia Geforce FX 5200 graphics card, and after attempting to install the proprietary drivers, it only works using the 386 kernel. 

When I type $glxgears

under the 386 kernel, the gears run great
under the 686 kernel, it freezes up.

Am I doing something wrong, or do I have to run a 386 kernel?

Computer is a dell desktop, pentium 4 processor

-Andrew

---

### Post by taurus on 2007-01-09
I have P4 and I use the 386-generic kernel and it is running just fine with the nVidia driver using this guide...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Atreus12 on 2007-01-10
I'm confused now. I read through the dapper customization guide, and it said to run the 686 kernel on a pentium 4. Is there an advantage to the 686? And why will the nvidia driver only work on the 386?

-Andrew

---

### Post by teaker1s on 2007-01-10
386i is for any single core x86,
 686 should I believe supports hyper threading;)

---

### Post by Delkster on 2007-01-10
> **Atreus12 said:**
> Is there an advantage to the 686?

It takes better advantage of some features in recent hardware that wasn't available in the older days. However, the 686 kernel won't run on old hardware, so the 386 one (which is the 'lowest common denominator' version) is a safer bet and is used by default.

> And why will the nvidia driver only work on the 386?

I don't know, but have you made sure that you also have the 686 version of the linux-restricted-modules package installed? Search for that name in Synaptic and see which package(s) you have installed.

---

