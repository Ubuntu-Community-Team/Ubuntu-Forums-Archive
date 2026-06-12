---
title: "authentication rejected need help"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by morfy on 2006-09-29
~$ gksudo gedit /etc/apt/sources.list
(gedit:5049): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Kateikyoushi on 2006-09-29
Does it work if you try this ?

```
sudo nano /etc/apt/sources.list
```

---

### Post by Scorpuk on 2006-09-29
Whenever I need to use gedit as sudo I just use sodu and not gksudo.


```
sudo gedit /etc/apt/sources.list
```

The only time I have used gksudo was to launch nautilus with root privilages, BUT that can be dangerous if you delete the wrong file or such like. ;)

---

