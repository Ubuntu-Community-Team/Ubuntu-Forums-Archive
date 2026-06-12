---
title: "Problemes de so Ubuntu 9.10"
date: 2009-11-23
forum: Catalan Team
---

### Post by Leirdalag on 2009-11-23
Hola!
Ara que per fi tinc instal·lat Ubuntu al meu ordinador i tot funciona correctament, m'he adonat d'una cosa. En obrir qualsevol arxiu de so, els altaveus fan un espetec molt molest abans d'iniciar la reprodució, a algú se li acudeix a que pot ser degut?
Segons m'informa sysinfo en quant a so tinc:
nVidia Corporation MCP61 High Definition Audio (rev a2)
Subsystem: Hewlett-Packard Company Devide 2a6d
...que ara que ho veig tampoc se si hauria de ser això...8-[

---

### Post by guillemsola on 2009-11-24
Ves que no sigui culpa de pulseaudio!

si vols prova a treure'l i reinicia la sessió

sudo apt-get purge pulseaudio

si vols després el tornes a posar amb "apt-get install"

---

### Post by guillemsola on 2009-11-24
per casualitat he trobat un que li pasava el mateix i era pq la tarja de so hibernava

[http://pcollaog.firefox.cl/2009/11/09/reparar-el-molesto-ruido-que-genera-pulseaudio-en-ubuntu-karmic/](http://pcollaog.firefox.cl/2009/11/09/reparar-el-molesto-ruido-que-genera-pulseaudio-en-ubuntu-karmic/)

---

### Post by Leirdalag on 2009-11-28
Gràcies pel consell angrychai!
Crec que el problema deu ser aquest que dius i seguiré investigant,  però no he pogut solucionar-lo seguint les instruccions de l'enllaç. A algú més li passa el mateix?
P.D: Perdó per haver trigat a contestar però he tingut problemes de connexió aquests dies.

---

### Post by ifanlo on 2009-11-29
Jo ja flipo, però en el meu cas, aleatòriament, reconeix o no la tarja de so...
Passo d'investigar, no tinc temps ni ganes, i total... pel que hi ha per sentir!  :-D
Però no deixa de ser interessant.

---

