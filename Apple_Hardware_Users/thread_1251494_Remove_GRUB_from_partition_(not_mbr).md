---
title: "Remove GRUB from partition (not mbr)"
date: 2009-08-27
forum: Apple Hardware Users
---

### Post by ercoppa on 2009-08-27
Hi, I have two GRUB installed (some tests :P) on my disk:
- /dev/sda3
- /dev/sda4

Grub was installed in this way (e.g. /dev/sda3):
```

root (hd0,2)
setup (hd0,2)

```
So, GRUB is not installed in disk's MBR.

I want only one GRUB (Refit now shows me two tux), how can I uninstall the second GRUB from /dev/sda4?

Greets, ercoppa

---

