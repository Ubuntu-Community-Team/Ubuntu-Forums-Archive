---
title: "feisty kernel on ubuntu gutsy"
date: 2007-12-05
forum: Apple PPC Users
---

### Post by karstengerber on 2007-12-05
Hi,
since i upgraded my powerbook to ubuntu gutsy, suspend to ram does not work anymore. in the lanchpad-bugtracker i read that installing the old feisty kernel would fix the problem, so i installed the kernel package from the feisty repository. however - the system does not even boot with this kernel - more precisely with the initial ramdisk that is builded during the install process of that package. when i use the kernel + ramdisk from the feisty desktop-cd  suspend to ram works, but the system does not sitch off power when shutting down. can anybody tell me how to build a correct ramdisk?

Regards, Karsten

---

### Post by stmiller on 2007-12-06
Can you still boot with an alternate older kernel? There is a kernel compile how-to in the PowerPCFAQ (link below). It is best to just try and get a good stable Gutsy kernel install (from apt-get). Then you can have that as a backup. Then try to install the Feisty kernel again.

---

### Post by karstengerber on 2007-12-07
i have several kernels (+ramdisks) installed on the system: the kernel/ramdisk that comes with the gutsy default installation, and the set that i copied from the feisty-desktop cd. both boot, but have some issues that are not working. then there are two more kernels and ramdisks installed: one from the feisty repository and one i build following the kernel-compile-howto. these two do not boot.
rgds, karsten

---

