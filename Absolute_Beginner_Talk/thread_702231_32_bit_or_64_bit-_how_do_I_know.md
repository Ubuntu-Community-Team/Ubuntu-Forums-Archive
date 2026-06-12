---
title: "32 bit or 64 bit- how do I know?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by FrancesL on 2008-02-20
Hello everyone. 
I have been reading through some of the tutorials etc.and see 32bit /64bit ..how do I know which I have? Sorry if this is dumb question, but, at over 60 and new to Linux..well, what more can I say! I am having a go!..thanks for all the help thus far (week 3 and still running! )

---

### Post by Kilz on 2008-02-20
> **FrancesL said:**
> Hello everyone. 
I have been reading through some of the tutorials etc.and see 32bit /64bit ..how do I know which I have? Sorry if this is dumb question, but, at over 60 and new to Linux..well, what more can I say! I am having a go!..thanks for all the help thus far (week 3 and still running! )

open a terminal and type in ```
uname -a
``` , if you see  x86_64 GNU/Linux at the end of the string it will show you have 64bit installed. If you have a 64bit computer and do not have the 64bit version installed you may want to install it before making a lot of changes. Since its a reinstall.

---

### Post by stunningman on 2008-02-20
its very simple if you are installing ubuntu just  first put 64 bit cd the system will automatically tell you that this cd can run on this machine or not.

---

### Post by FrancesL on 2008-02-20
> **Kilz said:**
> open a terminal and type in ```
uname -a
``` , if you see  x86_64 GNU/Linux at the end of the string it will show you have 64bit installed. If you have a 64bit computer and do not have the 64bit version installed you may want to install it before making a lot of changes. Since its a reinstall.

uname -a returned me: Linux ACER 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by FrancesL on 2008-02-20
> **stunningman said:**
> its very simple if you are installing ubuntu just  first put 64 bit cd the system will automatically tell you that this cd can run on this machine or not.
System came shipped on my notebook

---

### Post by Schalken on 2008-02-20
You therefore have the 32bit (i686) version installed.

---

### Post by emshains on 2008-02-20
> **FrancesL said:**
> uname -a returned me: Linux ACER 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux


The i686 means that you have a Pentium procesor and your system is 32bit so you dont need to reinstall to 64 bit version. 
Dont worry about the "fact" that  your system is just 32bit, rather than 64 bit, because i've used both and there is no BIG difference.

---

### Post by p_quarles on 2008-02-20
> **emshains said:**
> The i686 means that you have a Pentium procesor and your system is 32bit so you dont need to reinstall to 64 bit version. 
Dont worry about the "fact" that  your system is just 32bit, rather than 64 bit, because i've used both and there is no BIG difference.
Incorrect. It means that the system is running on a 32-bit kernel, but this doesn't indicate anything about the make or model of the processor itself. As for the difference between 32-bit and 64-bit, it can make a noticeable difference for many applications. For others, it will make no perceptible difference.

---

### Post by tangibleorange on 2008-02-20
> **FrancesL said:**
> Hello everyone. 
I have been reading through some of the tutorials etc.and see 32bit /64bit ..how do I know which I have? Sorry if this is dumb question, but, at over 60 and new to Linux..well, what more can I say! I am having a go!..thanks for all the help thus far (week 3 and still running! )

As for whether your machine is capable of running 64-bit, you can try the following command:

```
uname -m
```

i86_64 means you have a 64-bit capable processor.
Anything else means you don't (it's 32-bit). Simple as that!

---

### Post by Schalken on 2008-02-20
I recommend installing the 64bit version if you have a 64bit processor. (See tangibleorange's post above) The only problems you might experiance are:
> some third party packages might not be avaliable in 64bit, like Opera.
> the Sun Java Firefox plugin isnt avaliable in 64bit, AFAIK
Everything else seems to work fine, and ever so slightly faster :)

---

### Post by FrancesL on 2008-02-20
> **tangibleorange said:**
> As for whether your machine is capable of running 64-bit, you can try the following command:

```
uname -m
```returned me i686

---

### Post by tangibleorange on 2008-02-20
OK in that case you have a 32-bit processor, and we know from previous output that you are running the 32-bit version. Everything is as it should be!

---

### Post by p_quarles on 2008-02-20
> **FrancesL said:**
> returned me i686
tangibleorange was misinformed there. That command only tells you which kind of kernel you are currently running, and says nothing about the capabilities of the processor itself. If you want to know the CPU's capabilities, type:
```
cat /proc/cpuinfo
```
This will tell you what type of processor you have. You can either look this up yourself, or report the type here and someone will tell you.

---

### Post by FrancesL on 2008-02-20
> **p_quarles said:**
> tangibleorange was misinformed there. That command only tells you which kind of kernel you are currently running, and says nothing about the capabilities of the processor itself. If you want to know the CPU's capabilities, type:
```
cat /proc/cpuinfo
```
This will tell you what type of processor you have. You can either look this up yourself, or report the type here and someone will tell you.
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 22
model name      : Intel(R) Celeron(R) CPU          540  @ 1.86GHz
stepping        : 1
cpu MHz         : 1862.219
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3727.83
clflush size    : 64

---

### Post by p_quarles on 2008-02-20
The celeron is a 32-bit CPU.

---

### Post by portmanteau on 2008-02-22
The Celeron 540 is has Intel 64 tech.  Look at the flags listed in /proc/cpuinfo: lm means that the processor can do 64-bit instructions.

---

### Post by jrharvey on 2008-02-22
Intel claims that it is only 32 bit capable.

---

### Post by FrancesL on 2008-02-25
Thanks to all for taking the time to answer..I will stay with 32bit ! Still somewhat confused though. but thanks again

---

