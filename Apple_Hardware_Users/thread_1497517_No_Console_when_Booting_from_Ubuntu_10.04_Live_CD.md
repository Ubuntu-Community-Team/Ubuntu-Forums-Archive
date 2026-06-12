---
title: "No Console when Booting from Ubuntu 10.04 Live CD"
date: 2010-05-30
forum: Apple Hardware Users
---

### Post by srojtas@me.com on 2010-05-30
I'm trying to boot up from my Live CD on my eMac and I'm able to hear the startup sound play.  However I can not access the console (control-option-f1) to change the xorg.conf file.  The screen just stays black.  I have the original eMac (NVIDIA graphics).  This CD does work on my G4 Cube, so it's not defective.  Any ideas?

---

### Post by linuxopjemac on 2010-05-30
maybe when you can choose the kernel, e.g. powerpc, you type a "1" behind it, so you stay in single user mode

---

### Post by srojtas@me.com on 2010-05-30
> **linuxopjemac said:**
> maybe when you can choose the kernel, e.g. powerpc, you type a "1" behind it, so you stay in single user mode

At what point would I type the 1?  During Yaboot or something else?

---

### Post by linuxopjemac on 2010-05-31
in yaboot you normally choose linux first. then if you press Tab you see the available kernels. Just choose one. Suppose that kernel is called "Linux", then you don't simply press ENTER here but
```
Linux 1
```

---

### Post by djurny on 2010-05-31
you can also try to boot without kms, by adding 'nomodeset' to the kernel commandline

---

### Post by sha.goyjo on 2010-05-31
I use radeon.modeset=0 for my ibook. I hear nomodeset works, but I haven't had great luck with it. I don't know if there is an equivalent specialized modeset boolean for the nvidia staging driver. Anyone else know for sure?

---

