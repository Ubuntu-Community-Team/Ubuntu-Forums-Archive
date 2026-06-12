---
title: "Actualitzar des d'instal·lació compartida Windows Vista - Ubuntu 8.04"
date: 2010-04-30
forum: Catalan Team
---

### Post by marcmetallextrem on 2010-04-30
Voldria actualitzar el meu Ubuntu a 10.04 però no sé com fer-ho bé. Tinc un portàtil amb Windows Vista preinstal·lat (sí, ja ho sé) i vaig instal·lar al seu moment Ubuntu 8.04, amb les particions que fa per defecte. Vull substituir l'Ubuntu però conservar Windows sense haver de reinstal·lar-lo, ja que tot i ser còpia legal no tinc el disc (sí, ja ho sé!!)

Alguna idea? He llegit que potser amb Wubi es podria fer però no n'estic segur.

Gràcies!

---

### Post by wgarcia on 2010-04-30
Si tens instal·lat el grub, la pantalla inicial on esculls si vols començar l'Ubuntu o el Windows, no hi ha cap problema. Entres a l'Ubuntu, i al Gestor d'actualitzacions t'ha de donar l'opció d'actualitzar a la versió 10.04 (a dalt del tot de la finsestra hauria de dir "Nova distribució ..."). 

Si actualitzes l'Ubuntu d'aquesta manera no hi haurà cap problema amb la partició on tens instal·lat el Windows, continuarà funcionant exactament igual.

---

### Post by marcmetallextrem on 2010-05-03
Gràcies, wgarcia, però no veig cap opció de "nova distribució" al gestor d'actualitzacions. He sentit a dir que no es podia actualitzar des de 8.04, potser és per això. Què hauria de fer?

---

### Post by wgarcia on 2010-05-03
Sí, en principi es pot actualitzar directament des de 8.04 a 10.04, ja que es tracta de dues versions "LTS", que vol dir "Long Term Support" o "Suport de llarg termini" en català. 

És estrany que no vegis la possibilitat d'actualitzar a la nova versió des del gestor d'actualitzacions. Reps els avisos de les actualitzacions normals dels diferents paquets?

---

### Post by akyra on 2010-05-03
Has de fer un canvi de 4 versions, i crec que el més assenyat és que l'instal·lis de nou, no que l'actualitzis.

Si vols actualitzar, aquí tens les instruccions oficials:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Sort,

---

### Post by marcmetallextrem on 2010-05-03
Gràcies per les instruccions per actualitzar. La idea era instal·lar Ubuntu de nou, el problema és que amb el CD només puc o bé instal·lar Ubuntu a tot el portàtil (i esborrar Windows) o bé instal·lar Ubuntu 10.04 i conservar Ubuntu 8.04 a més Windows. No sé com passar d'una situació de Windows + Ubuntu 8.04 a una de Windows + Ubuntu 10.04.  

Gràcies als dos!

---

### Post by tanreb20 on 2010-05-03
AMb el LiveCD tens una opció que et permet triar manualment les particions.

Quan hi entres, esborres la ext3(suposu que la tindras ena quet format, la particio on tinguis el 8.04, la marques com a utilizar esta partcion, i /, aixi s'instalara alla i ja estará!

---

### Post by marcmetallextrem on 2010-05-04
Sembla fàcil tanreb20, ho provaré. Realment no cal fer res més?
En fi, ara el tema és que no trobe cap LiveCD disponible, on és?

Moltes gràcies pels consells!!!

---

### Post by marcmetallextrem on 2010-05-15
Ja tinc el LiveCD però després de molt de mirar-ho finalment no ho he fet, em sembla massa complicat. No em deixa eliminar la partició ext3 amb gparted, no sé com quedarà l'arrencada o què he de fer amb la resta de particions com la swap. No hi ha cap tutorial per aquest problema per fer-ho pas a pas? No l'he trobat i segur que no sóc l'únic! 
Gràcies igualment.

---

### Post by SiscoGarcia on 2010-05-17
Això que demanes és possible, com diu wgarcia, de fet jo ho he aconseguit. T'explico: obre un terminal i actualitza la màquina

```
sudo apt-get update
```

seguit de 
```
sudo apt-get upgrade
```

un cop la tinguis actualitzada prem Alt + F2 i se t'obrirà una caixeta de diàleg on has d'escriure

```
update-manager -d
```

Amb la qual cosa demanes de forçar una actualització de versió, i el gestor d'actualitzacions t'ha de proposar d'actualitzar a la nova versió 10.04; li dius que vols fer-ho i llestos.

Ja diràs.

---

### Post by marcmetallextrem on 2010-05-22
Gràcies, Siscogarcia però és que no ho veig clar. Aleshores, més enllà de si és possible o no, és recomanable actualitzar des de 8.04 o no?

---

### Post by SiscoGarcia on 2010-05-22
> **marcmetallextrem said:**
> [...]és recomanable actualitzar des de 8.04 o no?

Jo sí que ho trobo recomanable, però és una qüestió que hauràs de decidir tu mateix... sota la teua responsabilitat ;)

---

