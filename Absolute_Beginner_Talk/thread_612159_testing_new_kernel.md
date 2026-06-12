---
title: "testing new kernel"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-13
im making a custom kernel but i dont understand this step:


fakeroot make-kpkg --initrd --append-to-version=-*custom kernel_image kernel_headers *

the kernel is 2.6.23.1

what do i replace the italic text with?

thanks

---

### Post by mysticrider92 on 2007-11-13
That should be the name of the kernel you are making. I would just put 'custom' in the blanks, it will be added to the end of your kernel name in the .deb, uname results, and Grub menu.

---

### Post by skymera on 2007-11-13
can i have an example?

ive never done this before you see.

---

### Post by skymera on 2007-11-13
so does it go like this?

fakeroot make-kpkg --initrd --append-to-version=-scott

for example, i havent done anything as i need to know :@)

---

