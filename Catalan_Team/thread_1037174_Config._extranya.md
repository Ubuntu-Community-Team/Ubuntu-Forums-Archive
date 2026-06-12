---
title: "Config. extranya"
date: 2009-01-11
forum: Catalan Team
---

### Post by tanreb20 on 2009-01-11
Hola!

Tinc un HDD extern que el meu ubuntu em monta sense problemas, pero com a root(suposo que deu ser el normal aixo no?)

la linea del mtab és:

```
/dev/sdb1 /media/Discu fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
```

el problema bé que quan vui accedir a fitxers a traves d altres programes no em deixa modificar dades.

exemple: quan obro el songbird per escoltar musica i vui vambiar alguna metadata del arxiu d emusica em diu que no ticn permissos per fer-ho.

Com podria fer-ho perqué em deixes esditar els arxius en mode usuari normal?

Gracies!

---

### Post by orestesmas on 2009-01-11
És un disc USB? A mi la kubuntu me'ls munta amb els permisos del meu usuari, per la qual cosa hi puc escriure sense problemes. Si no és així, tens alguna cosa malament.

Curiositat: quin sistema de fitxers hi tens?

Com a solució d'emergència pots afegir una ordre al "/etc/fstab" amb l'opció "user" o "users" per tal que qualsevol usuari pugui muntar-lo i desmuntar-lo. El problema és que si és un dispositiu USB a vegades apareixerà com a /dev/sdb1 i a vegades com una altra cosa, per la qual cosa el millor és esbrinar el UUID de la partició (amb "blkid") i usar aquest UUID al fstab enlloc del nom de la partició.

Ah! i un consell: canvia "/media/Discu" per "/media/Disc" perquè "Discu" fa una mica de mal a la vista :-D

---

