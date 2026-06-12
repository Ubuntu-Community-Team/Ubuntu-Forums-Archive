---
title: "2012 MacBook Air (5,2) runs too hot, even with fans at full speed"
date: 2012-08-20
forum: Apple Hardware Users
---

### Post by sgarman on 2012-08-20
Hello,

I have a 2012 MacBook Air (5,2) which I am running with Ubuntu 12.04 installed natively. I have installed the latest applesmc kernel module from the mactel-support PPA, and run macfanctld.

Under normal user operations (web browsing, email, etc) the system runs fine and my CPU core temps are normal (50 - 60 degrees C).

However if I run a compile that uses both cores that lasts more than a few minutes, my CPU temperature gets dangerously hot - up into the 90's C, and I've even seen it reach 100 C. I will cancel my compile at that point because this is clearly an unsafe temperature to be running at. 

During this time the fans do correctly crank up to maximum speed (6200 RPM), so the problem isn't that my fans aren't working correctly.

Since I do long-running compiles of embedded Linux distros that take hours at a time to complete, I'd like to run a daemon that throttles my CPU speed once the temps reach a threshold (e.g, 90 C). 

Unfortunately cpufreqd does not work and segfaults upon starting. The issue is described here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=644567](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=644567)

I have rebuilt the Ubuntu Precise cpufreqd debian package with the suggested patch, but it now segfaults for another reason when starting. :(

Can anyone give me advice on something I can do to keep my CPU from getting this hot? I'm running out of ideas.

Thanks,

Scott

---

### Post by xTRICKYxx on 2012-08-21
Ivy Bridge CPU's temperature threshold is 105 celsius before they start to throttle automatically. 
Ivy Bridge traditionally runs a lot hotter than Sandy Bridge.

---

### Post by 2blue on 2012-08-21
edit

wrong tread post.

---

### Post by sgarman on 2012-08-21
> **xTRICKYxx said:**
> Ivy Bridge CPU's temperature threshold is 105 celsius before they start to throttle automatically. 
Ivy Bridge traditionally runs a lot hotter than Sandy Bridge.

Can you point me to some online documentation about this? I'd just like to confirm it, as 105C seems an amazingly high temperature for a CPU to handle for long periods. 

I can't seem to find anything definitive to tell me what the maxiumum operating temperature of the processor is, but according to this spec, the Tjunction temperature is 105 C:

[http://ark.intel.com/products/64898/Intel-Core-i7-3667U-Processor-%284M-Cache-up-to-3_20-GHz%29](http://ark.intel.com/products/64898/Intel-Core-i7-3667U-Processor-%284M-Cache-up-to-3_20-GHz%29)

My understanding of Tjunction is the temperature at which the CPU will shut itself off to protect against permanent damage. Am I mistaken?

Also, I was under the impression that due to the smaller process technology (22nm) of Ivy Bridge, the processor would use less power and generate less heat, compared to Sandy Bridge (32nm). I don't understand why it would be the opposite.

Thanks, I'd like to learn more about this.

Scott

---

