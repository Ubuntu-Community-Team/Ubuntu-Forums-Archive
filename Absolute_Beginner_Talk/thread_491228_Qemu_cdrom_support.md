---
title: "Qemu cdrom support"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-07-03
I installed Qemu and made a virtual installation of Win98SE. How do I enable cdrom support where I can install more programs into Win98SE using the cdrom on my computer? I also created a laucher on the desktop to start Qemu and Win98SE. Do I edit the laucher command to enable support?

HERE IS THE LAUCHER COMMAND:

```
 qemu -m 64 /home/rob/win98se/win98se.img
```

---

### Post by jrib on 2007-07-04
adding ```
-cdrom /dev/cdrom
``` should work

---

