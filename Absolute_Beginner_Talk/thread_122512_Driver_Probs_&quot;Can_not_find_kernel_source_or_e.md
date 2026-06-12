---
title: "Driver Probs &quot;Can not find kernel source or even headers.&quot;"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Inkyskin on 2006-01-27
I am getting this error while trying to install the driver for my Logitech Messenger Cam:

Can not find kernel source or even headers.

This seems to be causing probs, can anyone explain what I need to do to solve this?

---

### Post by chilly_willy2 on 2006-01-27
Make sure you're kernel source and/or kernel headers are installed.  Look under /usr/src to find those.  Also, the output of ```
uname -r
``` will give you the kernel version you're using.  Make sure the kernel source (src)/headers match that version.

Open Synaptic (or whatever you use to install new packages/software) and search for the kernel source and/or headers and install those.

When compiling new drivers (modules), they need to use the kernel headers to compile against the kernel.  Hope this helps...

---

### Post by Inkyskin on 2006-01-27
Sorted, thanks :) Now I can see my ugly mug on my monitor at last :D

---

### Post by az on 2006-01-27
You also need to get gcc-3.4 for kernel modules.  gcc-4.0 is what everything except the kernel was built with and what gets installed with build-essential.  You need to install gcc-3.4 additionaly.

---

