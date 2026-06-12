---
title: "swap memory not working"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by tjk on 2006-12-06
I've been using Kubuntu now for nearly a month.  I have system monitor applets in the panel, but the swap memory has **never** registered any use.  I run VMware often, which uses all my physical memory (I only have 512 & 256 banks), but swap memory has never been used.  Could it be that the swap memory isn't working?

---

### Post by tbroderick on 2006-12-06
Try taking a look at the output of, free -m, from a terminal.

---

### Post by tjk on 2006-12-06
> **tbroderick said:**
> Try taking a look at the output of, free -m, from a terminal.

This is what I get:
----------------------------------------------------------------------------------------
             total       used       free     shared    buffers     cached
Mem:           757        749          7          0         83        303
-/+ buffers/cache:        362        394
Swap:         1576         17       1558
-----------------------------------------------------------------------------------------
And the swap amount used doesn't change - even when I run VMware

---

### Post by mcduck on 2006-12-06
Your swap is working just fine, it's just that you have enough memory so there's no need to swap a lot.

From the 'free' output you can see that your apps are now using 362MB of memory and there's even room for keeping 394MB of disk cache in RAM (the line with '-/+ buffers/cache').

---

### Post by tjk on 2006-12-06
> **mcduck said:**
> Your swap is working just fine, it's just that you have enough memory so there's no need to swap a lot.

From the 'free' output you can see that your apps are now using 362MB of memory and there's even room for keeping 394MB of disk cache in RAM (the line with '-/+ buffers/cache').
Wow - that's hard to believe that I only use 362MB when I have about 4+ programs running in Linux and then a couple more under Win98 in VMware.  Maybe I can allocate more to VMware so that it runs faster/smoother...   Thanks.

---

### Post by az on 2006-12-06
> **tjk said:**
> Wow - that's hard to believe that I only use 362MB when I have about 4+ programs running in Linux and then a couple more under Win98 in VMware.  Maybe I can allocate more to VMware so that it runs faster/smoother...   Thanks.

I think the system requirements for windows 98 is a minimum of 16 megs of ram.

---

