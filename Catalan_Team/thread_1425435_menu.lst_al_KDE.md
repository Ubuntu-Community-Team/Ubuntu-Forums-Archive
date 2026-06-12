---
title: "menu.lst al KDE?"
date: 2010-03-09
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2010-03-09
Bon dia.
A un Kubuntu 9.10 no li trobo l'arxiu menu.lst
He mirat a /boot/grub i no hi és.
He fet una cerca, i res.
Algú sap com editar el grub amb kde?
Gracies.

---

### Post by bruno9779 on 2010-03-09
El funcionamento de grub no tiene diferenca entre Gnome y KDE.

Lo que si es diferente desde 9.10 es que la instalaccion predeterminada utiliza grub2 en lugar de grub-legacy.

Grub2 funciona en manera bastante diferente, y menu.lst ya no se edita.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Disculpa por la respuesta en Castellano...

---

### Post by Miquel Ubuntero on 2010-03-09
> **bruno9779 said:**
> El funcionamento de grub no tiene diferenca entre Gnome y KDE.

Lo que si es diferente desde 9.10 es que la instalaccion predeterminada utiliza grub2 en lugar de grub-legacy.

Grub2 funciona en manera bastante diferente, y menu.lst ya no se edita.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Moltes gràcies per respondre bruno. Ja he solventat els meus dubtes.


Disculpa por la respuesta en Castellano...

Per part meva estàs disculpat. Però ja que sembla que entens el català, hauries d'intentar d'escriure'l i respectar les normes del foro.
Salut i gràcies de nou. ;)

---

### Post by wgarcia on 2010-03-09
L'equivalent de "menu.lst" a grub2 és "grub.cfg", però no s'ha d'editar directament, sinó que els canvis s'han d'introduir als arxius que es troben a /etc/default/grub i /etc/grub.d (si se sap el que s'està fent, és clar, no hi ha millor manera de congelar l'arrencada de l'ordinador que tocar el grub sense saber el que s'està fent :) ), i córrer:

update-grub

per incorporar els canvis a "grub.cfg".
Una font útil sobre Grub2 és:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
(en anglès)

---

