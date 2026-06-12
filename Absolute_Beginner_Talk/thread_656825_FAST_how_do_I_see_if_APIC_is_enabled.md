---
title: "FAST: how do I see if APIC is enabled?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-03
thanks for the help

---

### Post by Ripfox on 2008-01-03
ACPI is enabled by default I believe, so if you didn't use a procedure to turn it off then it is most likely on. That is unless your computer is ancient, in which case it will say at boot up that it is disabled.

---

### Post by p_quarles on 2008-01-03
Open the terminal and type the following:
```
sudo cat /boot/grub/menu.lst | grep noapic
```
If this command returns with nothing, then apic is enabled.

---

