---
title: "XP doesn't appear in grub?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-11-04
I have installed XP and then installed Gutsy via the menu. Unfortunately, XP does not appear in the start up grub menu but it is alive and kicking but unusable on it's own partition. How do I get it into the start up menu so that I can have a choice of systems?

---

### Post by argie on 2007-11-04
Do you know which partition XP is installed to? If it's on the first partition, you must add this to your /boot/grub/menu.lst at the end:
```

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

If you'll run:
```
gksudo gedit /boot/grub/menu.lst
```
you should be able to copy and paste that entry. Remember you'll have to change the (h0,0) part to whatever is relevant. For example, if xp is on the second partition that would be (hd0,1)

---

