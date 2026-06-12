---
title: "How to install AMD Linux Drivers"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-11
Anyone installed any drivers that can help me? :confused:

---

### Post by MetalMusicAddict on 2006-09-11
Whats really your problem? Not enough info.

---

### Post by divague on 2006-09-11
what's the problem? why do you want AMD drivers?

---

### Post by WalmartSniperLX on 2006-09-11
> **divague said:**
> what's the problem? why do you want AMD drivers?

Well really Im a noob at this so heres the info: I dont have any problems really but I know AMD released new drivers so Im wondering If i should install them :rolleyes:

---

### Post by divague on 2006-09-11
I have a laptop with an AMD processor and in the 2 years i've been using ubuntu i've never needed drivers. I think you don't need them.

---

### Post by MetalMusicAddict on 2006-09-11
> **WalmartSniperLX said:**
> Well really Im a noob at this so heres the info: I dont have any problems really but I know **AMD released new drivers** so Im wondering If i should install them :rolleyes:

Drivers for what? And are they for linux? Im not sure you need anything. I have a new AM2 chip and the only specific thing I installed for it was the "K7" kernel.

---

### Post by WalmartSniperLX on 2006-09-11
> **MetalMusicAddict said:**
> Drivers for what? And are they for linux? Im not sure you need anything. I have a new AM2 chip and the only specific thing I installed for it was the "K7" kernel.

Version 1.39.xx of the driver can use either the 
PSB table or ACPI objects, dependent on whether
the kernel is configured to include ACPI support or
not. The driver version included is 1.39.04, for
the 2.6 kernel only. This driver supports SMP
frequency management and dual-core processors.  It
will not load on an SMP or dual-core system unless
the ACPI objects are available.  It will work on
all 2.6 kernels, but the 1.50.03 driver (below) 
is preferred for kernels 2.6.10 and later.

Version 1.60.xx of the driver can use either the
PSB table of the ACPI objects.  It supports Opteron,
Athlon 64 processors, in both single and dual core
versions, for all of the 754, 939, 940, and 1207
pin packages.  This driver supports SMP frequency
management but will not work on SMP or dual core
systems unless the ACPI powerstate objects are
available.  It will only work on 2.6.10 and later
kernels.  This driver is distributed with the
2.6.13 and later kernels.

The powernow-k8.c and powernow-k8.h files should be 
placed in the arch/i386/kernel/cpu/cpufreq directory. 
The kernel will then need to be rebuilt and the system
rebooted.  Builds of the 64-bit arch/x86_64 kernel use 
the same source files.

For further documentation, see the 
linux/Documentation/cpu-freq directory.

Support: [email]mark.langsdorf@amd.com[/email]
License: GPL

-AMD, inc

I guess I really dont need them. What is the K7 Kernel? What does it do?

---

### Post by Nrvnqsr on 2006-09-11
K7 kernel is the "engine" of Ubuntu and other Linux distros, that is designed for AMD Athlon processor family (eg: Athlon XP, Duron) Athlon 64 is a k8 processor but it can use the K7 kernel (which is 32-bit not 64-bit) without any problems

on the driver issue , I would say this, if it ain't broken, don't fix it....until the developer deem it necessary. so don't worry about it

---

### Post by MetalMusicAddict on 2006-09-11
Nrvnqsr beat me to it. ;)

> **WalmartSniperLX said:**
> I guess I really dont need them. What is the K7 Kernel? What does it do?

The K7 kernels are for 32-bit AMD Duron and Athlon chips. (correct me if Im wrong) K8 is for their 64-bit chips. I have one but I run 32-bit Ubuntu. It (K7) has SMP enabled and takes advantage of my dual-core chip.

---

### Post by WalmartSniperLX on 2006-09-11
Ok thanks for the info. I have a Sempron 64 running the 32-bit linux. Does anyone know what benifits ill get from the k7 kernel? :D

---

