---
title: "Very noobish XFCE quesiton.."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by BOBSONATOR on 2007-09-25
Hey guys, i just got XFCE, and there is a volume / icon on my desktop, and i cant delete it, how do i remove it? :P

Thanks !

---

### Post by Shazaam on 2007-09-25
What happens when you click it?

---

### Post by BOBSONATOR on 2007-09-25
it opens up / in thunar

---

### Post by Shazaam on 2007-09-25
Easy.
More than one partition? When you just had your Ubuntu desktop I bet there was a drive icon on it. Do you still need to access that drive without manually mounting it? If not you can add noauto to the fstab listing for that drive.

---

### Post by mysticmatrix on 2007-09-25
> **BOBSONATOR said:**
> Hey guys, i just got XFCE, and there is a volume / icon on my desktop, and i cant delete it, how do i remove it? :P

Thanks !

1) Do you simply want to not see the icons, or 2)do you don't want to read the partitions?

If latter is the case, you can follow the "noauto" option advised.

Also, I know how to do ( 1 ) in Gnome, but don't exactly know how XFCE handles things.

---

### Post by BOBSONATOR on 2007-09-25
Option one,

i know how to do it in gnome too, just not xfce

---

### Post by Shazaam on 2007-09-25
Try here...
[http://www.xfce.org/](http://www.xfce.org/)

---

### Post by kerry_s on 2007-09-25
[B]mousepad ~/.config/xfce4/desktop/xfdesktoprc

[file-icons]
show-filesystem=false
show-home=false
show-trash=false
show-removable=true[/B]

---

