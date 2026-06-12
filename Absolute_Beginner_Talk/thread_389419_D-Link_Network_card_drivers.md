---
title: "D-Link Network card drivers"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-03-20
i have a D-Link dfe-530tx network card that isn't being detected by ubuntu. it is working properly because it gets detected in windows and fedora core 6. I looked up the drivers and found one but it's not working good, i get errors when i "make" the file in terminal.
any ideas?
thanks

---

### Post by Kobalt on 2007-03-21
I think you need to install gcc-3.4 in order to make that driver. Install it through Synaptic and type in command line in order to set your compiler to gcc-3.4 temporarily 
```
export CC=gcc-3.4
```

And also don't forget to have build-essentials and linux-headers-$(uname -r) installed.

---

