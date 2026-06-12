---
title: "Which kernel should I use?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by the_tiger on 2006-05-02
I have an AMD64 processor. Should I use the 386, 686 or k7 kernel?

---

### Post by hw-tph on 2006-05-02
If you use 32bit Ubuntu you should use the k7 (Athlon series) kernel.


Håkan

---

### Post by the_tiger on 2006-05-02
If I install this kernel how do I choose which I start with? Is the only way to edit grubs menu?

---

### Post by muep on 2006-05-02
New kernels are automatically added to the GRUB menu.

Don't uninstall old kernels before you know your system boots with the new one. When the GRUB menu starts to get too long, uninstall some of the older kernels.

---

### Post by the_tiger on 2006-05-02
Ok I installed the k7 kernel but now glxgears runs really slowly? Everything else seems to be fine.

---

### Post by fallencan on 2006-05-05
after installing new kernel u need to reconfigure your vga driver for new kernel. at least that is the way i do for my comp

---

### Post by Sutekh on 2006-05-05
If you installed proprietry video drivers (NVIDIA/ATI) by installing the ones from the Ubuntu repositories (nvidia-glx, flgrx), then you need to install the restricted modules package for your new kernel,
```
sudo apt-get install linux-restricted-modules-k7
```

If you installed the proprietry drivers from the manufacturer's web site, then you will need to run the video driver installer again so that it can create a driver module for the new kernel.

This should be done for every change in kernel architecture (ie 383 -> k7)

---

### Post by az on 2006-05-05
[QUOTE=the_tiger]Ok I installed the k7 kernel but now glxgears runs really slowly? Everything else seems to be fine.[/QUOTE]

install the linux-k7 package.  That not only brings in the linux-image packages but the linux-restricted-modules, which is what you probably need to run your ATI card the way you want to.

---

### Post by filiep on 2006-05-30
If you use the K7 (32bit) kernel on a AMD64, will CPU frequency scaling work ?

---

### Post by Sutekh on 2006-05-30
[quote=filiep]If you use the K7 (32bit) kernel on a AMD64, will CPU frequency scaling work ?[/quote]
Its not a problem for me (K7 kernel with AMDX2 3800) so it should be fine for you.

---

