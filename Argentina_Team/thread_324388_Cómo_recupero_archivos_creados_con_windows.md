---
title: "Cómo recupero archivos creados con windows"
date: 2006-12-23
forum: Argentina Team
---

### Post by Trillian on 2006-12-23
Buenas!
Ya tenía pensado pasarme a Ubuntu, combinándolo con el XP por comodidad, pero hace un par de días mi XP decidió dejar de funcionar. En vista de que no consigo repararlo pero aún tengo archivos en el disco duro que necesito recuperar, pensé en emplear el Desktop CD de Ubuntu para poder correr el sistema operativo, recuperarlos y tostar unos cd's antes de formatear todo y hacer las particiones.
Resulta que efectivamente puedo emplear Ubuntu pero no consigo acceder a los archivos que estaban previamente en el disco duro, creados desde winXP.
¿Alguna idea de cómo llego a ellos?
Muchas gracias!

---

### Post by Nemesis Teufel on 2006-12-23
Tenes que montar el disco o instalando ubuntu te lo hace solo.

Para el LiveCD **_CREO_** que es esto:

```
sudo mkdir /media/miviejainstalacion
```
(nombra esto asi no te confundis el LiveCD directorio y el HD directorio)
```
sudo mount /dev/hda1 /media/miviejainstalacion
```
(donde /dev/hda1 es el camino al disco duro)  


Corroboren los que saben.

---

