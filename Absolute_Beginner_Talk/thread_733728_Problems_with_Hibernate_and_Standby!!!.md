---
title: "Problems with Hibernate and Standby!!!"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by mohd646 on 2008-03-24
Hi everyone,
I'm new to Ubuntu community and Ubuntu OS. I've already installed my own Ubuntu 7.10 (i think it's called Gusty or something like this:confused:) and I already updated this version from the net.

I faced many problems, but I'm working on to solve all of them by searching in the net and asking the experts (as you guys :guitar:).

One of these problems is when i choose to Hibernate, Ubuntu would not hibernate and instead it just show me a black screen (which means it is in progress!!!) and the nothing happen. And that force me to shut down the pc manually (by pressing and holding the power button:mad:) So, how to fix this issue??

But Standby is better than Hibernate. it shows some respect. But the only problem with Standby is that the light of the power button is still turned on!!!!  why??

---

### Post by erginemr on 2008-03-24
For standby and hibernate, except the fact that Ubuntu has to like your hardware first, you need to have enough swap for hibernate to dump the memory in to.

Your swap size should at least be the size of your real RAM. You can check the swap size with "top" (or better by installing "htop") from the terminal.

Please refer to this topic as well:
[http://ubuntuforums.org/showthread.php?t=406031](http://ubuntuforums.org/showthread.php?t=406031)

---

### Post by mohd646 on 2008-03-25
The swap size is twice the RAMs

I have 1024MB of RAM
and the swap size is 1906 MB

so, i think the problem is something else. any comments???

---

### Post by erginemr on 2008-03-25
Not that I have a response, but I think you should also give your computer specs to ease the indentification of the problem by other forum members.

---

### Post by AdamG51172 on 2008-04-14
```
But Standby is better than Hibernate. it shows some respect. But the only problem with Standby is that the light of the power button is still turned on!!!! why??
```
Just in case, I'm including some info on what these two functions actually do, Only trying to help, not to patronize.

First of all the s3 (or standby) state suspends to RAM, so there is some power still being used by the system.  If you use this, however and lose power to the system, you cannot resume, and will lose any unsaved information.  As for the light, that's in the BIOS, and usually not adjustable.  Mine kindly flashes to tell me it's in s3, 

S4 suspends to disk and shuts off all power, so you resume where you left off, and power is not an issue.  So s4 is safer, but slower.  s3 is faster, and consumes power (albeit less than usual)

Getting s4 to work can depend on alot of things, like mobo / BIOS support and even hardware drivers (i.e. the ATI proprietary drivers had issues with suspend and hibernate until just recently)  So, first check your BIOS settings and see that s4 is enabled.  Also listing your hardware specs, as previously mentioned, would do well to help your cause.

---

### Post by jimmy the saint on 2008-04-24
I dont know what hardware you have, so I dont want to tell you this will work.  That said, this [http://ubuntuforums.org/showthread.php?t=614106]("http://ubuntuforums.org/showthread.php?t=614106") worked for a lot of people.

---

