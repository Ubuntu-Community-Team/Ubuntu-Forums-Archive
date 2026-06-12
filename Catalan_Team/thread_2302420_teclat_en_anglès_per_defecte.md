---
title: "teclat en anglès per defecte"
date: 2015-11-10
forum: Catalan Team
---

### Post by jinglada on 2015-11-10
Des de fa més d'un any, a l'arrencada, se'm posava el teclat en anglès per defecte, malgrat a la barra de menús es llegia "Es"; manualment clicava "Es Català (Espanya, L amb punt volat)" cada cop que engegava l'ordenador, o sigui que em passava el mateix que als fils:

[teclat en anglès per defecte Ubuntu 14.04]("http://ubuntuforums.org/showthread.php?t=2247657&highlight=teclat+en+angl%E8s+defecte+Ubuntu")
[teclat en anglès per defecte Ubuntu 14.04]("http://ubuntuforums.org/showthread.php?t=2222159&highlight=teclat+en+angl%E8s+defecte+Ubuntu")
[teclat en anglès per defecte Ubuntu 13.10]("http://ubuntuforums.org/showthread.php?t=2198162&highlight=teclat+en+angl%E8s+defecte+Ubuntu")

i ho he solucionat aplicant la 2a solució de [http://que-cosas.blogspot.com.es/2014/03/poner-el-teclado-en-espanol-en-ubuntu.html](http://que-cosas.blogspot.com.es/2014/03/poner-el-teclado-en-espanol-en-ubuntu.html), però canviant l'ordre a: 
setxkbmap -layout 'ca,es' -model pc105 o sigui "Aplicacions d'inici", "Afegeix", Nom: "Teclat català", Ordre:"setxkbmap -layout 'ca,es' -model pc105" i Comentari: "Força teclat català", tot sense les cometes, és clar.

Ho comunico per si pot ajudar a algú que es trobi en la mateixa situació. He fet un fil nou perquè els tres indicats diu que estan tancats.

---

