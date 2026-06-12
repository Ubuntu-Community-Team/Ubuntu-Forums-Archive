---
title: "KDEnlive peta a mig renderitzar"
date: 2009-11-26
forum: Catalan Team
---

### Post by LitusMayol on 2009-11-26
Bona tarda familia!

Avui estava muntant un video quan de sobte el Kdenlive s'ha dedicat a petar. 

Això és el que em diu la consola
```
//STARTING RENDERING:  true , false , "/usr/bin/melt" , "hdv_1080_50i" , "avformat" , "-" , "consumer:/tmp/kde-root/kdenlivea15104.mlt" , "/home/litus/Escriptori/Cuento de navidad/Cuento de Navidad.avi" , () , ("f=avi", "vcodec=dvvideo", "pix_fmt=yuv420p", "acodec=pcm_s16le", "s=720x576", "profile=dv_pal") , -1 , -1 
kdeinit4: preparing to launch /usr/bin/knotify4
Started render process:  "/usr/bin/melt"   "consumer:/tmp/kde-root/kdenlivea15104.mlt profile=hdv_1080_50i -consumer avformat:/home/litus/Escriptori/Cuento de navidad/Cuento de Navidad.avi progress=1 f=avi vcodec=dvvideo pix_fmt=yuv420p acodec=pcm_s16le s=720x576 profile=dv_pal" 

```

i quan porta ben bé una hora:
```
Rendering of  "/home/litus/Escriptori/Cuento de navidad/Cuento de Navidad.avi"  aborted, resulting video will probably be corrupted. 
```

Total que el video queda renderitzat fins allà on arribat (un 70ipoc%).

Agú sap com solucionar-ho o què pot ser? 
Gràcies!

---

### Post by orestesmas on 2009-11-27
Quina versió del kdenlive tens? Com l'has instal·lat (repositoris oficials, no oficials, compilat tu mateix...)?

Més concretament, sospito del "Melt", un dels subprogrames que fa servir Kdenlive, concretament per renderitzar. Obre un terminal i posa-hi:
```

melt -version

```

Si per casualitat tens la versió 0.4.7 del melt no anem bé. És una versió de desenvolupament amb molts errors i petades.

---

### Post by akyra on 2009-11-28
Jo en breu també haig de renderitzar amb el kdenlive (primer haig de solucionar un problema amb els clips de titol), ja et diré com en funciona.

Salutacions

---

### Post by LitusMayol on 2009-12-01
Bones!

Gràcies per sortir al rescat! He instal·lat el dels repositoris, que segons el Synaptic és el  **KDEnlive 0.7.5**. Pel que fa al Melt, la consola em respon això:
```
litus@mayolets:~$ melt -version
MLT melt 0.4.5
Copyright (C) 2002-2009 Ushodaya Enterprises Limited
<http://www.mltframework.org/>
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
litus@mayolets:~$ 


```

És bo que no sigui el 0.4.7?

---

### Post by orestesmas on 2009-12-01
JO vaig provar el 0.4.7 i no anava bé. A banda de petar abans d'acabar el renderitzat, els vídeos amb format original FLV (flash) no els reproduïa bé.

Ara ho tinc funcionant amb la 0.4.6 (compilada a mà), i va com una seda. No et sabria dir res de la 0.4.5, però si és la versió que ve als repositoris, suposo que algú l'haurà provada abans de pujar-la.

---

### Post by akyra on 2009-12-02
Hola,

Jo ahir vaig renderitzar un video, i no em va donar cap error i va trigar uns 35 minuts.

Adeu.

---

