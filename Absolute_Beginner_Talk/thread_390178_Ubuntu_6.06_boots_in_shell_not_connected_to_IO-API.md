---
title: "Ubuntu 6.06 boots in shell? not connected to IO-APIC"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by nevaziah on 2007-03-21
my Ubuntu boots in the shell!!

after loading the first screen where it counts down from five, where i can press escape, it shows this error

......because not connected to IO-APIC

what does that mean?
I will restart to reproduce the FULL error. that's as much as I got because boot is too fast to read.

---

### Post by martinw89 on 2007-03-22
It sounds like a problem with APIC and an older kernel.  Try this, in the GRUB screen (the first screen where it counts down from 5) press Escape.  Then, press "e" to edit the boot options.  Highlight the part that starts with "kernel" and add the words "noapic nolapic" to the end of that line.  Press enter, than press "b".

Tell us if that works; if it does you can change the Grub configuration so that it will do this every time.  Additionally, if you finally get into your installation a system upgrade should fix the problem because newer linux kernels do not have this problem.

Hope that helps!

---

