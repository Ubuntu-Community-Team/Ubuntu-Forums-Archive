---
title: "How can I edit the dual boot menu?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by spencewah on 2007-05-09
Hey everyone,

I accidentally installed two instances of Feisty (it's a bit of a long story, I was editing xorg.conf on my first installation and really messed it up so I decided just to reinstall).  Anyway, now on the boot menu there's the "good" copy of Ubuntu and the messed up version.  How can I remove the messed up version as an option?

Thanks!
-S

---

### Post by alienexplorers on 2007-05-09
Go into terminal and type:

> sudo gedit /boot/grub/menu.lst

Remove or prefix all lines for this messed up build with #.

Save menu.lst

This should get rid of the problem

---

### Post by RedSquirrel on 2007-05-09
> **spencewah said:**
> Hey everyone,

I accidentally installed two instances of Feisty (it's a bit of a long story, I was editing xorg.conf on my first installation and really messed it up so I decided just to reinstall).  Anyway, now on the boot menu there's the "good" copy of Ubuntu and the messed up version.  How can I remove the messed up version as an option?

Thanks!
-S

```
**gksudo** gedit /boot/grub/menu.lst
```

and then run:

```
sudo update-grub
```

---

### Post by spencewah on 2007-05-09
> **alienexplorers said:**
> Go into terminal and type:



Remove or prefix all lines for this messed up build with #.

Save menu.lst

This should get rid of the problem

Worked like a charm, thanks!

---

