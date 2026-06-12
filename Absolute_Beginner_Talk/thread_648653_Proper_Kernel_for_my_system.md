---
title: "Proper Kernel for my system?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Shawn Reist on 2007-12-23
Hello, 

I am relatively new to Linux and have completely removed Windows from my system and I am looking to make sure I can get Ubuntu running properly and fast, my system is older.

I have Supermicro P4DC6+ motherboard and case, two 1.5 GHz Zeon Processors with 512 Megs of ram... planning to install more ram at a later time.

Installed Gusty from Live CD 7.10 with an NVIDIA FX 5500 video card.

NVIDIA Drivers installed on system.

I have the Generic Linux kernel... will this recognize my two processors or do I have to install the server kernel or this SMP kernel?

---

### Post by ChaosParser on 2007-12-23
System>Administration>System Monitor. 

Do you see two processors? 

If yes... well.  Yes. :)

---

### Post by Rocket2DMn on 2007-12-23
Both processors in System Monitor should show different data graphs to be functioning properly.  Please post the output of
```
cat /proc/cpuinfo
uname -a
```
I'm not sure if it's required to have the 64 bit version installed, I'll check.

---

### Post by Shawn Reist on 2007-12-25
Hello,

Thanks for the info, I think it is using both CPU's

this is what is shows

-----------------------------------------------------
shawn@Icabaud:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 0
model name      : Intel(R) Genuine CPU 1800MHz
stepping        : 10
cpu MHz         : 1586.159
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 3175.66
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 0
model name      : Intel(R) Genuine CPU 1800MHz
stepping        : 10
cpu MHz         : 1586.159
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 3172.33
clflush size    : 64

shawn@Icabaud:~$ uname -a
Linux Icabaud 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
-----------------------------------------------------

Thanks

---

