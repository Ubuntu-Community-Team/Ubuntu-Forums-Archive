---
title: "/etc/network/interfaces and hardware"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by dupa on 2006-10-26
I have a question.

If I have in the /etc/network/interfaces the following config:

```
iface eth1 inet static
        address 192.168.1.248
        netmask 255.255.255.0
        gateway 192.168.1.254
```

Where is written the "mapping" between the "eth1" interface and a specific Ethernet Adapter?

Thanks

---

### Post by displague on 2006-10-26
That would be /etc/modprobe.d/custom (or anyother file in that folder - but custom won't be conflict with any files in the package).

alias eth0      e1000

e1000 is the kernel module for the Intel Gigabit Ethernet adapter.  Aside from that, the normal system magic is probably already detecting your ethernet adapter and loading the appropriate module.

---

### Post by dupa on 2006-10-27
thank you very much!

---

