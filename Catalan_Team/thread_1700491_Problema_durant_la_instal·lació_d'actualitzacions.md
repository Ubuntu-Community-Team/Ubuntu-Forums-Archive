---
title: "Problema durant la instal·lació d'actualitzacions"
date: 2011-03-05
forum: Catalan Team
---

### Post by albertdelleida on 2011-03-05
Hola a tothom,

sóc usuari de l'Ubuntu 10.10. Avui he obert el gestor d'actualitzacions i he començat a instal·lar-les. A mitja instal·lació, l'ordinador s'ha penjat i quan he tornat a obrir l'Ubuntu m'ha dit que, degut a un error, l'actualització seria parcial. He continuat i he fet aquesta actualització parcial.

Ara, al col·locar un usb a l'ordinador, si pitjo amb el botó de la dreta sobre la icona per a fer una extracció segura, aquest desapareix i en pocs segons torna a aparèixer. Així, no puc fer una extracció segura. Imagino que això és conseqüència d'aquesta mala actualització. 

Em podríeu explicar com tornar a una versió anterior de l'Ubuntu per a tornar a fer l'actualització correctament? Al menú GRUB he seleccionat l'opció de recovery mode del kernel anterior, he seguit els passos per a reparar els paquets trencats però no me n'acabo de sortir.

Gràcies per la vostra ajuda.


Albert

---

### Post by wgarcia on 2011-03-05
Dues instruccions que a vegades arreglen paquets trencats i desconfigurats són:

sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by albertdelleida on 2011-03-05
Merci wgarcia.

Ho acabo de provar i em diu que no hi ha cap paquet trencat. Ara bé, el problema amb els usb em continua passant. A algú se li acudeix alguna cosa?

Gràcies :)

---

### Post by wgarcia on 2011-03-05
Has provat si et passa també amb un altre usuari que el que fas servir habitualment?

Si no en tens cap pots crear-te un amb Sistema -> Administració -> Usuaris.

---

### Post by albertdelleida on 2011-03-05
Acabo d'intentar accedir a Usuaris i Grups i no puc, no s'obra cap nova finestra :confused: Pot tenir alguna relació amb tot el que m'ha passat?

---

### Post by albertdelleida on 2011-03-05
Sé que no hauria de comentar aquest problema en aquest tema, però ja que tot pot estar relacionat i ser conseqüències del mateix problema, ara tampoc puc obrir els arxius pdf (ahir podia) :(

---

### Post by wgarcia on 2011-03-05
Una possibilitat és entrar en mode "recovery" i mirar si pots provar el que et deia d'obrir un altre usuari.

---

### Post by albertdelleida on 2011-03-06
Gràcies per l'ajuda wgarcia, però al final crec que em decantaré per fer una instal·lació neta de l'Ubuntu 10.10 i axí m'asseguro de solucionar qualsevol problema. En tot cas, altre cop per l'ajuda :)

---

### Post by joaquimrubio on 2011-03-06
Sóc molt inexpert, aleshores no sé si ja queda fet amb les ordres que ja has teclejat, però per sentit comú el primer que jo faria és acabar l'actualització, és a dir:

sudo apt-get update

sudo apt-get upgrade

---

### Post by albertdelleida on 2011-03-06
Merci joaquimrubio però ja he fet una instal·lació neta. He aprofitat el cap de setmana i a començar de nou ;)

---

