---
title: "Icones doblades"
date: 2007-05-06
forum: Catalan Team
---

### Post by Josep Maria on 2007-05-06
Hola :
Tinc dos dics durs externs, des que he actualitzat a Feisty, quant inicio amb els discs engegats, em surtes dues icones per cada disc, enlloc d'una per cada.
Bé, no és un problema gaire greu, però no sé per que passa.
Un te format ntfs, i l'altre fat32.
Pot ésser perquè tenia instal.lat en Edgy NTFS configuration Tol, i s'ha quedat al actualitzar?

Josep Maria

---

### Post by lluisanunez on 2007-05-06
És molt probable, perquè Feisty ja porta suport per NTFS

---

### Post by Josep Maria on 2007-05-06
Si Lluïsa, però sense aquesta aplicació d'automatix no puc escriure als dics externs NTFS.
Si engego l'ordinador, i després connecto els dics llavors només surt una icona a l'escriptori.

---

### Post by lluisanunez on 2007-05-06
No ho puc comprovar perquè no tinc cap directori NTFS, però avui he llegit als fòrums en anglès que Feisty ja porta el suport incorporat

---

### Post by CarlesOriol on 2007-05-07
Mostra'ns l'arxiu fstab.

En qualsevol cas l'ús d'automatix és una font gegant de problemes i et recomanaria que no l'usesis.

---

### Post by Josep Maria on 2007-05-08
On trobo l'arxiu fstab ?

---

### Post by papapep on 2007-05-08
fstab, i molts altres fitxers de configuració del sistema, és a /etc/fstab

Et recomano que per trobar fitxers o directoris, en consola, utilitzis l'eina "locate".

Per a fer-lo servir, primer actualitza la base de dades teclejant en consola

```
sudo updatedb
```

i un cop hagi acabat el procés, posa:

```
sudo locate fstab
```

i el sistema et mostrarà totes les coincidències amb el fitxer que busques, en aquest cas l'fstab

---

### Post by Josep Maria on 2007-05-08
oka
ja l'he trobat.

I em sembla que ja ha pujat.


Josep Maria

---

### Post by CarlesOriol on 2007-05-08
El fstab és correcte... seguim pensant!

---

### Post by patrickfromspain on 2007-05-08
Per probar que no quedi no? Se m'acut:
al teu arxiu /etc/apt/sources.list, comentes el repos de l'automatix (i fas un sudo apt-get update), obres aquell programa i desactives l'opcio d'escriure en NTFS (tant interns com externs) i per ultim desintal·les tot el que sigui del ntfs-3g i fuse (selecciona eliminar completament). Ara reinicies.

Et segueixen sortint les icones doblades?

De totes formes, per tonar a instal·lar ntfs-3g fas un sudo apt-get install ntfs-3g ntfs-config  i ja esta, no necessites automatix ni xorrades d'aquestes.

Igual te a veure amb alguna clau del gconf-editor, obre'l i ves a system -> storage -> default options i digues que hi ha sota ntfs-3g i vfat. Tambe deus tenir system -> storage -> volumes, a veure que hi tens posat alla. Igual veiem alguna cosa.

Tambe se m'acut que pugui tenir a veure amb hal, el dbus o inclus el kernel, aixi que podries probar a reinstalar aquests paquets (igual estic dient una bogeria, aixi que esperat a que algu que en sapigui mes que jo confirmi o no).

No se.. igual t'he dit moltes tonteries, pro proba-ho.. a males sempre pots fer una copia del teu home i formatejar.

Salut!

---

### Post by Josep Maria on 2007-05-09
El que em dius de fer la copia de la home m'interessa, perquè com que estic provant amb l'ubuntu, ja l'he reinstal.lat dues o tres vegades, i a cada cop haig de configurar-ho tot, i a demés perdo tots el correus.
Com puc fer-ho, i que funcioni?

Gràcies.

Josep Maria

---

### Post by patrickfromspain on 2007-05-09
Be, tens dos maneres: una es fent una particio /home especifica amb l'instalador: quan defineixes les particions, igual que poses una swap i una / en fas una mes i que el punt de montatge es digui /home. Potser algu de per aqui ho té fet així i et sabrà especificar millor.

Jo no ho faig així: el que faig es vaig al meu home i alla hi poso que es vegin el arxius ocults (en nautilus, control+h) i agafo les carpetes que m'interesen: .kde, .amsn, .amule, .mozilla, .thunderbird,.config etc. Si no saps quines agafar doncs agafa-les totes i en paus. En fas un arxiu de tot i despres de reinstal·lar el descomprimeixes al teu home i ja esta. Es facil.

salut!

---

