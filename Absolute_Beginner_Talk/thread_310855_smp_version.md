---
title: "smp version"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by dileepk on 2006-12-01
i loaded ubuntu 6.06 desktop on core duo laptop.  looks like it sees only 1 cpu.  is there an easy way to make it smp?

---

### Post by jdong on 2006-12-01
Install the linux-686 package via apt-get or synaptic to activate your other core :)

(just a note to anyone else reading this... starting from Edgy on, SMP is automatically active in the default kernels)

---

### Post by dileepk on 2006-12-03
I installed linux-686 package but when i run "top" it does not show 2 CPUs.  is there another way to verify that both cpus are active?

---

### Post by 5-HT on 2006-12-03
> **dileepk said:**
> I installed linux-686 package but when i run "top" it does not show 2 CPUs.  is there another way to verify that both cpus are active?
Did you press '1' to toggle top's SMP view?
Alternatively, **cat /proc/cpuinfo **should list both cores.

Hope that helps.

---

### Post by jdong on 2006-12-03
> **dileepk said:**
> I installed linux-686 package but when i run "top" it does not show 2 CPUs.  is there another way to verify that both cpus are active?

Top doesn't show anything different by default for two CPU's. Try using cat /proc/cpuinfo

---

