---
title: "Asus 1225B-SU17 w/ AMD E-450"
date: 2012-06-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by 4thelove on 2012-06-05
Hello,
I have been able to successfully install 12.04 LTS. However, every second time or so, my touchpad and keyboard are frozen upon start up. I get to lightdm and my touchpad or keyboard do not respond. I have tried automatic login, but still the same problem.

---

### Post by dankoi on 2012-10-21
> **4thelove said:**
> Hello,
I have been able to successfully install 12.04 LTS. However, every second time or so, my touchpad and keyboard are frozen upon start up. I get to lightdm and my touchpad or keyboard do not respond. I have tried automatic login, but still the same problem.

I had the same problem, and the solution was to edit /etc/default/grub, updating the GRUB_CMDLINE_LINUX_DEFAULT line to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux"
 and then run update-grub.

The bug report:[U]
[/U][https://bugs.launchpad.net/ubuntu/+bug/1014240](https://bugs.launchpad.net/ubuntu/+bug/1014240)

---

