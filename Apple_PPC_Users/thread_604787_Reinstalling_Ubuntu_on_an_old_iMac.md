---
title: "Reinstalling Ubuntu on an old iMac"
date: 2007-11-06
forum: Apple PPC Users
---

### Post by Orientsee on 2007-11-06
Hi,

I have an old Powerpc iMac. I have no Mac disks. The machine has an old version of Ubuntu but I cannot find a grub menu to recovery mode and resetting username and password which I do not know. I have tried to install over but it keeps finding the old Ubuntu and insists on the username and password. What should I do? Ireally don't want to just trash a potentially useful box. Thanks for any advice.

---

### Post by frog_pilot on 2007-11-06
As PPC-ubuntu dosen't work as x86 ubuntu, you won't find any grub menu. the PPC bootloader is yaboot. On the second yaboot stage, where you can choose your current kernel, simply type```
Linux single
```to enter the recovery mode as root.

---

