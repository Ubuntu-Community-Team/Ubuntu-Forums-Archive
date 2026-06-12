---
title: "Kernel 2.6.28.13"
date: 2009-07-13
forum: Catalan Team
---

### Post by tanreb20 on 2009-07-13
És recomanable instalar els paquets que porten aquesta actualització de kernel?

Un company al que l'ho vaig fer una instalació neta del jaunty al actualitzar-lo em va petar i ara no em vui arriscar, que faig?

---

### Post by oriolsbd on 2009-07-13
Jo sempre faig les acutalitzacions del Kernel, i només un cop em vaig portar una sorpresa.

El Kernel 13, a mi em va donar problemes perquè vaig fer una actualització de les particions d'ext3 a ext4, i vaig haver d'executar una comanda del Grub per a arreglar-ho (no sé si és el mateix que et va passar a tu). Amb Kernels anteriors no tenia aquest problema. Per si és aquest el problema que et donava (o per si li dóna a algú més) el que vaig fer per a arreglar-ho és entrar al sistema amb un LiveCD i executar el següent:
```
sudo mount /dev/sda1 /mnt
sudo grub-install /dev/sda --root-directory=/mnt --recheck
```
Cal tenir en compte que a la primera comanda se li indica la partició on hi ha muntada la "/" del nostre sistema (en el meu cas, /dev/sda1), i a la segona se li ha d'indicar el disc dur on està el grub (/dev/sda).

Salut!

---

### Post by Miquel Ubuntero on 2009-07-14
bones.
Per si és útil la informació, jo he passat d'un Xubuntu 8.10 amb 2.6.27. a Xubuntu 9.04 amb 2.6.28.13 i a anat be.
Salut!

---

