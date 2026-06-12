---
title: "Which kernal"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by egoo on 2006-03-17
Im instaling Ubuntu and on installing the base system, a popup asking which kernal to install has come up with the options


lunix-386
linux-image 386
linux-image-2.6.12-3-386

which one should i choose

---

### Post by arctic on 2006-03-17
The last one.

---

### Post by egoo on 2006-03-17
Thanks

---

### Post by Sutekh on 2006-03-18
The first package **linux-386** installs the i386 kernel and restricted modules.  

It always depends on the latest version of the kernel image package **linux-image-386**.  

This in turn depends on the latest kernel image itself **linux-image-2.6.12-3-386**



Install linux-386 when you want the latest kernel and restricted modules (good/easy for updating)

Install linux-image-386 when you want the latest kernel but not the restricted modules.

Install linux-image-2.6.12-3-386 when you want the linux kernel 2.6.12-3-386.

---

