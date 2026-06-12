---
title: "dual processor......... SMP etc...."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by cryo4.rm on 2007-07-07
trying to setup up ubuntu to recognise both CPUs of my dual processor..........

 installed the generic kernel which is supposedly SMP enabled and therefore compatible with my processor.... no?

 but when i run

   cat /proc/cpuinfo

i get
joe@stan:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2250  @ 1.73GHz
stepping        : 8
cpu MHz         : 798.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3461.80
clflush size    : 64



STill just the one processor.... anyone got any idea if im on the right track.. what to do etc... 

 Thnkyou....

---

### Post by 5-HT on 2007-07-07
> **cryo4.rm said:**
> 
 installed the generic kernel which is supposedly SMP enabled and therefore compatible with my processor.... no? 

Yup, -generic does support SMP...weird. Are you currently running the -generic kernel (can do a 'uname -r' to find out)

> **cryo4.rm said:**
>   but when i run...



If you're running the -generic kernel, this could *possibly* be due to some power management you have enabled (such as turning off a core when not needed, etc...).

If you take a look at '/sys/devices/system/cpu', are there directories for both cpu0 and cpu1?

---

### Post by cryo4.rm on 2007-07-07
running 

2.6.20-16-386 kernel

 i dont even know.... thats the generic right?

 as for power management 

directory '/sys/devices/system/cpu', only has entries cpu 0

---

### Post by 5-HT on 2007-07-07
> **cryo4.rm said:**
> running 

2.6.20-16-386 kernel

Seems like you're still running the 386 kernel, and not -generic. The 386 kernel does not have SMP support enabled.

Try doing a ```
sudo aptitude install linux-image-generic
```rebooting, and see if that takes care of it (if you've already installed the generic kernel, there should be an entry for 2.6.x-x-generic in your grub menu).

cheers,

---

### Post by cryo4.rm on 2007-07-07
thankkyou... 

 i just simply hadnt noticed the new option in the grub menu,,,,,,,,duh


 cheers

---

### Post by 5-HT on 2007-07-07
Glad you got it!:D

---

