---
title: "Bootloader deleted on mac during ubuntu reinstall"
date: 2011-03-17
forum: Apple Hardware Users
---

### Post by freeland on 2011-03-17
Hi
I have a Macbook Pro 7.1 with triple boot of OS X, Win 7 and Ubuntu 10.10, and rEFIt loader

Recently Ubuntu crashed

This was by partition structure before the crash
sda2 ~ 200MB
sda3 ~ 90GB (OS X)
sda4 ~ 1MB (boot)
sda5 ~ 50GB (ubuntu)
sda6 ~ 105GB (win 7)

During the ubuntu install, I combined the sda4 and sda5 partitions into one, and installed ubuntu 10.10 64-bit

Eversince, both Win7 and Ubuntu have stopped working. I guess the grub bootloader was sitting on sda4 and now its not there

Is it possible to recover Win 7 and Ubuntu without a full reinstall

Thanks

---

