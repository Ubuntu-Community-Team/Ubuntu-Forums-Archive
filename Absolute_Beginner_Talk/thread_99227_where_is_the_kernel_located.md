---
title: "where is the kernel located?"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by far on 2005-12-05
I'm trying to install a vpn client and apparently I need to know the location of the kernel to do so.
I'm on ubuntu 5. 04 , kernel vers : 2.6.10-5-386

Would anyone know that ?

thanx

---

### Post by az on 2005-12-05
If you mean the linux kernel source, you can just install the linux-headers package for your kernel and use that.  The use /usr/src/linux-headers-whatever as your source tree.

---

### Post by Jonne on 2005-12-05
/boot/vmlinuz-2.6.10-5-386
if I'm not mistaken.

---

