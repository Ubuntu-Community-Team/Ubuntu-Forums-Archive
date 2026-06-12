---
title: "off topic: Llistar directoris de qualsevol web?"
date: 2009-06-01
forum: Catalan Team
---

### Post by kukat on 2009-06-01
Es una pregunta un poc estranya...Hi ha alguna forma de llistar el contingut de una web??? O siga...veure tota l'estructura de carpetes i fitxers mitjançant algun comandament o algun programa???

Es que he estat buscant i buscant i no trobe res!!

Tenint en compte que hi haurà moltes maneres d'evitar açò per motius de seguretat, clar...(vaja pregunta "piratilla"....:p)

Salut!

PD: Es per un motiu "cultural" !!!!:)

---

### Post by papapep on 2009-06-01
Senyor meu! tenim el meravellós **[COLOR="DarkOrange"]wget[/COLOR]** !!

Amb:

```
wget http://elteullocweb.net
```

Descarregues la pàgina principal d'un lloc web.

amb:

```
wget -r http://elteullocweb.net
```

intentes descarregar de manera recursiva tot el seu contingut.

Com que, com tu bé intueixes, no sempre és una pràctica benvinguda, amb:

```
wget --wait=15 --limit-rate=20K -r -p -U Mozilla http://elteullocweb.net
```

Intentes descarregar tot el lloc (-r), amb tot el contingut necessari (-p), sense passar-te ocupant ample de banda (--limit-rate=20K), fent pauses de 15 segons per a que l'administrador no sospiti massa (--wait=15) i identificant la sessió com si fos un navegador "normal" (-U Mozilla).

Per que després diguin que emprar el terminal és cutre!!! :D

---

### Post by kukat on 2009-06-01
:D

Senzillament........genial!!!!

Acabe de veure un programa anomenat httrack, però....
Açò es el que volia!!!

Gràcies!

:D

PD: Visca el terminal!!!!

---

