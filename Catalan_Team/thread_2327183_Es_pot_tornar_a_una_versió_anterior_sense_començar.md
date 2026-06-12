---
title: "Es pot tornar a una versió anterior? sense començar de zero"
date: 2016-06-08
forum: Catalan Team
---

### Post by martibitria on 2016-06-08
Hola bona tarda,

Tenia el UBUNTU 16.04LTS i a terminal amb l'ordre sudo do-release-upgrade -d, em vaig posar la versió 16.10. (aquesta ordre me la van ensenyar a fer regularment)

En el post anterior que parlavem de CD/DVD... ho vaig comentar i el company amb va dir que era molt embrionari, que era millor la 16.04

He mirat per Google i per el fòrum, per tornar enrere hi només veig que has de començar de zero (el meu angles és nul).

Hi ha alguna manera més rapida? per terminal és pot??

Gracies de nou

Martí

---

### Post by wgarcia on 2016-06-08
No, que jo sàpiga no es pot desfer una actualització de versió. L'única manera és instal·lar de zero un altre cop. 

Quant a:
```
sudo do-release-upgrade -d
```
alguns comentaris:

1) Aquesta ordre és per actualitzar des de la línia de comandes, és a dir per actualitzar servidors, tot i que també es pot fer servir a sistemes normals. 
2) Per actualitzar normalment es pot fer servir la interfície gràfica normal. L'Ubuntu ja va oferint actualitzar els diferents paquets, i quan hi ha una versió nova de l'Ubuntu, t'avisa des de la interfície gràfica per si vols actualitzar. 
3) Una altra manera és amb l'ordre:
```
update-manager -d
```
que obre la interfície gràfica, però l'opció "-d" força l'actualització a una versió de desenvolupament, i això no és recomanable a no ser que se sàpiga el que s'està fent. 
4) A Paràmetres del sistema -> Programari i actualitzacions, a la pestanya "Actualitzacions" hi ha una opció per dir-li a l'Ubuntu si es vol que ofereixi actualitzacions de "versions de curt termini" o "de llarg termini (LTS)". Aquestes últimes són les versions d'any parell de l'abril (és a dir 12.04, 14.04, 16.04), i tenen manteniment de llarg termini. Es poden actualitzar cada dos anys o més, perquè tenen suport per (em sembla) 5 anys. Les de "curt termini" s'ofereixen cada 6 mesos, no són tan estables com la de llarg termini (però perfectament utilitzables i prou estables), però tenen el programari totalment actualitzat a les últimes versions.

---

### Post by martibitria on 2016-06-08
OK, s'acord!!
Gracies!!!

Martí

---

