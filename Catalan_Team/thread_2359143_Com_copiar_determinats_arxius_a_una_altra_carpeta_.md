---
title: "Com copiar determinats arxius a una altra carpeta conservant la jerarquia"
date: 2017-04-21
forum: Catalan Team
---

### Post by orfeu42 on 2017-04-21
Bon dia!

El meu problema és que vull copiar des d'un directori amb múltiples subdirectoris només un determinat tipus d'arxiu a un altre directori però que conservi els directoris originals. Especificant la qüestió:
- Tenc una carpeta a on hi ha múltiples subcarpetes on hi tenc videos i fotos ordenades en subcarpetes (anys/mesos/dia)
- El que voldria fer és agafar només els vídeos que hi ha i copiar-los a una altra carpeta però que en aquesta nova carpeta s'ordenin en carpetes tal qual estaven quan es trobaven mesclades amb les fotos (dies/mesos/any)

La meva primera opció era fer
find directory_origin -type f -name *.EXT -exec mv {} ./directory_destiny \;

però amb això només els copia dins una nova carpeta sense crear les subcarpetes que m'interessen.

És possible fer-ho? M'estalviaria molta feina perquè són molts els arxius a moure i a ordenar :-k

Moltes gràcies!

---

### Post by CarlesOriol on 2017-04-22
Prova això:

sols amb rsync he vist que em copiava sempre tota la estructura i no sols els fitxers que vull. Així que fes:

[FONT=Courier New]cd carpetaorigen
find . -name '*.EXT' | rsync --dry-run -arv --files-from=- carpetaorigen carpetadestí[/FONT]

---

