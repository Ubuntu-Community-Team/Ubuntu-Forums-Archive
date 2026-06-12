---
title: "Intel iMac"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by earlejones on 2007-01-25
Which version of Ubuntu is best for my Intel iMac?
Thanks,  earle
*

---

### Post by Zzl1xndd on 2007-01-25
it would be the normal X86 versions. No different then any other machine.

---

### Post by zgornel on 2007-01-25
Ubuntu 6.10 i386 . ;)

---

### Post by jonny on 2007-01-25
A warning: it's difficult to dual boot Ubuntu and OSX on an Intel Mac.  The problem is that Ubuntu's installer insists in using Grub as a bootloader, but Grub doesn't understand the partitioning scheme used by OSX.  I tried fiddling about with patched versions of Grub and finally gave up and did an ugly hack to get LILO working instead.

Now I've finally installed it, Ubuntu works like a charm on my Mac Mini - but do some googling before you start.

---

