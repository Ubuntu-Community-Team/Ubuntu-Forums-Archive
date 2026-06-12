---
title: "DTV help/silly question"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by NCAANFI on 2007-07-10
Err simply put what do I have to do to "compile a kernel"?
I'm stuck on the first set of instructions on the generic section
[http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29#Generic_Installation](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29#Generic_Installation)

---

### Post by Skrynesaver on 2007-07-10
If you have installed the kernel source package you open a terminal and cd to the /usr/src/linux directory then
make menuconfig (you can make xconfig, but I think the curses interface is clearer)
Once you have selected what is to be compiled in and what is to be built as modules you then make dep && make clean && make bzImage then
make modules && make modules install.

Now copy your new kernel to the root directory and edit /boot/grub/menu.lst to give you the option of booting it.

---

