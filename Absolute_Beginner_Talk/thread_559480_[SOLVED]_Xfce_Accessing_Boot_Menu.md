---
title: "[SOLVED] Xfce Accessing Boot Menu"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by rtr86 on 2007-09-25
Hi all,

I am using Xfce and need to add to the 'kernel modules to load at boot time'. I knew how to this with Gnome:

```
sudo gedit /etc/modules
```

But not Xfce :)

Any help appricated :)

---

### Post by Seisen on 2007-09-25
In XFCE you can use mouspad, vim, or nano and just use one of those instead of gedit in that command.

---

### Post by overdrank on 2007-09-25
> **rtr86 said:**
> Hi all,

I am using Xfce and need to add to the 'kernel modules to load at boot time'. I knew how to this with Gnome:

```
sudo gedit /etc/modules
```

But not Xfce :)

Any help appricated :)

Hi in xfce you need to replace gedit with mousepad and use gksudo
```
gksuo mousepad /etc/modules
```
Good luck!

Edit to slow

---

### Post by rtr86 on 2007-09-25
Awesome, thanks guys!

---

