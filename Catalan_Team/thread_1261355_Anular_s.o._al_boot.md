---
title: "Anular s.o. al boot"
date: 2009-09-08
forum: Catalan Team
---

### Post by JUSTERINI1 on 2009-09-08
Hola,
Soc novell i mica en mica vaig aprenent.
Vaig instal.lar l'ubuntú, llavors l'XP i novament l'ubuntú, el resultat és que ara en el boot em surten a triar:
Ubuntú a sda3 que és el bo
Ubuntu a sda1, partició de 3Gb que està formatejada amb el gparted.
Xp a sda2
El que vull és que en el boot no em surti la opció del sda1 doncs no hi ha informació, no hi ha dades, amb el StartUp-Manager veig que no ho puc fer.
Sabeu com ho puc fer? editant el boot? com es fa?

I ja posats, puc posar els 3Gb del sda1 dins del sd3, o no val la pena?

Gràcies per la vostra ajuda.

Justerini

---

### Post by orestesmas on 2009-09-08
> **JUSTERINI1 said:**
> Hola,
Soc novell i mica en mica vaig aprenent.
Vaig instal.lar l'ubuntú, llavors l'XP i novament l'ubuntú, el resultat és que ara en el boot em surten a triar:
Ubuntú a sda3 que és el bo
Ubuntu a sda1, partició de 3Gb que està formatejada amb el gparted.
Xp a sda2
El que vull és que en el boot no em surti la opció del sda1 doncs no hi ha informació, no hi ha dades, amb el StartUp-Manager veig que no ho puc fer.
Sabeu com ho puc fer? editant el boot? com es fa?


Cal que editis el fitxer /boot/grub/menu.list per tal d'eliminar les entrades que no vulguis, però si no ets massa expert fes una còpia de seguretat del fitxer original abans de modificar res, per restaurar-lo fàcilment en cas d'error.

I tingues cura de no modificar l'entrada corresponent al kernel actual, perquè si ho fas malament no podràs arrencar.

> **JUSTERINI1 said:**
> I ja posats, puc posar els 3Gb del sda1 dins del sd3, o no val la pena?


Pots reformatejar la partició /dev/sda1 i usar-la com a espai addicional de dades, muntant-la sobre /opt, /tmp, /usr/local o qualsevol altre directori que et vagi bé. O també pots fer-la servir de swap, però ja en deus tenir una. Tot això es fa tocant el fitxer /etc/fstab.

Si tens un disc petit amb poc espai, potser val la pena. Altrament pots esperar per recuperar l'espai buit fins a una altra ocasió en què reinstal·lis tot el sistema i reparticionis el disc de nou.

---

### Post by JUSTERINI1 on 2009-09-09
Doncs he editat el boot i ha funcionat, fins i tot l'he catalanitzat una mica.
jeje

Gràcies Orestesmas.

---

