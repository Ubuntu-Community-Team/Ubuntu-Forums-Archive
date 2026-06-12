---
title: "Shut down problem!"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-20
I keep getting a weird error every time I try to shut down. I end up having to hold down my power button...

The error reads

> [17183840.##0000] unregister_netdevice: waiting for vmnet1 to become free. Usage count = 1

(the ##s change as the error repeats every 3 seconds)

How do I fix this? It's very annoying!

---

### Post by taurus on 2007-01-20
Got VMware running on your machine?

---

### Post by kbsuperstar on 2007-01-20
Yes, but I've uninstalled all my virtual machines. Should I just remove VMware all together?

---

### Post by taurus on 2007-01-20
Yes.  Remove it if you don't need it anymore.

---

### Post by kbsuperstar on 2007-01-20
K, thanks!

---

### Post by kbsuperstar on 2007-01-20
I have VMware server and i can't figure out how to remove it :( I tried removing all the vmware stuff in synaptic, but it didn't get rid of everything

---

### Post by gammal on 2007-01-24
Run VMware's uninstallation script:
```
sudo /usr/bin/vmware-uninstall.pl
```

---

### Post by schleppel on 2007-01-25
How do i solve this problem without removing vmware?

---

### Post by tansu on 2007-02-16
> **schleppel said:**
> How do i solve this problem without removing vmware?
I want to know that too, I need vmware..

---

