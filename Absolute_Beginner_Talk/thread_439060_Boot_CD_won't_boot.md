---
title: "Boot CD won't boot"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-10
After the splash screen, I get the following series of error messages and the installation hangs completely:

[17179570.82400]  PCI: JMB36x Enabling dual function on 0000.02.00.0
[17179570.82400]  Cannot allocate resource region 0 of device 0000.02.00.0
[17179570.82400]  Cannot allocate resource region 1 of device 0000.02.00.0
[17179570.82400]  Cannot allocate resource region 2 of device 0000.02.00.0
[17179570.82400]  Cannot allocate resource region 3 of device 0000.02.00.0
[17179570.82400]  Error while updating region 0000.02.00.0/0 (0000b000 ! = 00000000)
[17179570.82400]  Error while updating region 0000.02.00.0/2 (0000b000 ! = 00000000)

What does it mean? Thanks for help.

---

### Post by Najand on 2007-05-10
It is a bug with edgy:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63516](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63516)
Use Feisty instead.

---

### Post by ginestre on 2007-05-10
Thanks. The most amazing thing about Ubuntu is not the software (which is excellent, by the way), but the support. It is, frankly, world class. Hang on -it??? No- YOU are frankly world class!

---

