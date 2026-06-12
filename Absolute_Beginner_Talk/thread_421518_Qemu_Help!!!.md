---
title: "Qemu Help!!!"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by esc0587 on 2007-04-24
Why do I keep getting this error when I use qemu with kqemu.  Or what does it mean?
Qemu loads with the  other operating system, but just wondering why this happens.

student@student-desktop:~/Desktop$ qemu -boot d -cdrom /dev/cdrom -hda dsl.img
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

---

### Post by dschaller on 2007-04-24
kqemu is an accelerator module that works with qemu. Apparently you don't have the accelerator compiled and configured for qemu to use it. The accelerator doesn't work on all target operating systems anyway (at least that's how it used to be).

If you feel you are getting acceptable performance from qemu without the accelerator, there's really no need to worry about this warning or bother with the kqemu module.

---

