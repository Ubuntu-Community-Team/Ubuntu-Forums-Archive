---
title: "Error al actualitzar el grub-pc (a falta d'un titol millor)"
date: 2010-08-13
forum: Catalan Team
---

### Post by Quepotser on 2010-08-13
Hola tothom.

Cada vegada que actualitzo o instal·lo un programa m'apareix un missatge d'error:[http://ubuntuforums.org/attachment.php?attachmentid=166317&stc=1&d=1281699662](http://ubuntuforums.org/attachment.php?attachmentid=166317&stc=1&d=1281699662)
Ja fa unes dues o tres setmanes que m'ho fa. He mirat a molts llocs però no sé trobar cap cas que s'ajusti exactament a aquest. 
Utilitzo el Lucid en un Acer Aspire 7736G.
Si algú en sap alguna cosa i m'ho vol fer arrivar li estaria molt agraït. Merces per endevant.

---

### Post by wgarcia on 2010-08-21
El primer que pots provar és reconfigurar tots els paquets que no estiguin configurats per veure si t'ho arregla. Ho pots fer amb la següent comanda:

sudo dpkg --configure -a

A veure si això t'ho arregla.

---

### Post by Quepotser on 2010-08-21
hola: gracies per l'ajut, però el [B]dpkg[B] ja l'havia probat i em responia amb el mateix missatge. Finalment ho he arreclat esborrant tot el que tinguès a veure amb el grub i tornant a instal·lar-lo. Ara ja funciona de conya. El què no sé és si funciona el "Sol·lucionat" per posar-lo al titol.

---

