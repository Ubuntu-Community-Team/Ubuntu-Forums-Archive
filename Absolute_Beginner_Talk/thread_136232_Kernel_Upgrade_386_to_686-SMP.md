---
title: "Kernel Upgrade: 386 to 686-SMP"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Billy Snorkeldick on 2006-02-25
I decided to upgrade to the 686-SMP kernel (from the default 386) after finding out that it will take advantage of Intel's Hyper-Threading technology, increasing Ubuntu's processing speed. So a visit to the Synaptic Base System repository got me to sucessfully download and install it. Here's my question: do I now need to remove the originating 386 kernel/image?

---

### Post by John.Michael.Kane on 2006-02-25
No you dont. the grub will boot from the 686kern automatic, however if you want to remove go into synaptic, and choose all the i386 kern stuff for removal. also install all the 686smp headers as well.

---

### Post by Billy Snorkeldick on 2006-02-25
Thank you much, man.

---

### Post by colo on 2006-02-25
If you want to know what exact kernel you're running at the moment, fire up a terminal of some sort, and start
```
uname -a
```

This will generate output in some way similar to this:
> Linux sam 2.6.15-gentoo-r1 #4 PREEMPT Sat Feb 25 14:38:55 CET 2006 i686 AMD Athlon(tm) 64 Processor 3000+ AuthenticAMD GNU/Linux

---

