---
title: "Convertir ogm --&gt; avi"
date: 2007-09-30
forum: Catalan Team
---

### Post by nickpage on 2007-09-30
Hola companys,

tinc uns arxius en format ogm però el meu reproductor no els pot reproduir, encara que si ho puc fer al PC.
Hi ha alguna forma de convertir-los en format avi o similar que si els puc veure al meu reproductor.

Gràcies

---

### Post by albertg on 2007-10-01
Hola,

L'Avidemux és un editor de vídeo que permet obrir/desar en diversos formats, potser et serveix.

Una altra opció és el mencoder. Si només vols canviar el contenidor del fitxer (sense canviar el codec de vídeo i àudio) pots fer-ho amb l'ordre:

```
mencoder fitxer.ogm -o fitxer.avi -oac copy -ovc copy
```

---

