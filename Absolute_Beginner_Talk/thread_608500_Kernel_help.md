---
title: "Kernel help"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by vistovistor on 2007-11-10
I am patching a driver, and to do that I need to apply the patch to the source, once I have put the patch and all the files in the source directory and typed make modules, can I just take the patched file I am after and place it in /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko or do I have to make modules_install and risk stuffing up my other stuff

Thanks in advance

---

### Post by jpkotta on 2007-11-10
It should be ok to just copy, as long as that is where the .ko would have gone.

---

