---
title: "Ubuntu fa el ruc"
date: 2013-01-21
forum: Catalan Team
---

### Post by amirrocat on 2013-01-21
Hola! 

Mireu, Ubuntu fa el ruc, últimament. Primer perquè des de fa la tira que no em deixa obrir el Centre de programari, seguit del fet que Libreoffice ni tant se val s'obre i que ara, a Google Chrome, quan només tinc una pestanya oberta no me l'ensenya, a dalt. 

El cas és que he mirat de fer servir el comando sudo dpkg-reconfigure -phigh -a però no funciona, perquè em dóna aquesta resposta: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: El recurs no es troba disponible temporalment

A la qual cosa he respost amb sudo killall process, però diu que no hi ha cap procés en marxa. 

Què puc fer?

---

### Post by wgarcia on 2013-01-21
Prova obrir una terminal i entrar les següents ordres:

```
sudo touch /var/lib/dpkg/lock
```

Seguit de:

```
sudo dpkg --configure -a
```

i

```
sudo apt-get clean
```

a veure si arregla el problema de no poder baixar i actualitzar el programari.

---

### Post by amirrocat on 2013-01-23
Hola. No ha funcionat. El problema, però, no és que no actualitzi programari, sinó que sembla que l'ordinador se satura de sobte quan carregues depèn quin vídeo o quan jugues al Tetris, simplement. Abans no ho feia, per tant, atribueixo aquest funcionament a un mal funcionament del sistema operatiu que, a més, fa el ruc. 

Com deia, però, no és que no actualitzi programari, sinó que n'hi ha que no em deixa obrir. 

A veure si a algú se li acut una solució...

Gràcies altre cop.

---

### Post by wgarcia on 2013-01-24
Sembla un problema gràfic, però per treure l'entrellat es necessita molta més informació. 

A més això que informes en el segon missatge és molt diferent del que dius en el primer. En el segon comentes problemes de parada del sistema quan estàs executant un joc o vols reproduir un vídeo, mentre que en el primer dius que no s'obre el Centre de Programari, dóna un error en actualitzar, i tens algun altre problema amb LibreOffice que no entec bé quin és. 

Per què no concretes una mica els problemes que hi ha, potser obrint un fil específic per a un en concret, així podem concentrar-nos de moment en un tema específic. Quan millor descriguis què intentes fer, què falla i quin error dóna, més fàcil serà intentar esbrinar què passa.

---

