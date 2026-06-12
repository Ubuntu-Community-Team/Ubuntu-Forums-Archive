---
title: "Which Kernel?"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by Nopposan on 2005-08-24
I'm on a Compaq Presario 705, mobile AMD Duron processor.  I'm currently running the 686 kernel, but I'm not sure whether it's the best choice.  Please tell me where I can find out which kernel is ideal for my machine.

---

### Post by jasmuz on 2005-08-24
the k7 processor line is optimal for AMD

---

### Post by Nopposan on 2005-08-25
O.K.  Thanks.

So, should I save all of my bookmarks and documents to my usb memory stick? Do I need to depackage the 686 Linux kernel before I install the k7?  Can I accomplish this through the Synaptic package manager?

---

### Post by jasmuz on 2005-08-26
Nothing of the above just do this:

Open a terminal, type sudo apt-get install linux-image-2.6.10-5-k7

Once its done it will install itself, and on next  boot select it, then remove the previous kernel

---

### Post by invalid on 2005-08-26
Better to do: sudo apt-get install linux-k7
This way you get all recomended packages included with the kernel.

Cheers,
Cb

---

### Post by Nopposan on 2005-08-27
Alrighty then.  Thank you jazmuz and invalid.  I followed your advice and it's as simple as that.  Easier than an oil change.

---

