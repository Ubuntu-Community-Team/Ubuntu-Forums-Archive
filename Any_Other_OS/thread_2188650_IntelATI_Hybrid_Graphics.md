---
title: "Intel/ATI Hybrid Graphics"
date: 2013-11-18
forum: Any Other OS
---

### Post by sancrya0 on 2013-11-18
Hi there,

In Ubuntu 13.10 Intel/AMD hybrid graphics are fully supported. This allowed me to finally delete my Windows partition (for gaming) and switch to Linux :)

The question is, does ArchLinux and other Linux Distro's also support hybrid graphics like Ubuntu does? I can't seem to find an answer anywhere.

---

### Post by wtheron on 2013-11-22
In general -  yes, but you will not know unless you install. And if it is not entirely supported, there will be a way to get it sorted. 

It also depends on the age of your card.  If your card is very recent (or you have integrated graphics with the latest chipset), there may be some levels of annoyance involved.  Worst case, you will have to be content with the vesa driver or some other software that best matches your card until you figure out how to fix it.  Thus, everything will work, just not the way you want it to.  For example, it may not default to the resolution you want when you start up.  But this really is one of the worst cases.  You can generally work around this by installing backports, and/or some reading and experimenting.

I ran into some problems with Haswell Intel HD 4400 in June 2013.  Nearly lost hope since the hardware was very recent with little support on the stable distributions.  Even so, there was a work-around to get it fully operational and just the other day, I reinstalled the same (updated) distro without any issues.

---

### Post by rousseau09 on 2013-11-25
Ubuntu is pretty good in terms of hardware support and driver release. Like wtheron mentioned, you get the new drivers in few weeks as someone somewhere managed to make it work with a patch. I personally don't use Ubuntu that much as I am not comfortable with Unity yet, I use Debian based Kali Linux. It was a nightmare to make AMD Graphics card work on them, specially when you try to upgrade to a newer kernel. I was so annoyed that once I made it work, I wrote a complete guide and put it in my website. Not sure if anyone here uses Kali Linux, but link is [here]("www.blackmoreops.com/?p=1"). Then again, I don't use it for gaming, I use my graphics card for crunching data using CAL++ and Pyrit. Ubuntu unfortunately is not supported to my causes and my OCD with Unity making it more harder by day to use it. I tried Lubuntu, then again, same issue, many things I want to use is not supported.

---

