---
title: "Making windows default Boot, Linux second choice"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by ozziejohn on 2006-03-26
Have just installed Ubuntu on a second partitioned drive with windows xp on the other.
When I boot up the dual boot window shows Ubuntu at the top of the list and windows last. How can I change the sequence so that Windows is at the top.


Many Thanks

---

### Post by taurus on 2006-03-26
You need to edit /boot/grub/menu.lst and change the default value (near the top) from 0 to 1...
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by codejunkie on 2006-03-26
[QUOTE=taurus]You need to edit /boot/grub/menu.lst and change the default value (near the top) from 0 to 1...
```

sudo gedit /boot/grub/menu.lst

```[/QUOTE]
wouldn't that just make it boot into recovery mode by default instead of windows.

---

### Post by taurus on 2006-03-26
[QUOTE=codejunkie]wouldn't that just make it boot into recovery mode by default instead of windows.[/QUOTE]
Or just replace whatever number Windows is in!!!

---

