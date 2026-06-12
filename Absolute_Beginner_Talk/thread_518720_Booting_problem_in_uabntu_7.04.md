---
title: "Booting problem in uabntu 7.04"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by ramu.prabakaran on 2007-08-06
I have installed the ubantu7.04 successfully. where as, whenever I starting the system, it requires the ubantu Cd for booting. How can configure, such a way that, it has to boot from hard disk.

---

### Post by wjp.reg on 2007-08-06
when you installed, did you confirm that grub could be written to the MBR?  If not, ubuntu expects a disk to boot the system.

You  can fix this by doing the following:

open a terminal window
```
sudo grub-install ´(hd0,0)´
```

NOTE: assuming you only have one drive and you only have ubuntu installed, otherwise ´hd0,0´ would need to change to ´hd0,1´ for partition 2 on the first drive, and so on..

---

