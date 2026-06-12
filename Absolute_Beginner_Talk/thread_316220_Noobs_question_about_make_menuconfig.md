---
title: "Noobs question about make menuconfig"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-10
Hi,

I compiled the latest Linux kernel and installed it successfully. I've seen I can still access the "options" with **make menuconfig** in the terminal. Does it mean I can change the "kernel settings" with this command without having to recompile the kernel????

Thanks

---

### Post by lonce on 2006-12-10
I dont know for certain, but my understanding is that you have to recompile the kernel to change it.  I might and very well could be completely wrong though.

---

### Post by kilou on 2006-12-10
I also think the kernel should be recompiled to account for changes in make menuconfig but is there any way to know this for sure?

---

### Post by az on 2006-12-10
> **kilou said:**
>  Does it mean I can change the "kernel settings" with this command without having to recompile the kernel????


No.

To be more specific, the installed kernel is found in /boot.  The initrd is also there -  the initrd is the ramdisk that gets loaded up and which can load a few modules fofore the kernel can actually use the filesystem on the disk.  Then, udev gets run and it loads up modules that it thinks you need.

So, changing the setting in your kernel source do not affect any of the above.

---

### Post by kilou on 2006-12-10
OK thanks. So I'll need to recompile if I want to change settings. Would have been too easy otherwise ;)

---

