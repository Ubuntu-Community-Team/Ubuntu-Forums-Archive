---
title: "Swap disk vs. Ram"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Darkula on 2007-02-27
How can I get the swapdisk (which doesn't seem to do much) to take some load off my RAM??

thanks

---

### Post by Richard Kut on 2007-02-27
Hello Darkula! If you have enough RAM, then the swap file will barely be touched. Linux manages memory differently than other operating systems, so it is quite normal to see that all of your memory has been allocated. Don't worry; most likely three quarters of the memory is allocated to caching. Since the Linux caching algorithms are very efficient there is no need to intervene. Unless, of course, you are having some problems. Are you?

---

### Post by compmodder26 on 2007-02-27
Why would you want it to?  Swap is much, much slower than RAM.   But if you insist, edit the number in the file /proc/sys/vm/swappiness.  The higher the number, the more the system will swap.

---

### Post by Darkula on 2007-02-27
Thanks for your reply RK,
this is the story:
I'm running kubuntu on a old IBM 866mhz w/ 512mb RAM which is max for this old but good machine.
I have phpsysinfo running and except for just after a reboot the sys memory shows mostly in the red 92-99%, is this normal then?

---

### Post by rsambuca on 2007-02-27
I agree with the last couple of posters.  If your machine is not using the swap that is a good thing!

---

### Post by compmodder26 on 2007-02-27
In a terminal type "free -m".  This will display how much memory is free on your computer (in megabytes).  Noticed the second line it produces.  This tells you how much you have free without buffers/cache.  That is the true amount of memory you have available.

Even if you are truly using up all your memory, making swap do more work isn't necessarily going to speed things up.

---

### Post by Darkula on 2007-02-27
would the x- graphics be the reason for the high physical memory use?

---

### Post by Darkula on 2007-02-27
tried the free -m command and am using 488 out of 502 RAM, OUCH!

so the phpsysinfo is showing correct.

---

### Post by rsambuca on 2007-02-27
If you click on the performance tab in your System Monitor, it will list all of the running processes along with CPU usage, memory usage, etc.

---

### Post by compmodder26 on 2007-02-27
> **Darkula said:**
> tried the free -m command and am using 488 out of 502 RAM, OUCH!

so the phpsysinfo is showing correct.

Is the 488 showing on the first or second line?

---

### Post by Darkula on 2007-02-27
> **compmodder26 said:**
> Is the 488 showing on the first or second line?


It's on the first line. Mem:

---

### Post by rsambuca on 2007-02-27
The first line is not the line you want to read.  What is on the next line (which excludes buffers and cache)?

---

### Post by Darkula on 2007-02-27
-/+  144 (used)   358(free)

Swap:  1466       16     1450

---

### Post by compmodder26 on 2007-02-27
> **Darkula said:**
> -/+  144 (used)   358(free)

Swap:  1466       16     1450

You have 358 megs available to you.  You don't need to do anything at all.  Your system is fine.

---

### Post by rsambuca on 2007-02-27
So you are really only using 144MB of your RAM.  Things are great.

Edit:  compmodder is *FAST!!!*

---

### Post by chavo on 2007-02-27
Yep. like everyone says Linux knows how to handle your ram and swap. Don't even worry about it.

---

### Post by Darkula on 2007-02-27
Thanks you guys!!!

All that 99% and red lines had me spooked.

Again thanks for clearing things up for me!!

---

