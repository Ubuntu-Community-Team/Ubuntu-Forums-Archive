---
title: "[SOLVED] Backdating Kernel"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-13
I Saw on a post somewhere about intel sound and wireless (but thats irrelvant) a command to backdate your kernel one version in terminal. Ive used the command many times and ive looked in my history but like a fool i cleared it.

So if someone could please tell me the command to backdate the kernel to the previous version i would be very greatful and il try not to lose it this time.

Saj

---

### Post by saj0577 on 2008-04-13
Someone answered over IRC

```
sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

Saj

---

