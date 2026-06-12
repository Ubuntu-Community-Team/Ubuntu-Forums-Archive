---
title: "i686 Kernal?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-04
Hi, Guys!

Is there any REAL reason to download the i686 Kernal and associated files?
I have an Acer TravelMate 4101 WNLCi which has a Pentium M730 processor.

Regards.
Roger :grin:

---

### Post by MrHorus on 2006-09-04
> **ramjet_1953 said:**
> 
Is there any REAL reason to download the i686 Kernal and associated files?


Yes.

The 386 kernel is a generic kernel that will work on any x86 processor but will not take advantage of any features of a 486 or higher CPU so if you have anything vaguely recent you will want one of the more advanced kernels like 686 or 686-k7 or a 64bit kernel if you have an 64bit CPU.

In other words, performance gains.

---

### Post by tommcd on 2006-09-04
See this thread:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
Everything you would want to know. I switched to the k7 kernel (I have an athlon64 CPU). To be honest I don't see any difference in performance. The 686 and k7 kernels cn use more than 1GB of RAM. This is one reason to switch. Hope this helps.

---

### Post by meborc on 2006-09-04
YES... you will have better CPU performance from 686 kern"e"l since it is optimized for processors pentium and up 8)

EDIT: damn, you guys are fast =D>

---

### Post by ramjet_1953 on 2006-09-04
Thanks for the info?
One thing that I read in the thread that you supplied wasn't quite clear to me.
As my laptop has a Pentium M730, running at 1.6GHz, can I use the smp kernal to enable multi-threading?

Regards,
Roger :grin:

---

### Post by tommcd on 2006-09-04
See the post by stubby (at the bottom of the first page of the link I posted) along with the reply by kvidell on the second page. He says the 686 kernel works great for pentium Ms.

---

### Post by az on 2006-09-04
Be sure to install the linux-686 package and not just the linux-image-686 package.  The former also installs the restricted modules you may need.

---

### Post by tageiru on 2006-09-04
> **meborc said:**
> YES... you will have better CPU performance from 686 kern"e"l since it is optimized for processors pentium and up 8)

EDIT: damn, you guys are fast =D>

It seems that the gains are minor, future ubuntu versions might drop the i686 and k7 kernels in favor of the generic i386 kernel.

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

---

