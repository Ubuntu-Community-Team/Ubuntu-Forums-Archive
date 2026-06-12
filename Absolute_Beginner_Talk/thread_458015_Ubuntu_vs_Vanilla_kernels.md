---
title: "Ubuntu vs Vanilla kernels"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-29
Hi,

I know that Ubuntu kernels are basically Vanilla kernels with some additional tweaks and drivers. But what is the exact difference between these (for the same version number)?? Is the Ubuntu kernel different just in the additional menu (Ubuntu additional drivers) in the configuration utility?? This is important for me because I always need to compile my own kernels in order to have some specific functions like undervolting patch etc. So I need to choose between Vanilla kernels or Ubuntu kernels...

I don't need restricted drivers and anyway it is possible to use them even when using a Vanilla kernel so what does Ubuntu kernels really brings? My system is not fancy:

i915 GPU
centrino 1.86Ghz Sonoma
ipw2200 wireless card
SD card reader (doesn't work anyway because mine is unsupported in Linux)

I think that a Vanilla kernel makes everything work OK so I'm unsure what a ubuntu kernel can bring. The only point is that I use VirtualBox and the Ubuntu kernel (in the Ubuntu additional drivers menu) has support for VirtualBox VMMon module.... Is this important when using virtualbox (this module is not loaded on startup apparently) or is it possible to use it as well in a Vanilla kernel??

Thanks

---

### Post by ikonia on 2007-05-29
the ubuntu kernels don't contain any restriced or additional drivers, they are just basiclly the stock kernels packaged up to fit into the ubuntu OS framework.

---

### Post by kilou on 2007-05-29
> **ikonia said:**
> the ubuntu kernels don't contain any restriced or additional drivers, they are just basiclly the stock kernels packaged up to fit into the ubuntu OS framework.

there is an additional menu in the configuration of Ubuntu kernels which is called Ubuntu additional drivers. This menu is not available in Vanilla kernels.

---

### Post by kilou on 2007-05-31
up

---

