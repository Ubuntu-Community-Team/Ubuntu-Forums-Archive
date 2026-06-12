---
title: "Changeing hardware?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Mr T 87 on 2008-03-29
I may be required to change pretty much the entire hardware configuration that I currently have Ubuntu installed upon. I was hoping that I could just swap the hard-drive but am unsure how Ubuntu will deal with the different hardware. If ubuntu supports the new hardware then will it automaticlly make the changes or will I have to do a complete re-install.

Thanks in advance =)

---

### Post by wolfen69 on 2008-03-29
if your hardware is supported, you should have no problems. ubuntu does very well with new hardware, regardless of how much you change.

---

### Post by Mr T 87 on 2008-03-30
Thanks for clearing that up

---

### Post by mcduck on 2008-03-30
The only thing that I'd expect to possibly cause problems is display card, if you move from nVidia to Ati or other way round you should probably get rid of restricted graphics drivers before moving the installation to new machine.

If both old and new machine have graphics card from the same manufacturer there shouldn't be any problems.

---

### Post by teaker1s on 2008-03-30
if you want to change processor makes, it would pay to have the correct kernel installed  prior to moving your drive, if you running 386 kernel no problems-amd or intel

---

### Post by mcduck on 2008-03-30
> **teaker1s said:**
> if you want to change processor makes, it would pay to have the correct kernel installed  prior to moving your drive, if you running 386 kernel no problems-amd or intel

This is irrelevant unless running very old Ubuntu version.

Ubuntu's generic kernel supports all modern CPU's, and there is no more separate kernels for 686, k7 or SMP setups. The CPU(s) are detected at boot time and correct features and optimizations are automatically used for your CPU.

---

### Post by teaker1s on 2008-03-30
Dapper  Ubuntu 6.06 LTS - Supported to 2009 and on download page, which there is a choice of kernels.

---

### Post by mcduck on 2008-03-30
> **teaker1s said:**
> Dapper  Ubuntu 6.06 LTS - Supported to 2009 and on download page, which there is a choice of kernels.

Dapper was the last version that needed separate kernels for different CPUs. But 3 Ubuntu versions have been released after Dapper, and fourth coming very soon, so most users are already running more up-to-date Ubuntu version than Dapper. So I wouldn't confuse anybody with kernel versions unless I'd know that they are actually running Dapper..

---

