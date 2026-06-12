---
title: "web cam TRUST WB-3320X Sense micròfon a Skype"
date: 2010-10-04
forum: Catalan Team
---

### Post by kukat on 2010-10-04
Bona vesprada a tots!

Després d'estar pegant tombs, no he aconseguit fer anar el so d'aquesta càmera web a l'skype. 

Posant la comanda->
**gstreamer-properties**

Em funcionen tant la sortida d'àudio com la de vídeo als test que hi ha. 

Per a que funcione correctament la càmera de vídeo engege el programa mitjançant aquest comandament:

**LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype**

Hi ha alguna forma de fer alguna cosa semblant amb l'àudio?? (em referisc a una comanda final que carregue el mòdul de vídeo, però també el d'àudio...)

Seria una putada que no funcionara l'àudio de cap forma i cap a Guindows únicament per l'Skype....
:(

Gràcies de totes formes!

EDITO: Estic a Kubuntu Lucid Lynx, i el Kmix detecta la interfície d'àudio de la cam com a USB Device 0x93a:0x2621

---

### Post by kukat on 2010-10-07
Després del problema amb les particions, i d'haver reinsta&#320;lat el Kubuntu, funciona tant la càmera com el micròfon....:confused:

Bé, *Qui no es consola és perquè no vol*, o en castellà: "No hay mal que por bien no venga"...

XD 

aixó si, tinc que executar-lo així:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Salut!

---

