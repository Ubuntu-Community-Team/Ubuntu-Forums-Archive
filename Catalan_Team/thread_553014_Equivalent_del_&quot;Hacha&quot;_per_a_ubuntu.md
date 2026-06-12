---
title: "Equivalent del &quot;Hacha&quot; per a ubuntu?"
date: 2007-09-17
forum: Catalan Team
---

### Post by lo gambusí on 2007-09-17
Salut!

M'interessaria unir diversos vídeos creant-ne un de sol, com tinc entès que fa lo programa Hacha, i no sé què podria usar per a ubuntu.

Alguna idea?

Gràcies!:lolflag:

---

### Post by pespin on 2007-09-17
Aquest enllaç potser t'interessa: [http://bulma.net/body.phtml?nIdNoticia=1450]("http://bulma.net/body.phtml?nIdNoticia=1450")

---

### Post by kukat on 2007-09-17
O aquest altre, jo també necessitava fer coses així, i hem va resultar molt útil aquest enllaç:

[http://www.hachemuda.com/2007/05/30/ejemplos-de-comandos-de-mencoder-para-edicion-de-video-en-gnulinux/](http://www.hachemuda.com/2007/05/30/ejemplos-de-comandos-de-mencoder-para-edicion-de-video-en-gnulinux/)

---

### Post by guillemsola on 2007-09-17
A veure, pel q jo se hacha es un programa per tallar-unir arxius llargs. A linux es fa servir split-cat.

Si el q vols es unir videos sense haver d'editar-los tens ffmpeg. Jo el faig servir i va de conya.

Per unir videos haurien d'estar en format mpg. Si no ho estan els converteixes amb

ffmpeg -i input1.avi -sameq intermediate1.mpg
ffmpeg -i input2.avi -sameq intermediate2.mpg

i despres els uneixes amb cat

cat intermediate1.mpg intermediate2.mpg > 
intermediate_all.mpg

i despres els pots tornar a format avi

ffmpeg -i intermediate_all.mpg -sameq output.avi

A veure si et serveix.

Salut!

---

### Post by CarlesOriol on 2007-09-18
Prova l'avidemux. Va de conya. 
Si vols fer-ho des del terminal mencoder es poderossissim!

---

### Post by lo gambusí on 2007-09-18
Moltes gràcies a tots!

---

### Post by pespin on 2007-09-24
He trobat aquesta entrada que parla d'un programa semblant que hacha per a linux anomenat "hoz". Ho deixo aquí per si a algú li interessa

[http://ubuntuparanovatos.wordpress.com/2007/06/11/que-preferieres-hoz-o-hacha/]("http://ubuntuparanovatos.wordpress.com/2007/06/11/que-preferieres-hoz-o-hacha/")

---

