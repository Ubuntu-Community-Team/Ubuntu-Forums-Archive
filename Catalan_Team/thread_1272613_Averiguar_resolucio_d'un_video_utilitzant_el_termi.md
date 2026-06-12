---
title: "Averiguar resolucio d'un video utilitzant el terminal"
date: 2009-09-22
forum: Catalan Team
---

### Post by PatrickVogeli on 2009-09-22
Hola a tothom!

Estic intentant trobar una ordre que simplement em digui la resolució d'un video. Fent ffmpeg -i video em dona molta infomació, però jo només necessito la resolució, ja que es per passar-la a un script.

Algu te idea de com fer-ho??

Merci!

---

### Post by orestesmas on 2009-09-23
No conec cap ordre especial per fer-ho, però pots aïllar la resolució a partir de l'ordre anterior fent quelcom semblant a això:
```

ffmpeg -i nom_del_fitxer_de_video 2>&1 | grep Video | cut -d "," -f 3

```

Després pots passar aquest resultat al teu script.

Clar que si el fitxer conté més d'un stream de vídeo això et retornarà més d'un resultat, i probablement no et servirà.

---

### Post by PatrickVogeli on 2009-09-23
Perfecte!!

He hagut d'afegir alguna cosa a la teva ordre, pero ara ja esta!


La teva ordre retorna aixo:
$ ffmpeg -i LockStock2SmockingBarrels.avi 2>&1 | grep Video | cut -d "," -f 3
 320x170 [PAR 1:1 DAR 32:17]

Despres d'afegir-hi 1 coseta més:
$ ffmpeg -i LockStock2SmockingBarrels.avi 2>&1 | grep Video | cut -d "," -f 3 | cut -d "[" -f -1
 320x170 

Moltes gracies Orestes, ets un crack!

Per cert, aixo de 2>&1 que fa exactament?

---

### Post by papapep on 2009-09-23
[http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/](http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/)

De fet, aquí ho explica encara millor: [http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by orestesmas on 2009-09-23
> **PatrickVogeli said:**
> 
Per cert, aixo de 2>&1 que fa exactament?

Essent una mica menys concís que el Papapep, potser caldria dir que una consola té dos "canals" per treure missatges: la sortida estàndard (stdout) i la sortida d'error estàndard (stderr). Quan tu desvies la sortida d'un programa cap a un fitxer (amb ">") o canonada ("|") estàs desviant la sortida estàndard, no la d'error. I sembla que el "ffmpeg -i" treu els seus missatges per la sortida d'error. Això pot ser una elecció del programador, que usa probablement la sortida d'error per enviar missatges a l'usuari, i deixa la sortida estàndard per a enviar-hi el material multimèdia processat (si no l'hem redirigit a un fitxer amb l'opció -o), cosa que pot ser útil per encadenar-lo amb altres programes.

Així, doncs, l'ordre 2>&1 el que fa és redirigir cap a la sortida estàndard els missatges que van a la sortida d'error, llavors pots encadenar la sortida cap al "grep".

---

### Post by papapep on 2009-09-23
Concís? Jo? Mai! :P

---

