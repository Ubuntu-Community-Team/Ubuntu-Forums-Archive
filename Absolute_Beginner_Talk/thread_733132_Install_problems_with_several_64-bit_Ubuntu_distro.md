---
title: "Install problems with several 64-bit Ubuntu distro"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by zaurus on 2008-03-23
Hi

I tryed to install several 64-bit Ubuntu distro and always had the error message: (initramfs) [107.592663] usb 1-2: device not accepting address 2, error -62.
What does it mean?
The only distro installed wo problem was 6.06 LTS.

I have Asrock motherboard K-8 Combo-Z, Athlon 64 CPU.

KR

N.B.
I have not tryed 32-bit distro, want a 64-bit one.

---

### Post by kwacka on 2008-03-28
There was a discussion about this on usb development forum (NOT an Ubuntu forum) some time ago when kernel 2.6.22 was being developed, and the feeling was (IIRC) that it was due to the order in which USB & USB-2 drivers were loaded. 

An error message is thrown up, but everything works OK.

---

