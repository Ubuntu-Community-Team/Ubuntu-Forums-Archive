---
title: "Missatgeria instantània Pidgin no connecta"
date: 2009-12-13
forum: Catalan Team
---

### Post by Curial on 2009-12-13
Bones,

Des de fa uns dies, el Pidgin (2.4.1) no em connecta, em diu que "el servidor no implementa el nostre protocol".

No se si s'haurà deixat de mantenir?

Tinc la Hardy i no se si es millor oblidar-se del Pidgin, desinstal·lar-lo i passar a Empathy.

Que us sembla?

Salut.

---

### Post by sumba on 2009-12-13
Jo utilitzo el Empathy i cap problema en cap dels comptes...

---

### Post by quitus on 2009-12-14
Jo faig servir el pidgin (2.6.2) i em va bé.

salut

---

### Post by Curial on 2009-12-14
Això de la versió em sembla que és important. Estic a la Hardy i no se si puc passar-lo a la teva versió.

Estic tenint problemes també amb l'Empathy i d'altres.(amb Hardy, amb Karmic Koala em funciona bé)

Em sembla que hauré de passar-me a la Karmic com tothom.

Salut.

---

### Post by Pablitus on 2009-12-16
Hola!

Això ha succeït perquè a microssoft han canviat el protocol de missatgeria (eet passa amb un compte de hotmail, no?), o algo així, però ho pots solucionar fàcilment. Mira't això: [URL="http://ubuntulife.wordpress.com/2009/01/12/pidgin-solucionar-problemas-de-conexion-a-msn-messenger/"]http://ubuntulife.wordpress.com/2009/01/12/pidgin-solucionar-problemas-de-conexion-a-msn-messenger/
[/URL]
De moment per això no cal que actualitzis, pots quedar-te amb la Hardy.

Pau

---

### Post by Curial on 2009-12-18
Moltes gràcies Pablitus, ja em funciona.

M'ha donat un error al fer l'apt-get update, no li deu agradar alguna cosa
d'aquestes línies:
deb [http://ppa.launchpad.net/msn-pecan/ubuntu](http://ppa.launchpad.net/msn-pecan/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/msn-pecan/ubuntu](http://ppa.launchpad.net/msn-pecan/ubuntu) intrepid main

Malgrat això, funciona.

Moltíssimes gràcies i Bon Nadal a tots.

---

### Post by Pablitus on 2009-12-18
Hola Curial!

Si fas servir la Hardy crec que hauries de tenir ```
deb http://ppa.launchpad.net/msn-pecan/ubuntu hardy main
deb-src http://ppa.launchpad.net/msn-pecan/ubuntu hardy main
```

L'error que et dóna potser és perquè no has instal·lat la signatura o la clau del repositori (no sé ben bé com funciona tot això). A la [pàgina del launchpad]("https://edge.launchpad.net/~msn-pecan/+archive/ppa") hi explica com fer-ho, on fica "Technical details about this PPA", i després "Signing key".

Fins ara!

---

