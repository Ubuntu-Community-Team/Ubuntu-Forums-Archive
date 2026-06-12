---
title: "help with recognizing second processor"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by roboducky28 on 2008-01-20
When I go to the system monitor, these are my laptop's specs:

Ubuntu
Release 7.10 (Gutsy)
Kernel Linux 2.6.22-14-386
GNOME 2.20.1

Hardware
Memory: 1002.2 MB
Processor: Genuine Intel(R) CPU   T2250 @ 1.73 GHz


I'm trying to get my laptop to recognize the second processor (it's a Centrino Duo)...is there a fix without having to reinstall the system?  Also, when I type in "uname -a" i get:

Linux journey 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux

The i686 worries me...can someone explain?  I was sure it was supposed to be i386, but when it comes to this sort of thing, I'm pretty much a newbie...

Thanks ;)

---

### Post by gn2 on 2008-01-20
There isn't a second processor. Just one processor with two cores.

---

### Post by swp6499 on 2008-01-20
what does "cat /proc/cpuinfo" show in terminal you may have to "sudo cat/proc/cpuinfo | less" to see it all???

---

### Post by steveneddy on 2008-01-20
Go to Synaptic and install the kernel that has -generic at the end.

If you don't find -generic, then look for -smp.

One of these for 32 bit will recognize your second processor.

Don't forget to reboot.

Linux 2.6.22-14**-generic**

---

### Post by roboducky28 on 2008-01-27
> **swp6499 said:**
> what does "cat /proc/cpuinfo" show in terminal you may have to "sudo cat/proc/cpuinfo | less" to see it all???

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2250  @ 1.73GHz
stepping        : 8
cpu MHz         : 800.000
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
bogomips        : 3462.80
clflush size    : 64

---

### Post by roboducky28 on 2008-01-27
> **steveneddy said:**
> Go to Synaptic and install the kernel that has -generic at the end.

If you don't find -generic, then look for -smp.

One of these for 32 bit will recognize your second processor.

Don't forget to reboot.

Linux 2.6.22-14**-generic**

...according to Synaptic, I already have this version installed....but then why doesn't it show up when I look at the system monitor? is it not being used, or I'm not booting with the generic kernel?

---

### Post by mortsahl on 2008-01-27
Actually, you should be using an i686 kernel on your machine (if you can find one ... I haven't looked).

i686 --> Pentium II and above. 

With that kernel it will take advantage of the enhanced instruction set made to the CPU since the i386 days.

---

### Post by mcduck on 2008-01-27
> **roboducky28 said:**
> ...according to Synaptic, I already have this version installed....but then why doesn't it show up when I look at the system monitor? is it not being used, or I'm not booting with the generic kernel?
If you have many different kernels installed  you have to select the right kernel from the Grub menu (during the boot). It seems that you are now running the 386 kernel instead of the default generic kernel. The 386 kernel doesn't have SMP support, generic does.

You are not going to need that kernel so you could just remove it with Synaptic,a s long as you make sure you have the "linux-generic" package installed (having this package makes sure you'll always have latest version of generic kernel, header files and other kernel-related stuff).

---

### Post by skymera on 2008-01-27
gutsy by defualt uses the i686 i believe.

and you dont have 2 processors, its mearly 2 cores in a single proc.

---

### Post by mcduck on 2008-01-27
> **mortsahl said:**
> Actually, you should be using an i686 kernel on your machine (if you can find one ... I haven't looked).

i686 --> Pentium II and above. 

With that kernel it will take advantage of the enhanced instruction set made to the CPU since the i386 days.

THere is no CPU-specific kernels in Ubuntu, hasn't been since Dapper. For desktop there are 2 different kernels, 386-kernel which is actually optimized for 586 or something and doesn't support multi-CPU/core setups, and the Generic kernel that detects your CPU at boot time and then uses correct optimizations, and also supports SMP setups.

386 kernel is only useful for very old machines, for everything else use the generic kernel.

(yes, I know there are packages for other kernels in repositories. They are just empty meta packages and actually install the generic kernel.)

---

### Post by LazKapitaL on 2008-01-27
Hello i have a problem opposite. I have 1 processor and it shows 2 processor on it. And &#305;t use CPU as hell !!! at least %80-%90 of both? processor. In fact there is one processor.

My processor is 3.2 Ghz Pentium 4

I m downloading Ubuntu desktop cd image right now. In system monitor shows 2 processor and they use %90+ of processor capacity. Its abnormal usage for the programs i curently use. I have 1Gb ram. Please someone tell me how to make it as 1 processor as it should be.

---

### Post by mcduck on 2008-01-28
> **LazKapitaL said:**
> Hello i have a problem opposite. I have 1 processor and it shows 2 processor on it. And &#305;t use CPU as hell !!! at least %80-%90 of both? processor. In fact there is one processor.

My processor is 3.2 Ghz Pentium 4

I m downloading Ubuntu desktop cd image right now. In system monitor shows 2 processor and they use %90+ of processor capacity. Its abnormal usage for the programs i curently use. I have 1Gb ram. Please someone tell me how to make it as 1 processor as it should be.

Many P4 models have a feature called Hyperthreading, which makes the CPU show to computer as 2 CPU's. While not as good as actually having 2 real CPUs/Cores, it still gives some benefits when running many programs at the same time. So, there's nothing wrong in that sense.

Most likely your high CPU usage is caused by something else. Open a terminal and run 'top' to see what process is using all the CPU time.

---

