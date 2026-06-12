---
title: "Sleep/Suspend/WakeUp problems with USB devices in hoary PPC"
date: 2005-03-13
forum: Apple PPC Users
---

### Post by Entity on 2005-03-13
When my powerbook G4 goes to sleep/suspend my USB devices don't work anymore on wake up.

Is that normal? What can I do?

Many thanks for your time and help.

---

### Post by val1984 on 2005-03-13
You can : 
sudo rmmod ehci-hcd
sudo modprobe ehci-hcd

---

