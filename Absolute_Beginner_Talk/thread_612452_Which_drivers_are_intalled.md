---
title: "Which drivers are intalled?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-11-13
I am troubleshooting my webcam.
Is there a terminal command used to list the currently installed drivers ?
Thanks.

---

### Post by Daveski on 2007-11-14
From a terminal:

*lspci *to list PCI devices
*lsusb* to list USB device

Also you can run *modprobe -l* to list loaded modules.

---

### Post by philinux on 2007-11-14
Which webcam is it?

---

