---
title: "Dual Core, Just realized"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-09
Is ubuntu making use of both my processors???  If not how can i make it or how can i figure out if it is using both...

---

### Post by joysofpi on 2006-09-09
install either the linux-686-smp (for intel) or linux-k7-smp (for amd) package, depending on which one you have. That should give you a kernel with dual core support on the next reboot

to check, run gnome-system-monitor. You should see 2 cpu's under the resources tab

---

### Post by Cynical on 2006-09-09
It should be using them both by default if you have an smp enabled kernel. To check, go to System > Administration > System Monitor

---

### Post by Devile on 2006-09-09
how do i check it in system monitor....

---

### Post by masnevets on 2006-09-09
Look at the resources tab, and under CPU history, there should be 2 CPUs. If not, you need to boot using an SMP enabled kernel (either linux-686-smp or linux-k7-smp)

---

