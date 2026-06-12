---
title: "fer el format a les memòries flash"
date: 2018-08-07
forum: Catalan Team
---

### Post by josep-maria on 2018-08-07
Com es fa per donar format a una memòria flash?

De cop i volta, una memòria flash no em deixa escriure-hi res. Diu que és només de lectura. Però ha anat bé gairebé dos anys. He volgut formatejar-la, però no he trobat cap menú per fer-ho. Tinc l'ubuntu 16.04 xerus, versió mate 1.12.1, linux 4.4.0. No he trobat cap cas semblant a aquest fòrum.

---

### Post by wgarcia on 2018-08-09
Sí, és empipador això de "sols lectura", no sé perquè passa, però jo ho he vist més d'un cop.

Als sistemes operatius (Gnome o Unity) que fan servir el navegador de fitxers "Nautilus" a vegades he vist que s'arregla amb les ordre següents:

```
rm -fr .local/share/nautilus
killall nautilus
```

és a dir eliminant la carpeta de configuració del nautilus (es recrea automàticament quan es reinicia) i reiniciant el nautilus.

Però el sistema MATE em sembla que no fa servir el nautilus sinó que porta un navegador de fitxers propi que es diu "Caja", per tant crec que això de dalt no arreglarà res.

Si vols formatejar-la i no et preocupa perdre les dades que hi ha, ho pots fer amb l'aplicació "gparted". Compte quan l'obris perquè et mostrarà tots els discos que hi vegi, fins i tot el disc dur. Has d'identificar el volum de la memòria flash, compte de no formatejar el que no vulguis. Hi ha un menú per formatejar en diversos formats. Si vols intercanviar amb windows s'ha de formatejar en format fat32 o ntfs.

---

