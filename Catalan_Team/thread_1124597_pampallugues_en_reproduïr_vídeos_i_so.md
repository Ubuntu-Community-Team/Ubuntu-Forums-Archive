---
title: "pampallugues en reproduïr vídeos i so"
date: 2009-04-13
forum: Catalan Team
---

### Post by joana ebrenca on 2009-04-13
Hola! Em dic Joana i fa poc que faig servir Ubuntu i m'he adonat que en reproduïr vídeos i so la pantalla em fa pampallugues.

Algú em podria ajudar?

La meva targeta gràfica és una ATI Radeon Express 1250 i vaig amb l'Ubuntu 8.10...

Moltes gràcies ;)

Joana

---

### Post by SiscoGarcia on 2009-04-13
Benvinguda Joana,

Abans de res, si no ho has fet ja, crec que hauries de mirar-te el [fil iniciàtic]("http://ubuntuforums.org/showthread.php?t=599965"), allà trobaràs informació sobre com moure't pel fòrum i veuràs que ens cal més informació; per exemple, quin format de vídeos i d'àudio és el que et dóna problemes? quin programa fas anar? Com més informació donis més fàcil serà ajudar-te.

D'altra banda, passa't pel [fil de benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") i explica'ns coses ;)

Fins aviat!

---

### Post by joana ebrenca on 2009-04-13
hehe tens raó...

me passa tant amb el reproductor de pel·lícules com amb el VLC media player, que són els dos que faig servir habitualment. Amb el rhythmbox no em passa suposo que perquè no té pantalla on ''veure'' res.

els formats que intento reproduïr són dvd comercials, cançons en mp3 i alguna en .ogg etc. en resum, em passa amb tot allò que intento reproduïr de música o vídeo i amb tots els programes que ho he intentat.

gràcies

---

### Post by torracastanyes on 2009-04-13
Bé ,avans de res, els sospitosos habituals: Mira aquí si et falta res:

[http://www.guia-ubuntu.org/index.php?title=Instalar_codecs_multimedia](http://www.guia-ubuntu.org/index.php?title=Instalar_codecs_multimedia)

I ara una pregunta capciosa: Quina edat té el teu monitor?

---

### Post by tanreb20 on 2009-04-13
Alt + F2 -> Escriu gstreamer-properties.

A la pestanya Vídeo / Sortida -> Marca X window sysrtem (X11/XShm/Xv)

I donar a acceptar.

Si no funciona inmediatament, reincia la sessió grafica (ctrl - alt - backspace(pero guarda toto el q estiguis fent avans)

Prova si no funciona tamb les altres opcions, a vere si alguna et funciona.

---

### Post by CarlesOriol on 2009-04-14
Prova també sense els efectes d'escriptori Sistema > Prefer'encies > Aparença > Efectes visuals -> Cap.

Quin controlador uses el lliure o el privatiu? 
Sistema>Administracio'>controladors de maquinari

---

### Post by joana ebrenca on 2009-04-16
Ei!! moltes gràcies als tres :D

M'ha funcionat la idea de CarlesOriol, eren els efectes de l'escriptori.

Salut!

---

### Post by joseap on 2009-04-23
Hola Joana, m'alegro que hagis solucionat el problema.

A mi em pasaba y vaig llegir a ubuntuforums(angles) que les targetes grafiques AT HD y el compiz no eren gaire amics.

Yo vaig anar a la pagina de ati y vaig baixar l'ultim paquet de drivers per la meva targeta grafica(hd3600). Com que tenen un paquet específic per linux es molt facil d'instalar(amb instal.lador gràfic y ati control center y tot!!).

Un cop actualitzat el driver, puc utilitzar el compiz y ya no fa pampagulles quan veig pelis.

Nota: crec que aquest bug només existia en intrepid ibex

Salut!

---

