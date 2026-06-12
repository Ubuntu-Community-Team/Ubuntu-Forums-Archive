---
title: "Sense so al Firefox"
date: 2010-11-15
forum: Catalan Team
---

### Post by CarlesF on 2010-11-15
Bones!

Des del setembre que tinc instal·lat el Kubuntu 10.04 però no he aconseguit tenir so amb el Firefox. Puc sentir mp3 amb l'Amarok. Puc veure i sentir vídeos amb Dragon Player, però amb el MPlayer només puc veure'ls i no sentir-los.

He mirat per tota la xarxa, he mirat això del volum PCM, he instal·lat i desinstal·lat connectors, controladors i no se que més... però vaja, soc nou amb això i no se pas que em puc deixar...

Help!

---

### Post by epileg on 2010-11-16
¿Has provat d'anar a la icona del volum del so, fer clic a «preferències del so...» i anar a la pestanya «Aplicacions» a veure si tens el volum baix o directament en silenci?

---

### Post by CarlesF on 2010-11-16
Gràcies **epileg**, però això hagués estat massa fàcil... :(

Carles.

---

### Post by wgarcia on 2010-11-17
Pots instal·lar "pavucontrol" i despres obir aquesta aplicació des d' Aplicacions -> So i vídeo. Després engegues el Firefox i li intentes fer reproduir algun so, i dins dels controls que tens en pavucontrol mires si hi ha algun volum que no estigui donat. 

pavucontrol és un control de volum del servidor Pulseaudio que s'encarrega d'actuar d'intermediari entre les aplicacions i el sistema de so.

---

### Post by CarlesF on 2010-11-19
Però jo no tinc el PulseAudio, tinc el Alsa. Em pensava que amb Kubuntu no s'havia d'utilitzar el PulseAudio... M'instalo el PuseAudio?

---

### Post by wgarcia on 2010-11-19
Jo crec que el pulseaudio està instal·lat per defecte i penso que si no els tens és perquè l'has desintal·lat. No és un sistema d'àudio alternatiu a Alsa sinó un intermediari entre el hardware d'àudio (la targeta de so) i les aplicacions que volen generar àudio. Per tant perfectament pots tenir el pulseaudio i estar fer servint Alsa. 

Prova de fer des d'una terminal:

ps -ef | grep pulseaudio

i mostra que et surt, això permetrà veure si tens el pulseaudio corrent.

---

### Post by CarlesF on 2010-11-19
He instal·lat el PulseAudio i el  "pavucontrol" i tots els volums estan alts.

He fet:
ps -ef | grep pulseaudio

i em posa:
ERROR: Garbage option.

Segueix sense xutar...

---

### Post by wgarcia on 2010-11-20
M'estranya el que et dóna la comanda "ps -ef | grep pulseaudio", però bé, deixe'm-lo estar perquè era sols per comprovar si tenies el pulseaudio instal·lat i executant, i donat el que veus amb el "pavucontrol" sembla que sí.

Ara el que pots fer és engegar el firefox, posar alguna pàgina que hauria de generar so, anar al "pavucontrol" i mirar en les diferents pestanyes si veus l'aplicació i els nivells de volum associats, a veure si hi ha algun control que estigui posat perquè no hi hagi so.

---

### Post by CarlesF on 2010-11-20
[SIZE=4][COLOR=DarkGreen]MOLTES GRÀCIES **WGARCIA**!!!![/COLOR][/SIZE]

Ho he pogut solucionar fent el que deies i posant al "pavucontrol" el so intern "inactiu"... IMPRESSIONANT!!! VISCAAAA!!!

Oh, de veritat que ho necessitava arreglar de totes totes!!!! MOLTES GRÀCIES!!!

---

### Post by wgarcia on 2010-11-21
Si te'n recordes ves a "Thread tools" i posa-li "Solved" al fil perquè en quedi constància.

---

