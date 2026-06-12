---
title: "Error: no es pot muntar el volum"
date: 2009-02-25
forum: Catalan Team
---

### Post by diablessamariken on 2009-02-25
Hola ubuntaires

tinc un problema que m'ha deixat glaçada...

He intentat accedir a les dues particions del disc dur que tinc (C: i D:) i de sobte m'apareix aquest error:
[I]
No es pot muntar el volum
Detalls: mount: només l'usuari root pot muntar /dev/sda3 a /media/sda3[/I]

Algú sap què vol dir i què puc fer?? 
No entenc com ha passat, no he fet res diferent de la resta de dies, només configurar una nova xarxa wifi. I ara no puc accedir a les meves carpetes...
Evidentment se suposa que jo sóc l'usuari administrador (de fet no tinc cap altra compta d'usuari configurada).

Em doneu un cop de mà? 

Gràcies

Astrid

---

### Post by papapep on 2009-02-25
> Evidentment se suposa que jo sóc l'usuari administrador (de fet no tinc cap altra compta d'usuari configurada).


Vols dir que **sempre** i constantment treballes com a root????

---

### Post by diablessamariken on 2009-02-25
ui... ara m'has fet dubtar i he mirat què diu dels usuaris i he vist que n'hi ha dos: 
Astrid
Root

Això vol dir que dec haver d'accedir des de root per mirar els disc durs? i perquè abans sí que podia?... quin embolic...

---

### Post by papapep on 2009-02-25
> Això vol dir que dec haver d'accedir des de root per mirar els disc durs? i perquè abans sí que podia?... quin embolic... 

Des de la llunyania ho tinc complicat per saber "efectivament" que pots haver fet :-)

Però quan entres a l'ordinador, amb quin usuari t'identifiques, root o astrid? Si has treballat com a root és possible que hagis modificat permisos de fitxers, directoris o dispositius, deixant-los fora de l'abast dels usuaris "comuns", però això només ho pots saber tu ;-)

Ara que hi penso.....per què anomenes les particions C i D???? en Gnu/Linux no es diuen pas així...[-(

Enganxa el resultat de:

```
cat /etc/fstab
```

i 

```
sudo fdisk -l /dev/sd*
```

---

### Post by diablessamariken on 2009-02-25
ja està ja està!!!

resulta que ahir es va tancar malament el windows després de fer-hi la instal·lació de la nova xarxa wifi i això no permetia que l'ubuntu obrís els disc durs :)

Ho he llegit d'un fil similar però més complex i en CarlesOriol donava aquesta explicació. 
Només cal reiniciar i tancar correctament el windows i tot solucionat! buff! quin descans!!

MOltes gràcies i perdoneu les molèsties!!

Astrid

---

