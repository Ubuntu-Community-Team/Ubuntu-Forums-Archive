---
title: "[SOLVED] instal·lar adaptador Usb Conceptronic C54RU"
date: 2007-07-28
forum: Catalan Team
---

### Post by pablinsfc on 2007-07-28
Hola companys!!

Estic ampliant el radi d'acció d'Ubuntu i he convençut a la meva parella perquè li formategi el PC i li instal·li Ubuntu. El problema que tinc és que a casa seva han instal·lat fa molt poc la Imagenio de Telefònica i ha de conectar-se a internet a través de wifi.

L'adaptador que té és el Conceptronic C54RU (usb), i no hi ha manera d'instal·lar-ho. Porto no se quantes hores entre forums i webs i no me'n surto. En alguna web em diu que haig de mirar que tingui intal·lats uns determinats paquets, però clar, no me'ls puc baixar perquè justament estic instal·lant la connexió!!

Estic molt perdut i ella comença a rajar d'Ubuntu :(

Merci per endavant!

---

### Post by papapep on 2007-07-28
Aquí et deixo un parell d'enllaços de gent que els ha fet funcionar a veure si t'ajuden:

[http://www.ubuntu-es.org/node/10762](http://www.ubuntu-es.org/node/10762)

[http://rubensa.wordpress.com/2006/03/20/ubuntu-c54ru/](http://rubensa.wordpress.com/2006/03/20/ubuntu-c54ru/)

Tots dos són bastant antics, però et poden guiar per a fer-la funcionar.

Per cert, per a fer la instal·lació no hi ha cap possibilitat de que puguis posar un cable ethernet??

---

### Post by pablinsfc on 2007-07-28
Quan pico tan sols la primera ordre:

$ gunzip rt2570-1.1.0-b1.tar.gz

em torna un "bash: $: command not found"

això crec que no és correcte, no?

---

### Post by papapep on 2007-07-28
Tecleja a un terminal:

```
tar xvfz rt2570-1.1.0-b1.tar.gz
```

---

### Post by pablinsfc on 2007-07-28
bones papapep, ho he fet i em retorna això:

gzip: stdin: not in gzip format
tar: child returned status 1
tar: Error exit delayet form previous errors

que faig?

merci per tot!

---

### Post by papapep on 2007-07-28
Bé doncs, fes:

```
sudo aptitude install gzip
```

I després executa el 

```
gunzip rt2570-1.1.0-b1.tar.gz
```

---

### Post by pablinsfc on 2007-07-28
Bones company, ho he fet, han sortit tot de linies de codi, en principi tot bé.
Torno a fer el tar xvfz rt.... .tar.gz

i em retorna el mateix :(

em sap greu ser tant inutil xD

---

### Post by papapep on 2007-07-28
No, no, ara ja no has de **tar xvfz**, ara només has de posar 

```
tar xvf rt2570-1.1.0-b1.tar.gz
```

Sense la "z"

---

### Post by pablinsfc on 2007-07-28
Disculpa, no havia vist la segona linia de codi, fent el gunzip em surt

gunzip: rt2570.... .tar.gz: not in gzip format

---

### Post by pablinsfc on 2007-07-28
Faig tar xvf rt.....tar.gz

em torna:

tar: this does not look like a tar archive
tar: skipping to next header
tar: error exit delayet from previous errors

---

### Post by papapep on 2007-07-28
A veure, algun problema has de tenir amb el fitxer que t'has descarregat. Jo me l'he baixat i m'ha funcionat tant el "tar xvf**z**"  com el "gunzip" i després el "tar xvf".

Necessitaria veure exactament què tecleges i què et torna el terminal. Segur que és un simple error de sintaxi.

Una altra possibilitat és que el paquet que tinguis estigui corrupte. Torna'l a baixar i prova-ho un altre cop.

---

### Post by pablinsfc on 2007-07-28
Merci per tot, company. Ara no tinc mes temps de mirar-m'ho. Ho intentaré de nou més tard i penjaré captures de pantalla perquè pot ser que sigui el que em comentes. De totes maneres, potser acabaré abans baixant a la botiga i comprant un cable de xarxar prou llarg per arribar des del menjador a l'habitació i actualitzar l'Ubuntu, no?? 

Merci per l'ajuda!!

Pau.

---

### Post by pablinsfc on 2007-07-28
Bones papapep! Ara ja sí que no entenc rès de rès... he marxat a demanar un cable de xarxa a un company per conectar el PC amb el router del menjador. Al arribar he engegat el PC i he seguit remenant perquè no el podia passar el cable (era mal moment, és igual).

En fi, buscant no se m'acudeix rès més que obrir "Eines de xarxa", he anat mirant cosetes x aki (sense tocar rès) i he vist la pestanya "ping". Tot i que els meus coneixements informàtics siguin una mica baixos... sé que pots fer (i he fet varies vegades) ping a una adreça per saber si respon.

I quasi per rutina de veure kin error donava, he provat un ping a 192.168.1.1 (l'adreça dels routers de telefònica). I la meva sorpresa ha sigut bastant gran quan he vist que responia. Primer he pensat que no podia ser. L'he fet des del FIrefox i també m'anava. Finalment [www.ubuntu.cat](www.ubuntu.cat) i perfecte!!!! 

De totes maneres em fa ràbia perquè NO SE com s'ha solucionat, però mira, una cosa menys. Ara estic actualizant amb el gestor d'actualitzacions i demés.

Merci per tot el teu temps!!! Sou genials!!

Segueixo invetigant a l'Ubuntu!

Pau.

---

### Post by papapep on 2007-07-28
M'alegro que t'hagi funcionat encara que no sàpigues perquè :-D

Vull assumir que, simplement, el kernel que tens ja el suporta i no ho sabiem.

---

### Post by pablinsfc on 2007-07-28
Segurament serà això. He estat llegint en HOWTO's que a partir de la versió 6.0 aprox i endavant ja porta els drivers de "serie" i que no necessitaven instal·lació, però com que en un inici no em funcionava...

En fi, merci per tot!

---

