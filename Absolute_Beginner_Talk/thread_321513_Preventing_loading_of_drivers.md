---
title: "Preventing loading of drivers?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by hearty on 2006-12-19
Hello,
  My wireless card drivers are giving some problem which are loaded automatically during the bootup. Because of which kernel is getting panic.
  I want to prevent that drivers to load automatically. Does the kernel bootup process has a method which will ask me which driver to load and which to not.



Another Question is.
when i boot the kernel with option init=/bin/sh

My root partition is mounted in ro , preventing me to edit any file of the fs. So how to mount the fs in RW mode?

---

### Post by Ecthelion on 2006-12-19
> Another Question is.
when i boot the kernel with option init=/bin/sh

My root partition is mounted in ro , preventing me to edit any file of the fs. So how to mount the fs in RW mode?

You mean you want a normal user to be able to write on the root fs?
Why would you want that?
Just change your user to root and then you can write anywhere.

---

