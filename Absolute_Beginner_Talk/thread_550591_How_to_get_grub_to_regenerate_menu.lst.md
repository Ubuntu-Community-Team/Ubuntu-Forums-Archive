---
title: "How to get grub to regenerate menu.lst"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-09-14
Anyone know how?

I tried purgin the install with remove --purge.

Then reinstalling it..
It does not regernerate the menu.lst and device.map.

---

### Post by simonn on 2007-09-14
Reinstall the kernel.

---

### Post by meierfra on 2007-09-15
```
sudo update-grub
```

---

