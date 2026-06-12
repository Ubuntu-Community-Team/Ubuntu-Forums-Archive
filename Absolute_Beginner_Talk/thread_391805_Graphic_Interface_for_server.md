---
title: "Graphic Interface for server"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-23
Is there any graphic interface for 6.06.1? I don't see one when I boot

---

### Post by ardchoille42 on 2007-03-23
> **Peter1234123 said:**
> Is there any graphic interface for 6.06.1? I don't see one when I boot

There aren't gui's on a server. You can, however, install a graphical environment if you want.

```

sudo apt-get install ubuntu-desktop

```

That will get you the default Ubuntu desktop environment (gnome) or you can install something else.

---

### Post by kerry_s on 2007-03-23
You can add one, just pick something light weight.
Example:
apt-get install xorg fluxbox
startx
or
apt-get install xorg icewm


Just something light will do, theres no need to install a whole desktop if you don't need it.
Desktops:
kubuntu-desktop<- heavest
ubuntu-desktop<- heavy 
xubuntu-desktop<- lighter than the rest, but still alot of apps.

---

