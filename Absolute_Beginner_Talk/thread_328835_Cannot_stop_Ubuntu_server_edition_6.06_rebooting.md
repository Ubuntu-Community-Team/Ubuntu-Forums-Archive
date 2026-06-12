---
title: "Cannot stop Ubuntu server edition 6.06 rebooting"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by fixit1 on 2006-12-31
I have installed ubuntu server edition 6.06 on an old desktop with no problem.
However, when I try to start it constantly reboots.  I can access the GRUB options, but still get a boot command.  Any comments please?
AMD K6 375 MHz
132 Mbytes RAM
12 Gbytes HD

---

### Post by roseap on 2007-01-03
I ran into this problem too... found the answer here:

[http://www.ubuntuforums.org/showthread.php?t=300390]("http://www.ubuntuforums.org/showthread.php?t=300390")

In short, your processor is too old for the kernel that is installed by default on ubuntu server (as is mine)... the link contains instructions on installing a kernel that supports i386 and removing the kernel that doesn't work on your proc.

---

