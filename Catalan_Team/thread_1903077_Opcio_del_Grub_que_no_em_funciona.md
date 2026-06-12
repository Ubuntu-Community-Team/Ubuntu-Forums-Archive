---
title: "Opcio del Grub que no em funciona"
date: 2012-01-01
forum: Catalan Team
---

### Post by jparramon on 2012-01-01
Tinc l'ordinador amb dos disc durs. En un el windows Vista, que es el que normalment treballo. En l'altre canviant l'ordre d'arrencada per la bios, ho tinc el windows 7. Com que en aquest hi tenia més espai vaig instalar en nova partició l'ubuntu en arrencada dual. Des del grub diu que puc arrebcar:
L'ubuntu
....
El windows 7 (sda1)
El windows wista (sdb1)
He editat (sense modificar) el ficher del menú i tot semble correcte, però en els dos últims apartats sempre m'obre el Windows 7.
M'aniria bé poder accedir als tres sitemes operatius sense tenir que tocar la bios.
Es posible?
(Soc principiant en Ubuntu. Amb Linkat em defenso millor. El tinc instalat a l'escola amb servidor, clients i terminals lleugers)

---

### Post by wgarcia on 2012-01-03
Hi ha un programeta molt útil per veure com estan configurades les opcions d'arrencada. El pots baixar de:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Posa'l en qualsevol lloc que puguis accedir (per exemple el teu "home") i entra en una terminal de comandes:

sudo bash ~/boot_info_script*.sh

(això és vàlid si l'has instal·lat al teu home, sinó simplement canvia al directori on el tinguis i posa "sudo bash boot_info_script*.sh".

Crearà un arxiu que es diu "RESULT.txt". Enganxa aquest fitxer aquí (no enganxis el text perquè pot ser llarg) i a veure si es pot esbrinar què està passant.

---

