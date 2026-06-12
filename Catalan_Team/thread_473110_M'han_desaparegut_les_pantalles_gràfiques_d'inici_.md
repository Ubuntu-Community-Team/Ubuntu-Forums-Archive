---
title: "M'han desaparegut les pantalles gràfiques d'inici i tancamant"
date: 2007-06-13
forum: Catalan Team
---

### Post by rajoar on 2007-06-13
Hem passa una cosa curiosa:
No se ben bé que és el que dec haver tocat que m'han desaparegut les pantalles gràfiques d'inici i de tancament del programa... Ara em surten pantalles tipus Dos, com si engegués en la modalitat a prova de errors... Es a dir van surtin tots els llistats dels elements que es van carregant o descarregant fins al final... Sabeu com puc recuperar el modus normal amb les pantalles gràfiques corresponents?...

---

### Post by crazyserver on 2007-06-13
a viam...
mirarem que tinguis el menu del grub ben configurat
obre un terminal i fes:
cat menu.lst | grep vmlinuz

Si et diu permision denied, escriu sudo davant de la comanda.
Quan ho tinguis posa el resultat al forum, a veure que podem veure

---

### Post by rajoar on 2007-06-14
Bé, això es el que surt:
sudo cat /boot/grub/menu.lst | grep vmlinuz
# kernel        /vmlinuz root=/dev/hda2 ro
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=425d32a2-6825-424c-9686-4726b66a5610 ro quiet splash locale=es_ES
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=425d32a2-6825-424c-9686-4726b66a5610 ro single
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=425d32a2-6825-424c-9686-4726b66a5610 ro quiet splash locale=es_ES
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=425d32a2-6825-424c-9686-4726b66a5610 ro single

Tot funciona bé però han desaparegut les pantalles gráfiques de kubuntu amb la característica barra de progrés, tant a l'obrir com al tancar el programa (¿...?)... i surt tot en mode text, semblant al mode de recuperació...
He probat d'instal·lar el Start-up Manager i totes les configuracions posibles i sempre carrega i descarrega en mode text...

---

### Post by patrickfromspain on 2007-06-14
sudo dpkg-reconfigure linux-image-2.6.20-16-generic igual ho arregla.

salut

---

### Post by rajoar on 2007-06-14
Doncs no..., l'execució de sudo dpkg-reconfigure linux-image-2.6.20-16-generic no ho ha arreglat. Tot ha quedat igual. Continua carregant en mode text...

---

### Post by papapep on 2007-06-14
I què tal fent: "sudo dpgk-reconfigure kubuntu-desktop"  (sense cometes, clar).

Si no fa res, "sudo aptitude install kubuntu-desktop".

Igual és que t'has carregat tot t'entorn gràfic sense adonar-te'n...

---

### Post by rajoar on 2007-06-14
Bé, la resposta a "sudo dpgk-reconfigure kubuntu-desktop" (dpkg en comptes de dpgk) ha estat que no estaba instal·lat, tal com intuies. He instalat amb "sudo aptitude install kubuntu-desktop". Pensaba que ja estaria tot arreglat, però no, tot continua igual... Arrancada i tancament en mode text (¿...?)...

---

### Post by papapep on 2007-06-14
Bé, doncs ara (si noi, abans m'han ballat la k i la g...): "sudo aptitude install kdm"

---

### Post by rajoar on 2007-06-14
Sí, també ho he fet i, sorprenentment tot continua igual..., en mode text. De totes maneres ara me n'adono que si carrego amb el kernel 2.6.20-15 torna a funcionar l'entorn gràfic de kubuntu. Potser hauria de reconfigurar el kernel 2.6.20-16? O tornar-lo a instal·lar? O estic dient una bestiesa?...

---

### Post by papapep on 2007-06-14
Si el 2.6.20-16 no et fa falta per res especial, passa d'ell. No crec que et valgui l'esforç. Simplement edita el fitxer /boot/grub/menu.lst i comenta les línies que fan referència al kernel que et falla.

---

### Post by rajoar on 2007-06-14
Bé, moltes gràcies pel teu interès, seguiré els teus consells que són d'agrair. Però m'agradaria que m'expliquesis si es molt complicat, des del kernel 2.6.20-15, desinstal·lar el kernel 2.6.20-16-generic per a què després es tornés a regenerar?... Només és per aprendre una miqueta més...

---

### Post by papapep on 2007-06-14
Si el que vols és desinstal·lar la versió 2.6.20-16:

sudo aptitude purge linux-image-2.6.20-16-generic (suposant que sigui aquesta la versió que tens instal·lada).

Per a tornar-la a instal·lar, simplement:

sudo aptitude install linux-image-2.6.20-16-generic

No té més secrets (a les distros Debian like, clar...)

En condicions normals, t'hauria de funcionar tot correctament després d'instal·lar-lo, però si et torna a fallar ja t'he dit què faria jo.

Salutacions.

---

### Post by AlexMuntada on 2007-06-16
> **rajoar said:**
> ara me n'adono que si carrego amb el kernel 2.6.20-15 torna a funcionar l'entorn gràfic de kubuntu.

Això té tota la pinta de ser un problema amb els control·ladors privatius que ha provocat la versió 2.6.20-16.  Pots comprovar si tens aquests paquets instal·lats?

```
$ dpkg -l linux-$(uname -r|cut -f3 -d-) | grep ^i
ii  linux-...
$ dpkg -l linux-restricted-modules-$(uname -r|cut -f3 -d-) | grep ^i
ii  linux-restricted-modules-...
```

En cas que no els tingues, els hauries d'instal·lar:
```
sudo apt-get install linux-$(uname -r|cut -f3 -d-)
sudo apt-get install linux-restricted-modules-$(uname -r|cut -f3 -d-)
```

---

### Post by rajoar on 2007-06-16
Efectivament, Àlex, l'has clavada... Després d'instal·lar-los tot ha tornat a la normalitat!...
No se ben bé què és això que m'has fet fer, però... funciona!!!
Merci...

---

### Post by AlexMuntada on 2007-06-16
> **rajoar said:**
> No se ben bé què és això que m'has fet fer, però... funciona

Si teniu curiositat per saber què fa tot això que us he indicat, us ho puc explicar amb pèls i senyals.  Només m'ho heu de demanar.

---

