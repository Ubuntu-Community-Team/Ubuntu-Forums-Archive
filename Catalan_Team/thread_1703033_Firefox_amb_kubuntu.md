---
title: "Firefox amb kubuntu"
date: 2011-03-08
forum: Catalan Team
---

### Post by Lomarc on 2011-03-08
Hola, sóc nou amb Linux i amb Kubuntu, i potser no faig les preguntes correctament però aquí va.
El tema es que tinc el firefox 3.6 instal·lat amb el S.O. Kunbuntu 10.10 i la navegació web va molt, però molt lenta he fet test de velocitat i son correctes..., he provat el navegador rekonq i va perfecte.
Algú te alguna idea que pot passar? jo crec que es alguna cosa de configuració,  però no se...
Gràcies!

---

### Post by orestesmas on 2011-03-08
He vist algun post pels fòrums que podria donar alguna resposta.

Hauries, però, de concretar què vol dir per tu "va lent". Potser va lent en contactar amb la pàgina, però una vegadda contactada la pinta ràpidament? Si és així, la cosa podria estar relacionada amb la resolució DNS i les IPv6. [Alguns suggereixen]("http://ubuntuforums.org/showthread.php?t=1603904") que provis de desactivar les IPv6:

Tecleja "about:config" a la barra d'adreces, accepta la "pèrdua de la garantia", tecleja "ipv6" a la barra de filtre i fes doble clic sobre la instrucció que et surt per tal de canviar-la de "false" a "true". Reinicia el firefox i prova.

---

### Post by Funk'u on 2011-03-08
En cas de tenir-hi molts connectors mira de desinstal·lar-ne algun a veure que passa.



Salut!

---

### Post by Lomarc on 2011-03-09
Perfecte, he desactivat IPv6 i ara funciona normal!! Moltes gracies de veritat!


> **orestesmas said:**
> He vist algun post pels fòrums que podria donar alguna resposta.

Hauries, però, de concretar què vol dir per tu "va lent". Potser va lent en contactar amb la pàgina, però una vegadda contactada la pinta ràpidament? Si és així, la cosa podria estar relacionada amb la resolució DNS i les IPv6. [Alguns suggereixen]("http://ubuntuforums.org/showthread.php?t=1603904") que provis de desactivar les IPv6:

Tecleja "about:config" a la barra d'adreces, accepta la "pèrdua de la garantia", tecleja "ipv6" a la barra de filtre i fes doble clic sobre la instrucció que et surt per tal de canviar-la de "false" a "true". Reinicia el firefox i prova.

---

### Post by Lomarc on 2011-03-09
No tenia connectors instalats, tot just acabava d'instal·lar el firefox. El problema era de IPv6, l'he desactivat i perfecte!
Gràcies per respondre!

> **Funk'u said:**
> En cas de tenir-hi molts connectors mira de desinstal·lar-ne algun a veure que passa.



Salut!

---

### Post by wgarcia on 2011-03-09
Posa-li sisplau "Solved" al fil (usant "Thread tools" que pots veure a dalt del fil) perquè en quedi referència per futurs usuaris.

---

