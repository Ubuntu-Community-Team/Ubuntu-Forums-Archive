---
title: "Problema al ficar en maxa la 10.4"
date: 2010-05-01
forum: Catalan Team
---

### Post by lluisalguero on 2010-05-01
Hola companys,
avui he fet l'actualització a la 10.4 i després de una bona estona ja la tenia rutllant. De moment semblava que anava prou bé, i mirant opcions i demés novetats, he instal·lat "Docky" per mirar de fer l'escriptori una mica més "amigable".
Com que no m'ha convençut, l'he desinstal·lat i he passat a tornar-ho a deixar tal i com ho tenia al principi (afegir la barra de sota i les icones). Doncs m'ha sortit un error (ho sento, no he pensat en anotar-ho) i m'ha tocat reiniciar-lo a la "brava". Des de llavors quan entro i trio al Grub l'opció en concret, fa que carrega però, al final es queda amb el dibuix de fons d'escriptori (sense icones ni res) i a l'extrem superior esquerre una finestra de la consola.
I aquí be el problema, no sé que haig de fer, ni que ha pogut passar, no sé si és que s'ha desconfigurat l'entorn gràfic o veritablement m'he "carregat" alguna cosa més important.
Dir-vos que he provat el "recovery mode" i nuclis més antics i no fan res, ni tant sols apareix la finestra de la consola.

Gràcies per l'ajuda que em pugueu donar.

Lluís

---

### Post by lluisalguero on 2010-05-01
He anat buscant informació pel Google, de moment he provat:

```
sudo /etc/init.d/gdm restart
```

sense cap resultat positiu...torna al lloc on estava :(

---

### Post by lluisalguero on 2010-05-01
continuo buscant informació, l'error que em surt al fer "startx" és aquest:

> Fatal server error
Server is already active for display0
If this server is no longer running,
remove /tmp/.X0-lock

he fet

```
rm -rf /tmp/.X0-lock
```

i tampoc en trec l'aigua clara, surt el mateix error

Per fi intento una reinstalació

```
sudo apt-get install -f
```

però no fa res, no actualitza res ni instala res...

continuo buscant informació, però si algú mentrestant em pot tirar un cable em faria un gran favor

---

### Post by SiscoGarcia on 2010-05-01
Prova amb:

```
sudo dpkg --configure -a
```

a veure què.

---

### Post by lluisalguero on 2010-05-02
> **SiscoGarcia said:**
> Prova amb:

```
sudo dpkg --configure -a
```

a veure què.

Res Sisco...ho fico i al fer intro, torna a sortir la linea de comandos, no fa res en absolut...estic desesperat i no sé per on tirar...

Gràcies per l'ajuda

---

### Post by lluisalguero on 2010-05-02
Bé, per fi ho he aconseguit !!!!!

el que he fet ha estat

```
sudo apt-get install ubuntu-desktop
```

Gràcies a tots, tanco el post

---

### Post by SiscoGarcia on 2010-05-02
No fotis, havies perdut l'escriptori!

Bé, me n'alegro que se t'hagi resolt per fi el problema... ara ja pots començar a gaudir de la lucid :D

---

