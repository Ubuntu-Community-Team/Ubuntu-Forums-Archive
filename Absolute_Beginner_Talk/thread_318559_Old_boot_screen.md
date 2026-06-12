---
title: "Old boot screen"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Mr Green on 2006-12-14
I kind of miss the old way Ubuntu booted and shut down where it would go through a lot of stuff and check each one with [OK] or [FAIL]

Anyway to get it back?

---

### Post by taurus on 2006-12-14
Edit /boot/grub/menu.lst and remove the "quiet splash" at the end of the entry for kernel...

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by mcduck on 2006-12-14
..or just remove the 'quiet' and leave the 'splash' to get best of both worlds.. ;)

---

