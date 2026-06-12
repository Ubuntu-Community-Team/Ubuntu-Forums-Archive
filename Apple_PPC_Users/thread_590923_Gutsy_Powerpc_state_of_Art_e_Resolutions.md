---
title: "Gutsy Powerpc state of Art e Resolutions"
date: 2007-10-25
forum: Apple PPC Users
---

### Post by robyinno on 2007-10-25
**Make STABLE Gutsy Powerpc**
At the moment i have installed gutsy powerpc on my Powerbook G4, but there are still many problems, so I think we can put posts here** solutions** for make the **gutsy for powerp**c stable.
If some one open a wiki regarding this is a good bless, please post in this thread the link.

---

### Post by robyinno on 2007-10-25
About wireless problem:
[http://ubuntuforums.org/showthread.php?t=590597]("http://ubuntuforums.org/showthread.php?t=590597")

---

### Post by robyinno on 2007-10-25
**if you don't see ethernet :**

[FONT="System"][COLOR="Blue"]sudo if up eth1 inet
sudo dhclient eth1[/COLOR]
[/FONT]
modify /etc/network/interfaces

and write this lines if doesn't exist:
[FONT="System"]
 [COLOR="Blue"]auto eth1
iface eth1 inet dhcp[/COLOR][/FONT]

In these way the changement is permanent.

---

