---
title: "Problemes amb el so en els videos flash"
date: 2010-11-28
forum: Catalan Team
---

### Post by albertdelleida on 2010-11-28
Hola a totes,

us escric perquè de des de fa uns dies no puc sentir el so en els videos flash (youtube, jocs flash...). 

Tinc l'Ubuntu 10.04 i mai havia tingut cap mena de problema d'aquest tipus. Crec que aquest problema ha aparegut després de fer una actualització des del gestor d'actualitzacions. He desinstal·lat l'Adobe Flash i l'he tornat a instal·lar però res de res. Em podríeu donar un cop de mà?

Moltes gràcies

Albert

---

### Post by wgarcia on 2010-11-29
Un suggeriment que a vegades m'ho arreglat a mi: Tens instal·lat el control de volum de so de pulseaudio? 

sudo apt-get install pavucontrol

Un cop instal·lat obre'l des del menú "So i vídeo", engega el Flash, i busca'l a les diferents opcions de volum de so que tens al control de volum a veure si té el volum donat.

---

### Post by albertdelleida on 2010-11-29
Funciona :P

Acabo de provar-ho i he canviat el "ALSA plug-in [plugin-container]: ALSA Playback on" de sortida HDMI a Àudio Intern i ja funciona.

Moltíssimes gràcies!

---

