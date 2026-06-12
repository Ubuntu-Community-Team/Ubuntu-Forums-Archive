---
title: "Ioncube issues"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by hvc123 on 2008-08-21
hi all,

im having issues with IONCUBE this is the output on /var/log/apache2/error.log

Failed loading ioncube_loader_lin_5.1.so: ioncube_loader_lin_5.1.so: R_PPC_REL24 relocation at 0x0d9d6318 for symbol `malloc' out of range.

this is the PPC version.
i have tried to load all versions and they all error. 

is it possible to get the source code

---

### Post by darmstrong on 2008-09-22
Hi I have this identical same issue with the ionCube ppc loader failing to load with memory allocation issues on IBM p5 POWER5+ with RedHat Enterprise Linux 5.1

Failed loading /usr/.../ioncube/ioncube_loader_lin_5.1.so: /usr/.../ioncube/ioncube_loader_lin_5.1.so: R_PPC_REL24 relocation at 0x043f2318 for symbol `malloc' out of range

Did you find a resolution?

---

