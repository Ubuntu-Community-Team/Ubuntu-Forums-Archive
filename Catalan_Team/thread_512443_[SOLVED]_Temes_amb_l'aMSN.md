---
title: "[SOLVED] Temes amb l'aMSN"
date: 2007-07-29
forum: Catalan Team
---

### Post by pablinsfc on 2007-07-29
Bones companys!! Segueixo amb la meu aterratge al món ubuntu i cada cop n'estic més content. Però m'he trobat amb una questió, suposo sobre permisos d'usuari, i és que a l'hora de personalitzar els temes de l'aMSN, per instarl·lar-los has de descomprimir la carpeta i copiar-la a /usr/share/amsn/plugins. Al fer-ho em diu que no tinc premís per escriu-re a aquesta carpeta. En principi jo com a usuari tinc tots els "privilegis d'usuari" activats, per tant no sé a què es deu.

Merci per endavant!

Pau.

---

### Post by papapep on 2007-07-29
Per molt que tinguis "tots" els permisos, com tu dius, no ho estàs fent amb els drets suficients, ja que tots els directoris que pengen de /usr/share són propietat de l'usuari i grup **root**. La resta d'usuaris només poden llistar-los o llegir-los i, per aixó mateix, no t'hi deixa escriure.
Els fitxers dins aquests directoris només són de lectura.

L'únic que has de fer, és teclejar en un terminal:

```
sudo mv /directori_descomprimit/*   /usr/share/amsn/plugins/
```

---

### Post by pablinsfc on 2007-07-29
Merci de nou papapep!! M'ha anat molt bé, ja està instal·lat.

Saps d'alguna pàgina on pugui aprendre aquestes quatre ordres bàsiques i la sintaxis per moure, esborrar, obrir fixers, navegar entre les carpetes, etc des del terminal??

Així no us emprenyaré tant... 

Salut!

Pau.

---

### Post by papapep on 2007-07-29
[http://tinyurl.com/3drv2e](http://tinyurl.com/3drv2e) 

;-)

---

### Post by pablinsfc on 2007-07-29
Genial! Segur que m'anirà de meravella,

Gràcies!

---

