---
title: "l'hora friki"
date: 2009-02-12
forum: Catalan Team
---

### Post by lluisanunez on 2009-02-12
Hola,
divendres a la nit, a les 0:30 aprox es produïrà la hora Unix 1234567890
Com que a més s'escau en una hora que estarem acabant de sopar, i hi haurà  gent bastant friki, volia posar a la configuració del rellotge el temps Unix en comptes del UMT., i aprofitar l'ocasió per a brindar (més). 
Doncs l'opció Unix Time ha **desaparegut** de la configuració del rellotge!!! Algú sap com es pot fer?

PS. Ja sé que es pot anar a una pàgina com [http://cntdwn.eu](http://cntdwn.eu), però volia que ho fes el meu PC...

---

### Post by kukat on 2009-02-12
Ostres, pots explicar que es això de l'hora UNIX? he entrar a la web i sembla curiós...però no se que es! :confused:

EDITO: He llegit alguna cosa en la wikipedia, però segueix sense saber res....jajajja

---

### Post by lluisanunez on 2009-02-12
Doncs a la wikipedia diu que és la manera de consignar un punt concret en el temps, a base de comptar els segons que han passat des de l'1 de gener de 1970 a les dotze de la nit (UTC)
La curiositat és que divendres a la nit, o per ser exactes dissabte a la matinada, farà 1234567890 segons.
Molts sistemes utilitzen aquest sistema per al seu rellotge, i linux tota la vida(1) t'havia deixat l'opció entre temps clàssic o UTC, Unix Time o Internet Time

(1) em sembla que va ser al Hardy on va desaparèixer aquesta opció (o és cosa del Gnome)

---

### Post by papapep on 2009-02-12
És tan simple, o complicat, com pensar que les 00:00h del dia 01.01.1970 és l'inici del temps pels sistemes Unix, i derivats. A partir d'aquí el temps es calcula en el nombre de segons transcurreguts des d'aquest moment, sumats un darrera l'altre.
Si vols convertir aquest nombre als nostres acostumbrats hora-minut-segon, només has d'operar amb el nombre:

1234567890 / 3600 = 342935,525 hores transcorregudes des de 01.01.1970

342935,525 / 24 = 14288,980208333 dies

14288,980208333 / 365 = 39,147890982 anys

tot això és aproximat, sense considerar anys de traspàs ni els segons de compensació que s'ha d'afegir cada cert nombre d'anys  ;-)

---

### Post by RainCT on 2009-02-12
Per a veure el temps UNIX des de la terminal:

```
python -c 'import time; print int(time.time())'
```

---

### Post by kukat on 2009-02-12
això de "no et gitaràs sense saber alguna cosa més" sembla que es cert!!! jejejej
gràcies!

---

### Post by kukat on 2009-02-12
no hi ha forma de posar el rellotge eixe en temps real?
o siga, que vaja passant com si fos un cronòmotre en algun lloc de la pantalla? com si fos el rellotge? jajaja
seria curiós!

---

### Post by papapep on 2009-02-12
XFCE ho fa :-P
Mireu a la barra de dalt... (elis, elis...:-D)

[[IMG]http://img17.imageshack.us/img17/439/xfcerulezji1.png[/IMG]](http://img17.imageshack.us/my.php?image=xfcerulezji1.png)

---

### Post by papapep on 2009-02-12
Per cert, crec que amb qualsevol rellotge que us permeti especificar el format de representació del temps us permetrà visualitzar-ho en format de temps unix. Heu de triar/posar el format:

```
%s
```

la 's' ha de ser minúscula.

---

### Post by kukat on 2009-02-13
doncs en l'Intrepid no està l'opció, no se per què l'hauran llevada. Llàstima!

---

### Post by lluisanunez on 2009-02-13
Així doncs, és cosa del Gnome...

---

### Post by tanreb20 on 2009-02-13
I TANT QUE ES POT XAVALS!!!!!!!1

I en gnome!!!!

Obriu

```
gconf-editor
```

aneu a 

```
apps > panel > applets > applet_0 > prefs
```

alla a linea que psoa format escriviu

```
unix
```

I taxaaaan! Hora en sistema UNIX!!!

---

### Post by lluisanunez on 2009-02-13
Olééé, Tanreb20!!!

---

### Post by Daerun on 2009-02-14
Jo a Hardy ho tinc sota
```
apps > panel > applets > clock_screen0 > prefs
```I allà canviar "Format" i posar-hi unix.

Què bó que és això! :lol:

---

### Post by kukat on 2009-02-15
aaaa
doncs ja està! jejeje
Gràcies!!

---

