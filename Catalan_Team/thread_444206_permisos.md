---
title: "permisos"
date: 2007-05-15
forum: Catalan Team
---

### Post by bratac on 2007-05-15
Bones, 

tinc dos dubes sobre permisos a ubuntu.

1.- Tinc uns documents que vull esborrar però no puc per que el seu propietari és en root.

2.- Per acabar la instal·lació d'un joc he de copiar i enganxar uns fitxers en una carpeta situada a:
[INDENT][/INDENT]/usr/share/games/
      Com ho puc fer per modificar els permisos, posar-hi els fixers i tornar-los a deixar com estaven? El propietari també és en root.

Gràcies, 

alfred

---

### Post by CarlesOriol on 2007-05-15
sudo chown alfred:alfred nomdelfitxer

---

### Post by marcoil on 2007-05-15
En general, per fer qualsevol cosa com si fossis l'usuari *root*, has d'anar a la línia de comandes i emprar **sudo**. Així, per exemple, per esborrar un directori /tmp/dir001 que és del *root* pots fer

```
sudo rm -rf /tmp/dir001
```

(el -r és per poder borrar, recursivament, directoris). Per copiar els arxius a /usr/share/games has de fer

```
sudo cp -r arxius /usr/share/games
```

L'exemple que ha posat en CarlesOriol te servirà per canviar qualsevol fitxer del root a l'usuari alfred.

---

### Post by bratac on 2007-05-20
Més preguntes, 

vull passar uns fitxers a la carpeta /usr/share/color/icc però no puc per que no tinc permisos, no vull alterar-ne els permisos (o almenys si ho faig, després ho vull deixar tal com estava) els fitxers els tinc a l'escriptori. Com m'ho faig?

fins ara,

---

### Post by CarlesOriol on 2007-05-20
És importat fer cada pregunta en un thread diferenet. Per que això no es converteixi en un poti poti.

pots copiar fent sudo cp arxiuacopiar /usr/share/color/icc/

o bé obrir un nautilus amb sudo (sudo nautilus). A mi m'agrada molt de canviar el fons del nautilus i del gedit a color vermell quan els engego en sudo. Així amb un cop d'ull ja veus que pots fer grans destrosses.

---

