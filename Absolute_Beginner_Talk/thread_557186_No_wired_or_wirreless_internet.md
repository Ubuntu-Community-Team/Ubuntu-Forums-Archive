---
title: "No wired or wirreless internet"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by ed44 on 2007-09-22
HI

I've recently installed Ubuntu on my Dell Inspiron 1501. The problem I have is that there is no internet - wired or wireless.

The wireless card is a Broadcom BCM 4310 UART.

In the network setting box the wired connection is set to DCHP.

I've been going through loads of posts and they all seem to require at least a wired internet connection to solve the problem.

Thanks

---

### Post by master_kernel on 2007-09-22
> **ed44 said:**
> HI

I've recently installed Ubuntu on my Dell Inspiron 1501. The problem I have is that there is no internet - wired or wireless.

The wireless card is a Broadcom BCM 4310 UART.

In the network setting box the wired connection is set to DCHP.

I've been going through loads of posts and they all seem to require at least a wired internet connection to solve the problem.

Thanks

This reminds me of a recently solved problem at my Master Kernel Thread.

Try this:
```
sudo modprobe bcm43xx
```
and add bcm43xx to your /etc/modules so it will boot every time.

master_kernel

---

