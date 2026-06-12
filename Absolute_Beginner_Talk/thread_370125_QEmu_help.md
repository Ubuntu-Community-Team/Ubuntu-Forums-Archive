---
title: "QEmu help"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Zilulil on 2007-02-25
Hi i'm running Feisty and trying to setup QEmu using [WindowsXPUnderQEmu]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo?highlight=%28qemu%29") and I've run into some problems.
I can't figure out what he means by install **linux-source-*version***

```
cd /usr/src/linux
make-kpkg debian
make-kpkg modules_image
module-assistant prepare kqemu 
dpkg -i /usr/src/kqemu-modules-''version''.dpkg
```
and the last line in that code is confusing me too.

---

### Post by Zilulil on 2007-02-25
Ok so i got past that problem but now i've run into another.
```
qemu -localtime -cdrom /dev/cdrom -m 384 -boot d windows.img
```
i get a qemu:could not open hard disk image '/dev/cdrom'

---

