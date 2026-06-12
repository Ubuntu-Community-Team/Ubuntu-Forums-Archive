---
title: "Impossible instalar ATI Radeon HD 4250"
date: 2012-05-29
forum: Catalan Team
---

### Post by Arteazul on 2012-05-29
Hola a tots, estic a punt de tornar a Windows desesperat!!

Quan instal·le Ubuntu 12.04 i li done a controladors adicionals, m'instal·la els antics drivers de la placa base, però no els nous (hi ha dos), aleshores, això dona com resultat un fum d'errors:
- He d'iniciar i reiniciar ubuntu com 10 vegades abans de poder tindre so i video.
- Quan tinc video, aleshores sols tinc flash, pero el vídeo s'em veu fatal, a saltitos...
He intentat instal·lar els drivers directament des de la pàgina oficial de AMD i ho he aconseguit, però aleshores tot es veu en 2D...

PER FAVOR, VULL CONTINUAR AJUNDAT A UBUNTU I AL SEU PROJECTE, PERÒ SI NINGÚ NO M'AJUDA, DEURÉ CANVIAR-ME A WINDOWS, PERQUÈ NO PODER VEURE NI PEL·LIS ÉS QUE NO ÉS NORMAL I JA PORTE DOS MESOS AIXÍ.

AL MENYS UNA RESPOSTA, PER FAVOR, NO M'IGNOREU, NO PUC MÉS!

mOLTES GRÀCIES.

---

### Post by kimet on 2012-05-29
El driver lliure em funciona fabulosament, inclosos jocs i programes que demanden alt rendiment gràfic.
Prova a desinstal.lar tot el relacionat amb fglx i reinicia el sistema gràfic.

Siusplau, no majúscules.:)

---

### Post by Arteazul on 2012-05-29
Gràcies, tio, però com ho faig lo de desinstalar els anteriors i instalar els lliures? coneixes alguna guia? Tu també tens esta tarjeta? :)

---

### Post by Arteazul on 2012-05-29
Ja ho he fet!!! amb aquest tutorial!!

[http://www.leanuxeros.com/linux/como-desinstalar-los-drivers-privativos-catalystfglrx-en-ubuntu-11-10-y-derivados/](http://www.leanuxeros.com/linux/como-desinstalar-los-drivers-privativos-catalystfglrx-en-ubuntu-11-10-y-derivados/)

La cosa encara no va perfecta però ja s'ha millorat moltíssim!!!

Moltes moltes gràcies. Has escrit una línia i m'has canviat dos mesos sense poder veure pel·lis al meu ordinador. Mira que és fàcil i bonic ajudar-se:

GRÀCIES (sí, en majúscules)!!! :)

---

### Post by akyra on 2012-05-30
Hola,

Jo vaig tenir aquest problema amb la versió anterior de Ubuntu, i des de les hores utilitzo els drivers lliures, i funcionen perfectament.

Salutacions.

---

### Post by AlbertJB on 2012-06-01
Jo també he tingut problemes amb la targeta gràfica ATI RADEON SAPPHIRE 5450. 

El que vaig fer va ser instal·lar els drivers privatius seguint les passes de :


[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

escollint la versió 12.04 en aquest cas:  [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Abans d'instal·lar-los, has de desinstal·lar fent un --purge dels drivers anteriors, aquest punt és important.

---

