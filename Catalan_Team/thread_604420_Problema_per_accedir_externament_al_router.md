---
title: "Problema per accedir externament al router"
date: 2007-11-06
forum: Catalan Team
---

### Post by klonner on 2007-11-06
Bones.

Al servidor he instal·lat una pàgina wordpress, i el problema que tinc és que si puc entrar jo, des de fora de la xarxa no poden entrar-hi(els envia cap al router segons m'han dit), i si a la configuració del wordpress li canvio la ruta de la IP interna pel redireccionament, des de fora poden entrar perfectament, però llavors a m'envia a mi cap al router tant posant el redireccionament, com posant la ip del pc en qüestió.

Fa un temps al servidor vaig instal·lar un fòrum phpbb i vaig aconseguir arreglar-ho, però ara no trobo la solució 


també em va comentar un amic que no se com es podia fer que accedint des de dins posant el redireccionament que enviés a la carpeta on està allotjada la pàgina.


Mercès!

---

### Post by papapep on 2007-11-06
"L'únic" que has de fer és que el router redirigeixi el port 80 a la ip del teu servidor.
El com depén directament del model i marca del router que tinguis.
Evidentment, també cal que verifiquis que no tens el port 80 tancat pel firestarter o similars.

---

### Post by klonner on 2007-11-06
el port està obert per l'ordinador en questió.
No es problema de ports (crec), ja que hi tinc àlbums del picasa penjats, i jo posant la IP del PC (el servidor és un PII reciclat) puc veure'ls perfectament, i la gent des de fora també(posant el redireccionament).

Entre el moment de crear la base de dades del wordpress, i fer l'install.php, des de fora podien veure que no estava instalat, els donava el mateix error que em sortia a mi, entrant directament sense cridar l'install.php

---

### Post by papapep on 2007-11-06
> el port està obert per l'ordinador en questió.

Amb això estàs dient que el router ja té el port 80 redirigit al servidor web que hostatja el wordpress??

> i jo posant la IP del PC (el servidor és un PII reciclat) puc veure'ls perfectament, i la gent des de fora també.

....estic en un mar de dubtes...el Picasa permet servir les fotografies des de l'ordinador on és instal·lat??? O parles dels Picasa Web Albums que Google proporciona als seus servidors?

I si realment ho permet, per quin port ho fa? Quina url posen els de fora en ambdós casos?

> (posant el redireccionament)

Quin redireccionament??

---

### Post by klonner on 2007-11-06
el port 80 està redireccionat al PC on està allotjat el Wordpress.

el Picasa te una opció per crear albums de fotos que son pagines web, i el que he fet es penjar-ho al servidor dins una carpeta que posa fotos, i tinc una altra carpeta que es diu wordpress.

la gent pot entrar al servidor i veu les dues carpetes la de les fotos i del wordpress, a la de les fotos entra perfectament i a la del wordpress els envia cap al router.

El redireccionament em refereixo al DyNDNS per no haver de posar la IP

Jo entro perfectament als albums i al wordpress amb la IP de la LAN del PC, des de fora als albums cap problema, després si entren al wordpress els reenvia cap al router


Sento no explicar-me millor

---

### Post by papapep on 2007-11-06
Seria possible veure una impresió de pantalla d'aquestes pàgines que dius que el teu servidor proporciona?

He vist que el que fa el Picasa és simplement crear una pàgina estàtica de les fotografies que tu l'hi indiques. Però pel Wordpress ja has configurat l'apache correctament??

---

### Post by klonner on 2007-11-06
[[IMG]http://img465.imageshack.us/img465/683/generalbo0.th.jpg[/IMG]](http://img465.imageshack.us/my.php?image=generalbo0.jpg)

La carpeta general del servidor

[[IMG]http://img223.imageshack.us/img223/1741/fotosvu8.th.jpg[/IMG]](http://img223.imageshack.us/my.php?image=fotosvu8.jpg)

el directori dels albums

[[IMG]http://img223.imageshack.us/img223/2772/albumdx8.th.jpg[/IMG]](http://img223.imageshack.us/my.php?image=albumdx8.jpg)

visualització dun album

[IMG]http://img48.imageshack.us/img48/1315/wordpressxj6.th.jpg[/IMG]


wordpress vist des del meu ordinador (o sigui a traves de la LAN)


des de fora de la LAN accedeixen mitjançant el redireccionament IP [http://blablala.asas.net](http://blablala.asas.net) i si entren als albums pos l'adreça canvia a [http://blablala.asas.net/albums](http://blablala.asas.net/albums) i a l'entrar al wordpress el que passa es que els envia a la IP local del PC [http://192.168.1.10/wordpress](http://192.168.1.10/wordpress)

PD: Sento haver dit que els enviava al router (això em van dir ahir a la nit, ara han rectificat)

PD2: no em feu crits per estar al windows, he de fer servir un programa (PSPICE) i amb wine no aconsegueixo que funcioni!

---

