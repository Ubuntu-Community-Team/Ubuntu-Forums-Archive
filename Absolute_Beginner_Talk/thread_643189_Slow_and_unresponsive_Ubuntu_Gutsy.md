---
title: "Slow and unresponsive Ubuntu Gutsy"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by johann_p on 2007-12-17
My 32bit Ubuntu Gutsy installation seems to behave quite slow and unresponsive recently. I have a Intel  Dual Core Duo witj 2.4 GHz and 4GB Ram, so starting a terminal should not take a second or sometimes several seconds to show me the prompt. 

Biggest problem is running Java apps -- they sometimes seem to crawl to a halt, though heapspace is barely used (as in jconsole shown).

I have checked ps and there are no processes that use significant amounts of CPU. I have disabled both beagle and tracker. And still ...

This could somehow be related to upgrading to Gutsy or upgrading my memory from 2 to 4 GB - both happened around the same time and it seems I see those slowdowns since then.

The memory I installed are exactly the same model and make with exactly the same timings as the first 2 GB (I have 4 x 1 GB of identical blocks, but I bought the first 2 GB when memory was still more expensive).

So any ideas what could be going on?

---

### Post by cmnorton on 2007-12-17
When you upgraded, did you let the installation overwrite system config files? I have found two upgrades went very well, when I saved certain system configuration files, like /etc/hosts, /etc/services, and so on, and let the installation write its new files.

I only have empirical evidence that doing this works, having performed a Gutsy upgrade that resulted in my having to reinstall Gutsy from scratch and two Gutsy upgrades on a desktop and laptop, where I let the installation overwrite the system files (after saving them off to a safe place before the installation).

---

### Post by johann_p on 2007-12-17
> **cmnorton said:**
> When you upgraded, did you let the installation overwrite system config files? I have found two upgrades went very well, when I saved certain system configuration files, like /etc/hosts, /etc/services, and so on, and let the installation write its new files.

I only have empirical evidence that doing this works, having performed a Gutsy upgrade that resulted in my having to reinstall Gutsy from scratch and two Gutsy upgrades on a desktop and laptop, where I let the installation overwrite the system files (after saving them off to a safe place before the installation).

There must have been dozens of questions about whether i want to overwrite a configuration file or not and I did my best to make sense of naked diff output (talk about user friendlyness!) to make that decision. On the other hand I cannot imagine why this would change the responsiveness of my system -- whether or not I did let them be overwritten or not.


Some java apps are much much slower now but all the monitor tools show low CPU and (relatively, compared with the RAM I have) low memory usage.

---

### Post by cmnorton on 2007-12-18
It's a stretch. I only know on my laptop, that when I let all the sys files update, my laptop ran fine. Obviously, there could be other reasons. I gave you my answer based on seeing your post that things were running sluggishly.

---

### Post by johann_p on 2007-12-18
Thank you for your help ... I am just trying to figure out what might be going on before I decide what to do. 

My biggest problem is that I am not 100% sure if that slowdown is even related to the Gutsy upgrade or the memory upgrade. Could it be that upgrading the RAM from 2GB to 4GB *slows down* a computer? Or one running 32 bit Gutsy?

:confused:

---

### Post by learning curve on 2007-12-18
troubleshoot by removing the ram and see what happens.  you may have gotten a bad module.

---

