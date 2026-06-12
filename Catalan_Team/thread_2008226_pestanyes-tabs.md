---
title: "pestanyes-tabs"
date: 2012-06-22
forum: Catalan Team
---

### Post by josep-maria on 2012-06-22
Tinc l'ubuntu 12-04. Des de un dels darrers canvis de versió de l'ubuntu que em passa això: quan obro una segona o tercera pestanya del firefox, i han passat uns segons o minuts, es tanca una de les pestanyes i s'obre una altra finestra amb el mateix contingut de la pestanya desapareguda. És a dir, és com si jo hagués tancat una pestanya i hagués tornat a engegar el navegador. Uns minuts després torna a passar igual, però amb una altra pestanya. És molt emprenyador que el sistema em canviï les coses que no vull canviar. Com es pot arreglar?

---

### Post by wgarcia on 2012-06-22
Això no sembla ser responsabilitat dels canvis de versió de firefox, i menys d'Ubuntu, sinó algun problema de configuració del Firefox o d'alguna extensió. 

Per començar a esbrinar què pot estar causant el problema jo provaria d'anar deshabilitant una per una les extensions que tinguis instal·lades i veure si es reprodueix el problema. 

Si després de no tenir cap extensió habilitada es continua reproduint, provaria de canviar de perfil, perquè no sigui alguna cosa desconfigurada al perfil actual, però això s'ha de fer amb molt de cura perquè si es perd el perfil actual es perden totes les dades, com ara els favorits, claus desades, etc. Però si fa falta fer-ho es pot mirar de fer sense perdre dades, tot i que primer convé descartar que no sigui alguna extensió que està fent la guixa.

---

### Post by josep-maria on 2012-06-23
Com que em passa a dos pc (sense haver fet jo cap canvi) suposava que era per culpa d'una actualització i que li passava a tothom. Per això m'he aguantat tant de temps, però ara veig que només em passa a mi.

Com es fa això que dius de les extensions i del perfil? He mirat tots els menús del firefox i no he trobat res que s'assembli.

---

### Post by josep-maria on 2012-06-23
Em sembla que ja he trobat això de les extensions. Són a:
eines > complements > extensions. N'he trobat dues:
'global menu bar integrations' i 'ubuntu firefox modifications'. No goso esborrar res perquè no sé per a què serveixen.

---

### Post by wgarcia on 2012-06-24
Si sols tens aquestes dues no deu ser això, perquè aquestes venen per defecte al Firefox de l'Ubuntu. 

Una altra prova que pots fer és entrar al compte d'invitat, si el tens, i mirar si també es reprodueix el problema aquí.

---

### Post by josep-maria on 2012-06-30
He fet proves i he trobat que si faig: 

edita > preferències > pestanyes > obre les noves finestres millor en pestanyes = no

i: avisa'm quan en obrir moltes pestanyes pugui alentir-se el firefox = no

Ara no va sempre bé però ha millorat molt. Abans era un caos insuportable. Molt agraït.

---

