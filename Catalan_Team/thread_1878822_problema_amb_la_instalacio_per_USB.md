---
title: "problema amb la instalacio per USB"
date: 2011-11-10
forum: Catalan Team
---

### Post by ETP on 2011-11-10
Bona tarda, avui hem instalat un Ubuntu server 32b desde un USB com a disc d'arranc, ja que el servidor no tenia CD. la instlacio l'ha feta correctament, pero quan hem reiniciat el server, hi hen tret el USB, no s'engegava. Ens hem adonat que posant-hi el USB de instalacio, i reinician s'engega i funciona correctament, i un cop engegat es pot treure el USB, per engegat. Suposo que es problema de grups a la instal·lació, pero.....
Com s'ha de fer per solucionar això?
Gracies

---

### Post by wgarcia on 2011-11-10
No s'haurà instal·lat el grub al MBR del disc USB?

---

### Post by ETP on 2011-11-11
crec que si que el problema esta al grub, pero ara com que s'engega correctament amb el USB, un cop esta estable puc treure el usb i canviar el grub, ja que va per identificador....

---

### Post by wgarcia on 2011-11-11
Sí, o reinstal·lar el grub al MBR del disc dur, si es diu /dev/sda seria "grub-install /dev/sda".

---

