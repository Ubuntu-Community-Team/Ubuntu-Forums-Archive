---
title: "Where can i see the kernel config?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by schmolch on 2007-04-22
Hi, i just installed Ubuntu today and so far i like it very much.

Sorry for not searching more thoroughly, but can anyone tell me where i can see the kernel-configuration?

I would especially like to know if this kernel uses suspend2 for suspend-to-disk and if yes which version and settings.

---

### Post by aidanr on 2007-04-22
/boot/config-2.6.whatever or /usr/src/linux/.config

---

### Post by Bachstelze on 2007-04-22
```
less /boot/config-$(uname -r)
```

---

### Post by schmolch on 2007-04-22
thx alot!

---

