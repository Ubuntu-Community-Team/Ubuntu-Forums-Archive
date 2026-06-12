---
title: "[SOLVED] Problemes reproducció video"
date: 2007-10-23
forum: Catalan Team
---

### Post by nickpage on 2007-10-23
Hola companys,

continuo tenint problemes amb la nova instal·lació neta de Gutsy, i ara es la de reproducció de video.

He instal·lat el mplayer, tal com tenia al Feisty ja que amb el reproductor per defecte me va a empentes, en canvi amb el mplayer anava tot molt fi.

El problema es que amb el mplayer no me va gairebé ja que me surt una pantalla super allargada i molt borrós. 

Tota la ajuda serà agraïda.

Salut

---

### Post by RainCT on 2007-10-23
Hola,

Pots provar a veure si s'arregla insta&#320;lant el paquet «ubuntu-restricted-extras» des del Synaptic.

Salut

---

### Post by nickpage on 2007-10-23
Doncs això continua igual, la reproducció no va gaire fina. Crec que es un problema del mplayer amb el Gutsy.

---

### Post by Kosimo on 2007-10-23
Has probat desactivant els efectes d'escriptori?
Fes click amb el botó dret del ratolí sobre l'escriptori i escull canviar fons d'escriptori allà veuras la pestanya d'efectes.
Desactiva'ls, fes-nos saber si veus millor els videos

---

### Post by Satboy on 2007-10-25
Hola,
 Sempre ets a temps de provar el Videolan o VLC, per mí és un dels milors reproductors que hi ha.

 Aquí en tens més informació des del seu web:

 [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

 Siau! ;-)

 P.D.La interfície és totalment en català.

---

### Post by nickpage on 2007-10-25
Hola Satboy,

doncs aquesta nit provaré el VLC.

el mplayer m'ha funcionat be després de varies reinstalacions, però encara tinc un problema, resulta que quan poso en marxa un video el mplayer me mostra una pantalla molt allargada, només puc redimensionarla a ma, ja que les opcions de pantalla completa o tamany original, etc... no funcionen  o fan que la finestra de visualització desaparegui.
De tota manera la reproducció es igual que bona que quan tenia el Feisty, fins i tot funciona molt be amb l'efecte de cub, encara que es un pal tenir que redimensionar a ma la finestra.

---

### Post by Satboy on 2007-10-25
Hola,
 Doncs prova el VLC (Videolan) ja veuràs com no te'n penediràs!

 Siau!;-)

 P.D.El pots instal.lar des del **Synaptic**.

---

### Post by nickpage on 2007-10-25
VLC funciona de conya!!!!!:popcorn:

Gràcies company

---

### Post by Satboy on 2007-10-25
Nickpage,
 Em deus una birra!! :biggrin::biggrin::biggrin::biggrin:

 Siau! ;-)

---

### Post by CarlesOriol on 2007-10-25
Per què no et funcionava el gstreamer? (amb el frontend totem)

Jo ho puc veure tot.

---

### Post by nickpage on 2007-10-25
El reproductor que hi ha per defecte al ubuntu anava a empentes, molt desagradable per seguir qualsevol video.

---

### Post by CarlesOriol on 2007-10-25
No debies tenir-lo ben configurat. ( o el reproductor o el sistema o la targeta gràfica)

---

### Post by jodufi on 2007-10-26
El navegador per defecte, el Totem, acostuma a agafar qualsevol vídeo un cop instal·lat el «ubuntu-restricted-extras».

---

### Post by jerec on 2007-10-27
Jo penso que ni VLC ni Totem ni res de res, el mplayer es la bomba.!!! desde la consola pots fer realment virgueries.
Pero entre gust no hi has res escrit.

Tambe penso que es problema de configuració, Quin driver de video tens posat al mplayer (gmplayer, preferencies, video) prova de fer servir el xv.

Mira de passada que tinguis el driver de la teva tarja ben configurat i acceleracio 3D.

# glxinfo | grep direct
has d'obtenir:
# direct rendering: Yes

---

### Post by CarlesOriol on 2007-10-27
A mi també m'agrada força l'mplayer i el seu complement mencoder és absolutament genial.

Però hem de tiner present els més teclaires que la majoria dels nous companys de viatge i els que vindran d'ara endavant son clicaires i primer voldran fer les coses a cop de clic... si s'hi enganxen ja descobriran tot el nostre univers.

---

### Post by jerec on 2007-10-27
Tens rao, però tambe feia referencia al gui del mplayer, el gMplayer. 
Tambe es cert que potser no te els menus tant acurats com el totem, kaffeine, VLC i demes, pero es menja tots els formats.

Per els amants del ASCII, proveu això i aparteu-vos una mica de la pantalla:

# mplayer -vo aa PeliculaQueVolgueu.avi

---

### Post by guillemsola on 2007-10-28
Jo he provat amb el gutsy i el reproductor que més em tira és el mplayer. Ho he provat amb un vídeo de qualitat i el VLC i el totem anaven a trompicons.

Salut!

---

### Post by CarlesOriol on 2007-10-29
Tot depen del que vulguis fer. Per exemple sobre un suport n una xarxa lenta (wifi 11 o similar) veuras que amb l'mplayer és gairebé impossible de veure una película ja que gestiona els buffers molt malament de forma predeterminada. En canvi amb un totem no tindras cap problema.

Sobre els trompicons... hauries de ser més concret, per que no és veritat que el totem vagi a salts en un video d'alta definició. Pot ser que hi hagi algun format concret o vídeo concret en el que hagis tingut problemes i llavors hauries d'especificar-ho o pot ser és un problema amb alguna configuració de maquinari específica o també potser que et passi a tu o és genèric.

---

