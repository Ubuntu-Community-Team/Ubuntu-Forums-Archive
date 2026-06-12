---
title: "[SOLVED] gusty gibbon 7.1 won't recognise  both cores pentium d"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by jpdamigaman on 2008-03-09
HI linux only recognise 1 core !

only 1 core shows up in system monitor!

also typed in cat /proc/cpuinfo 

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 2
cpu MHz         : 2999.940
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx cid cx16 xtpr lahf_lm
bogomips        : 6003.61
clflush size    : 64

jpdamigaman

---

### Post by igknighted on 2008-03-09
> **jpdamigaman said:**
> HI linux only recognise 1 core !

only 1 core shows up in system monitor!

also typed in cat /proc/cpuinfo 

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 2
cpu MHz         : 2999.940
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx cid cx16 xtpr lahf_lm
bogomips        : 6003.61
clflush size    : 64

jpdamigaman

What does the command "uname -r" yield?

---

### Post by p_quarles on 2008-03-09
I remember having a similar problem with the Gnome system monitor a while back. The Pentium D chip is fully supported by the default 7.10 kernel, so it's most likely working fine. To verify, I'm going to recommend installing another (better, imo) system monitor. To install via the terminal:
```
sudo apt-get install htop
```
Or search for "htop" in Synaptic. 

This monitor runs in the terminal, so open one up and simply type:
```
htop
```
The numbers on the top left of htop are your CPUs. If it lists both 1 and 2, your system is running as it should.

---

### Post by jpdamigaman on 2008-03-09
ran uname -r  thats what I got!

 2.6.22-14-386

---

### Post by igknighted on 2008-03-09
> **jpdamigaman said:**
> 2.6.22-14-386

You have changed kernels from the default (2.6.22-14-generic).  You should still have generic on your system and could boot to it via the grub menu (accessible at boot time).  Was there any particular reason to switch to the i386 kernel?  It is meant for really old (ie, original pentium) systems and therefor has no support for things like multiprocessor functions.

---

### Post by jpdamigaman on 2008-03-09
Hi Thanks to all who contributed to this post

How do I mark this problem solved?

---

### Post by p_quarles on 2008-03-09
> **jpdamigaman said:**
> Hi Thanks to all who contributed to this post

How do I mark this problem solved?
Glad you got it working. To mark the thread solved, use the "Thread Tools" menu at the top of the page, and select the appropriate option.

---

