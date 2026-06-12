---
title: "NeoGrub Help?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by 2Dum2Kno on 2008-01-07
```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries

title Ubuntu
find --set-root /boot/vmlinuz-2.6.17-10-generic
kernel /boot/vmlinuz-2.6.17-10-generic ro root=/dev/sda5
initrd /boot/initrd.img-2.6.17-10-generic
```

i think im doing somthing wrong in NeoGrub Linux
can anyone help

---

### Post by wheels. on 2008-01-09
are you dual booting with vista and are you trying to use the vista bootloader using easybcd to configure it??
if so just add entry and pick your partition from easy bcd you don't need to configure it manually.

---

