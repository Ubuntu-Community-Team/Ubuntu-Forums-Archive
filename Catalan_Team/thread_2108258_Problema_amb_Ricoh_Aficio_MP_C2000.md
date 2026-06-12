---
title: "Problema amb Ricoh Aficio MP C2000"
date: 2013-01-24
forum: Catalan Team
---

### Post by simfomet on 2013-01-24
Hola a tots,

    fa poc he instal·lat en un pc una mica antic Xubuntu 12.10 i fins ara tot va prou bé, fins i tot me n'he sortit configurant gigolo perquè es connecti a unes carpetes compartides en un servidor amb windows server 2003.

Però tinc problemes amb una cosa aparentment més senzilla com poder imprimir ja que vull imprimir en una Ricoh Aficio MP C2000 i seguint els passos per configurar-la la detecta i tot el procés sembla correcte instal·lant els controladors que em recomana. El problema és que quan vull imprimir en una primera pàgina apareix un text en 5 o 6 ratlles que surt: 

%!PS-Adobe-3.0  %% %% mark ()() (201301241110) {setuserinfo} stopped cleartomark %%

Què puc fer??

---

### Post by wgarcia on 2013-01-24
En aquest fil:

[http://ubuntuforums.org/showthread.php?t=1601797](http://ubuntuforums.org/showthread.php?t=1601797)

Recomanen agafar la següent opció:

Generic PCL 5c Foomatic/hpijs-pcl5c [en]

entre les opcions de tipus d'impressora a la configuració inicial.

---

### Post by simfomet on 2013-01-24
> **wgarcia said:**
> En aquest fil:

[http://ubuntuforums.org/showthread.php?t=1601797](http://ubuntuforums.org/showthread.php?t=1601797)

Recomanen agafar la següent opció:

Generic PCL 5c Foomatic/hpijs-pcl5c [en]

entre les opcions de tipus d'impressora a la configuració inicial.

PERFECTE!!!!  Ha funcionat, d'entre les opcions que hem dóna he escollit Generic PCL 6c Foomatic/hpijs-pcl5c [en] enlloc del 5 que citaves ja que no apareix aquesta opció.
Quan ha acabat li he fet imprimir la pàgina de prova i toooott perfecte.

Moltes gràcies!!!!!!

---

### Post by wgarcia on 2013-01-24
Me n'alegro, si pots marcat el fil com "Solved" (mirant a Thread Tools i escollint aquesta opció) faràs un favor als que consultin el fòrum en el futur.

---

### Post by simfomet on 2013-01-26
Ja està fet, moltes gràcies de nou.

---

