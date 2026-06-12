---
title: "tornar a una versió anterior del Mysql"
date: 2010-06-02
forum: Catalan Team
---

### Post by jaumety on 2010-06-02
Hola de nou, al actualitzar l'ubuntu server també m'ha actualitzat la versió del mysql a la versió 5.1.37, com ho puc fer per tornar a instalar una versió anterior i d'on la puc treure?

---

### Post by wgarcia on 2010-06-02
Si vols tornar a la versió 5.0 (després de fer còpies de seguretat de les teves dades), primer hauràs d'eliminar tots els paquets de la versió actual amb 

sudo aptitude purge paquet1 paquet2 ...

Em sembla que els actuals són:
mysql-server-core-5.1 mysql-server-5.1 mysql-cluster-server-5.1

i després buscar els "deb" que encara hi són al repositori de karmic i instal·lar-los a mà, per exemple mysql-server-5.0 el pots trobar a:

[http://packages.ubuntu.com/karmic/i386/mysql-server-5.0/download](http://packages.ubuntu.com/karmic/i386/mysql-server-5.0/download)

Si a més fas servir mysql en combinació de php també hauràs de degradar php.

---

### Post by jaumety on 2010-06-02
tinc un problema afegit, crec, el cas és que penso que tinc instalat ubuntu 64 bits (com ho podria esbrinar?). Hauria de d'instalar un mysql per 64 bits?

---

### Post by papapep on 2010-06-02
Jaumety, potser seria millor que ens expliquessis detalladament quin/s problema tens en concreti aixi seria mes facil respondre't de manera adient (ho sento, ara no tinc accents...)

---

### Post by indiosincracia on 2010-06-02
lshw -C CPU|grep width

---

### Post by jaumety on 2010-06-03
doncs bé, al actualitzar el servidor des de ubuntu 9.04 a 10.04, el programa que tinc de facturació i que fa servir la base de dades msql dona algún error que no donava abans de l'actualització, el cas és que m'han aconsellat que torni a la versió anterior del msql. El problema és que no se quina era aquesta versió.

---

### Post by wgarcia on 2010-06-03
La versió d'Ubuntu 9.04 (Jaunty) era:

mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.3)

Els arxius deb d'instal·lació els pots trobar a:

[http://packages.ubuntu.com/jaunty/i386/mysql-server-5.0/download](http://packages.ubuntu.com/jaunty/i386/mysql-server-5.0/download)

si és de 32 bits.

---

### Post by papapep on 2010-06-03
Doncs per saber quina versió tenies instal·lada de mysql: [http://packages.ubuntu.com/search?keywords=mysql-server&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=mysql-server&searchon=names&suite=karmic&section=all)

Suposadament, serà la versió anterior a la que tens actualment instal·lada.

I a la 10.04 sembla que van prou més avançats, com és normal: [http://packages.ubuntu.com/search?keywords=mysql-server&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=mysql-server&searchon=names&suite=lucid&section=all)

Respecte la versió que tens instal·lada, amb un:

```
uname -a
``` 

hauries de veure quina arquitectura de nucli estàs executant. 
En el cas de la màquina on sóc ara:

Linux SIST001 2.6.24-27-generic #1 SMP Wed Mar 24 10:04:52 UTC 2010 **i686** GNU/Linux

---

### Post by jaumety on 2010-06-03
fent uname -a em diu això:
Linux servidor 2.6.31-21-server #59-Ubuntu SMP Wed Mar 24 08:26:06 UTC 2010 x86_64 GNU/Linux

---

### Post by papapep on 2010-06-03
Doncs el teu sistema instal·lat és de 64 bits:

Linux servidor 2.6.31-21-server #59-Ubuntu SMP Wed Mar 24 08:26:06 UTC 2010 ***x86_64*** GNU/Linux

---

### Post by wgarcia on 2010-06-03
A més no sembla que estiguis actualitzat a 10.04, ja que aquesta versió porta els nuclis amb número de versió 2.32.xx i el teu resultat mostra 2.31.xx, a no ser que estiguis arrencant el sistema amb un nucli que no és l'últim disponible. 

Per veure quina versió d'Ubuntu tens instal·lat pots anar a Sistema - Sobre Ubuntu i et mostrarà quina versió d'Ubuntu tens.

---

### Post by PatrickVogeli on 2010-06-03
si, el wgarcia té raó. Es possible que t'hagis quedat a mitja actualització? Té tota la pinta que alguna cosa no va acabar d'anar massa bé.

Salut

---

### Post by jaumety on 2010-06-04
estic ben perdut,
fent:~# cat /etc/lsb-release em surt això:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

que en penseu? i que creieu que hauria de fer?

---

### Post by wgarcia on 2010-06-04
Potser fora millor exactament explicar exactament quina disfunció tens. De moment està clar que la versió que tens instal·lada és la Karmic Koala (Ubuntu 9.10) que és la versió anterior a l'actual (Lucid Lynx 10.04), però tu deies que havies actualitzat a aquesta última versió. Però en realitat aquest fil va començar amb la teva pregunta de com degradar mysql, que no té res a veure amb tot això. Penso que seria millor un altre fill, descriure exactament el problema que tens o què vols fer, i donar el màxim de dades sobre el teu sistema.

---

### Post by jaumety on 2010-06-08
finalment ho he arreglat fent una instal·lació neta des de zero.

De totes maneres, gràcies.

---

