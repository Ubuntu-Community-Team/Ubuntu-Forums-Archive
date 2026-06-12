---
title: "password recovery and boot probs"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-19
I need to do some editing in the OS options that appear at the bootloader.
It asks for apassword which i have forgotten
I can only boot into the recovery mode of ubuntu.
please help

---

### Post by Oldsoldier2003 on 2008-04-19
> **sameer.india said:**
> I need to do some editing in the OS options that appear at the bootloader.
It asks for apassword which i have forgotten
I can only boot into the recovery mode of ubuntu.
please help

if you can boot into recovery mode do so the edit /boot/grub/menu.lst from there.

```
cp /boot/grub/menu.lst /boot/gru/menu.lst.old
nano /boot/grub/menu.lst
```

If you break the system further you'll have to go in with a live cd and restore the menu.lst.

Alternatively you might consider using a  [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/").

---

