---
title: "Grub.."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Jademalo on 2007-12-30
Is it possible, and if so, how, to stop making grub auto boot linux and jut hang on the selection screen?

Also, is it then possible to just uninstall grub, and use the bios built in OS switcher?

I dont wanna have to format or get rid of ubuntu.

Thanks :)

---

### Post by taurus on 2007-12-30
Edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and replace 

```
timeout     5
```
with 

```
prompt
```

---

### Post by Jademalo on 2007-12-30
ty! :D

---

