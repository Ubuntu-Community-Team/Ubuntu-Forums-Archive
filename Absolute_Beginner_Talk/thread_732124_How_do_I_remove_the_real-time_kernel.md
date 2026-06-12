---
title: "How do I remove the real-time kernel?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-03-22
While trying to follow various posts for getting my video card driver working, some place along the line one of those ended up with me having the real-time kernel installed.  The entries are there in /boot/grub, and also in the grub menu.  I know how to clean up the grub menu, but I need to know how to actually delete the real-time kernel itself.  Part of my video driver compilation is failing with a message about driver not compiled with same version of compiler as the kernel.  I am hoping removing the real-time kernel will help.

Any help is greatly appreciated!  :)

---

### Post by girishv on 2008-03-23
Hi,

Each kernel will have its own modules libraries, usually at
/lib/modules/`uname -r` and  they should not change the behaviour of other kernels unless
you some how overwrote the library folder name.

Removing of the kernel depends on the way you installed it. If you had used apt, you can simply remove it by 
sudo apt-get remove linux-image-version

Else, simple deleting of vmlinuz, initrd and /lib/modules/kernel_version and /usr/headers/kernel_version should do the job for you.

Do not forget to edit the grub entry accordingly (if you are manually deleting the files)

Girish

---

