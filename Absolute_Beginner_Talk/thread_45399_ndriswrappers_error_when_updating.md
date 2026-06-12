---
title: "ndriswrappers error when updating"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by czambran on 2005-06-29
When I was trying to update the linux-image-2.6.10-5-385, I got the following error:
E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

can somebody tell me why?


Thanks
Christian

---

### Post by czambran on 2005-06-30
*bump*

---

### Post by ssck on 2005-06-30
[QUOTE=czambran]When I was trying to update the linux-image-2.6.10-5-385, I got the following error:
E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

can somebody tell me why?


Thanks
Christian[/QUOTE]

i faced the same problem.i had to uninstall ndiswrapper and then run the update.once that is done, i install the ndiswrapper again.that will fix the problem.i don't know how to go around this problem.can someone help ?

---

### Post by czambran on 2005-06-30
Yap, it worked!.

---

