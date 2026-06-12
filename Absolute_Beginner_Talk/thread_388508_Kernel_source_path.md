---
title: "Kernel source path"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2007-03-19
Hi

I'm building a driver for my Atheros wireless card on Edgy. The make file wants a variable called KERNELPATH which is "the location of the kernel build tree" which I assume means the root of the kernel source code. The default, /usr/src/Linux-2.6.3, is empty. Since I haven't compiled the kernel, I assume I need to download the source. Where can I download the source (I've searched kernel.org in vain) and how do I find exactly which kernel build my system is using (2.6.15 or something later)? 

Thanks!

---

### Post by Bachstelze on 2007-03-19
```
sudo apt-get install linux-headers-$(uname -r)
```

If you're stilll prompted for the path, try /lib/modules/$(uname -r)/build

To find your current running kernel version, type *uname -r* in a terminal.

---

