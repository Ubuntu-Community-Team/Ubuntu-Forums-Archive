---
title: "Changing current kernel options ????"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by merobson25 on 2007-06-04
I'm new at this, so I apologize if the answer has been posted somewhere already.

I'm trying to get wireless running (who isn't), and figured that one of the things i would try is installing the newest MadWifFi drivers. When I look through the list of requirements on madwifi.org, I see that they recommend that the option CONFIG_MODVERSIONS be disabled. On my kernel, however(2.6-20-16-GENERIC) , the option is enabled. Is there a way to disable that option without compiling a custom kernel? 

Thanks in advance

---

### Post by dstew on 2007-06-04
You can add this to the kernel line in your /boot/grub/menu.lst file:```
--disable-modver=yes
```

---

### Post by merobson25 on 2007-06-04
Thanks! They also say to set CONFIG_CRYPTO_AES enabled, but mine is currently set to (I believe) manual (the line in the file says CONFIG_CRYPTO_AES=m, so I'm presuming that's what that means). You wouldn't happen to be able to tell me how to enable AES automatically????

Thanks again.

---

