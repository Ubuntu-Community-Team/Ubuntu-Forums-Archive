---
title: "Compressió Nautilus dona errors en caracters noms fitxer"
date: 2010-06-05
forum: Catalan Team
---

### Post by somhi on 2010-06-05
Des del Nautilus quan vull comprimir una sèrie d'arxius que contenen accents amb l'opció "Comprimeix" del menú contextual, si elegeixo format zip o rar, aquests caràcters amb accents apareixen mal codificats quan ho descomprimeixo des de windows. Des de linux sempre funciona bé.

En la 9.04 només em passava amb els zip, ara amb lucid em passa també amb els rar.  En canvi he provat 7z i desde windows ho descomprimeix bé.

Alguna solució?

Gràcies.
Somhi

---

### Post by wgarcia on 2010-06-05
Jo diria que el que passa és que el nautilus codifica els títols amb el sistema UTF-8 i el Windows amb algun altre sistema. Per tant la solució seria codificar els títols amb els sistema que utilitza Windows, però en aquest cas es veuria malament a l'Ubuntu. 

Potser la millor solució és no utilitzar accents i altres caràcters especials als títols dels fitxers, per no complicar-se amb aquest tema.

---

### Post by somhi on 2010-06-12
Gràcies per la resposta, però això s'ha de poder sol·lucionar d'alguna forma, no ens podem aconformar a no poder posar accents...

Somhi

---

### Post by wgarcia on 2010-06-13
Si fas servir dos sistemes operatius que fan servir sistemes de caràcters diferents, doncs sembla difícil que mostrin els caràcters d'una altra manera, però és clar que es pot solucionar, i els sistema que utilitza l'Ubuntu (UTF-8) suposo que es pot imposar en altres sistemes operatius.

---

