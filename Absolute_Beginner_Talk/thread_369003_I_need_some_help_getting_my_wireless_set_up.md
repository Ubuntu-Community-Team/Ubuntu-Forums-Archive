---
title: "I need some help getting my wireless set up"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Mardok45 on 2007-02-24
Just to point out, I'm an absolute beginner to Unix OS's.

I installed Ubuntu on my laptop, and can't get the wireless card to work.  I know it's a Broadcom device, but not sure what model.

When I run:
lspci | grep Broadcom\ Corporation
I get:
Network controller: Broadcom Corporation Unkown device 4311 (rev 01)

So I'm guessing the model is a BCM4311.

I also saw somewhere to try and install the latest version of the wl_apsta.o file and get the Wireless-2.6 Kernel.  I got the file wl_apsta.o file, but I don't know where to get the kernel.  I also don't know how to install wl_apsta.o.

Can anyone help me out here?

---

### Post by ddom87 on 2007-02-24
i hope [this ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")helps you . Its for BCM43xx cards in dapper

---

