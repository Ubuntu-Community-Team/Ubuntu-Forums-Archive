---
title: "[SOLVED] Problemes amb permisos?"
date: 2007-09-24
forum: Catalan Team
---

### Post by kukat on 2007-09-24
No es un problema greu, ja que no ocurreix res, però hem surt aquest missatje al posar l'usuari i el password:

"S'ignorarà el fitxer $HOME/.dmrc. Això evita que es desin la sessió predeterminada i la llengua. El direcotri d'usuari &HOME hauria de ser propietat de l'Usuari i no permetre l'escriptura d'altres usuaris"

Jo havia pensat de fer alguna cosa amb chmod, però no estic segur i no vullc estropejar-ho mes.

Gràcies a tots!!

---

### Post by papapep on 2007-09-24
Si ens passes el que et surt al terminal quan hi poses:

```
ls -la /home
```

Podrem veure si tens algun problema real de permisos.

---

### Post by kukat on 2007-09-24
Hem surt això:


kukat@kukat:~$ ls -la /home
total 12
drwxrwxrwx  3 root  root  4096 2007-06-13 02:10 .
drwxr-xr-x 21 root  root  4096 2007-06-13 08:47 ..
drwxrwxr-x 45 kukat kukat 4096 2007-09-24 18:12 kukat

???

He donat el chmod, i tot açó, però no se el que hi ha que fer en  un cas així, per què no sé que es el que passa...

Gràcies

---

### Post by papapep on 2007-09-24
> He donat el chmod, i tot açó

Què significa això??? No t'entenc.

Per cert, l'ordre que t'he indicat no estava bé del tot:

```
ls -la /home/kukat
```

També podries provar posant correctament els permisos de la teva carpeta d'usuari:

```
chmod 700 /home/kukat
```

I després posant bé els permisos del .dmrc

```
chmod 644 /home/kukat/.dmrc
```

---

### Post by kukat on 2007-09-24
Gràcies!! ja funciona. He fet els dos chmod que m'has dit i ja no hem diu res quan inicie. 

El que hem referia amb "he donat el chmod" es que he estudiat alguna cosa a clase, ja que hem donat alguns comandaments i algunes coses, però no sabia que fer en aquest cas.

Gràcies, altra vegada.

---

### Post by papapep on 2007-09-24
Aaaahhhh! Era això! :-D

Au, m'alegro que et funcioni.

---

### Post by ernestux on 2007-12-07
Hola a tothom,

La solució del sabi papapep a mi també m'ha funcionat, però hi ha alguna sorpresa: he fet els 2 passos indicats pel papapep 1)sudo  chmod 700 /home/merlot  i 2)sudo chmod 644 /home/merlot/.dmrc .
He reiniciat l'ordinador i ja se m'ha obert bé el meu usuari,però mirant els permisos veig que el fitxer  /home/merlot/.dmrc té els permisos 600 i no el que li havia donat anteriorment a través de la terminal (segur). Com pot ser ? 

Seguim amb permisos de fitxers i directoris : 
**a.** els /home/usuaris  han de tenir el permisos 700 ? . Jo tinc un usuari amb 755 -no sé perquè, però funciona aparentment bé.
**b.** Les carpetes ocultes (ex. .gconf  , .gnome , .local ..)  dins de cada usuari han de tenir els permisos 755 ? M'he trobat un usuari amb alguna carpeta amb permisos 700 (ex.  .kde , .gnome2 ,gconf   ) Cal corregir-ho ?

Gràcies,
Ernest

---

### Post by papapep on 2007-12-08
Hauries de deixar els permisos com estan. Els paquets, en condicions normals, ja s'encarreguen de configurar això quan s'instal·len.
Excepte que tu mateix hagis modificat alguna cosa, segur que ja està bé com està. I el .dmrc deixa'l a 600, ja està bé.

---

