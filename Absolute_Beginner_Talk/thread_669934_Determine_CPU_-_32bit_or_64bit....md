---
title: "Determine CPU - 32bit or 64bit..."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by schu777 on 2008-01-16
Okay, I'm out of the loop for several years now on CPU speeds and such and mainly due to the fact that I don't upgrade computers like I used to.

Anyway, I'm looking at trying Ubuntu for the first time and would like to install the correct one for my CPU, but I don't know if the CPU is 64 bit or not.  My laptop is a EMachine M5405 - 

I'm currently running Fedora Core 7 and found this out - so hopefully this will point to the right direction.

Thanks, Michael

[michaels@localhost ~]$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 8
model name      : Mobile AMD Sempron(tm) Processor 2800+
stepping        : 2
cpu MHz         : 800.000
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up ts fid vid ttp
bogomips        : 1596.90
clflush size    : 64

---

### Post by c0met on 2008-01-16
Hi,

I pasted your model name into Google and found this site....

[http://www.allbusiness.com/electronics/computer-equipment-laptop-computers/5201507-1.html]("http://www.allbusiness.com/electronics/computer-equipment-laptop-computers/5201507-1.html")

From what I read there, it seems as though you have a 64 bit processor. If you try to install the 64 bit version of Ubuntu and you have a 32 bit processor, I'd imagine that Ubuntu will tell you that your installation version is incompatible.

---

### Post by Rotaj on 2008-01-16
Download and burn both the 32 and the 64 bit disc images. If the 32 bit live disc requires you to log on, then you probably have a 64 bot processor.

I have a Sempron 3400, and it requires the 64 bit version.

---

