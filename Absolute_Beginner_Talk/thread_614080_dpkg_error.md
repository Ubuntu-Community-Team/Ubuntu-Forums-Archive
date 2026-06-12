---
title: "dpkg error"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-15
```

scott@scott-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.23.1-scott-custom
Cannot find /lib/modules/2.6.23.1-scott-custom
update-initramfs: failed for /boot/initrd.img-2.6.23.1-scott-custom
dpkg: subprocess post-installation script returned error exit status 1
scott@scott-desktop:~$ 

```

what does this eror mean?

---

### Post by dajhorn on 2007-11-15
This error means that your custom kernel is broken or incomplete.

You should use the "kernel-package" program to compile and install a custom kernel on an Ubuntu computer instead of doing a "make install" from the source tree.

---

### Post by skymera on 2007-11-15
but how do i fix this?

i removed the .debs as it didnt work right

---

### Post by skymera on 2007-11-15
anyone?

---

