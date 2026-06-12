---
title: "how much ram does ubuntu support?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by alexlex on 2007-05-05
my motherboard will max at 4g's of ram. windows xp will only support 3.

what does ubuntu support?

---

### Post by oilchangeguy on 2007-05-05
found this by doing a google search:
[http://ubuntuforums.org/showthread.php?t=430457](http://ubuntuforums.org/showthread.php?t=430457)
not sure if this will help.

---

### Post by mustang on 2007-05-05
> 
Windows XP Professional and Windows Server 2003 Memory Support. The maximum amount of memory that can be supported on Windows XP Professional and Windows Server 2003 is also 4 GB. However, Windows Server 2003, Enterprise Edition supports 32 GB of physical RAM and Windows Server 2003, Datacenter Edition supports 64 GB of physical RAM using the PAE feature.


[http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx](http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx)

An operating system can only support as much memory as the hardware can. A 32-bit system has an address space of 0-(2^32 - 1) so it can only support upto ~4 gigabytes of memory. This constraint applies to any operating system running on 32-bit hardware---linux, windows, or mac.

To answer your question, it depends on what type of hardware you have. If you have a 32-bit system, then ~4 gigabytes. If you have a 64-bit system, you can use more ram than you can afford.

---

