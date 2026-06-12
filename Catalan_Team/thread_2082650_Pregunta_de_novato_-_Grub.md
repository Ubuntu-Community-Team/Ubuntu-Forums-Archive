---
title: "Pregunta de novato - Grub"
date: 2012-11-10
forum: Catalan Team
---

### Post by karto_on on 2012-11-10
Hola a tothom!

bé, després d'una llarga temporada sense fer anar l'Ubuntu (mai l'he desinstal·lat), m'hi torno a posar, aviam si d'una vegada deixo el Win dels co.. aparcat.
El tema és que em fa molta ràbia que al menú de sel·lecció de SO em surtin totes les versions d'Ubuntu que he instal·lat i ara ja n'hi ha més de 6 o 7.
He investigat i això es gestiona pel GRUB, però seguint les instruccions de la guia Ubuntu no me'n surto:
[http://www.guia-ubuntu.org/index.php?title=GRUB](http://www.guia-ubuntu.org/index.php?title=GRUB)

He buscat més info i he trobat això:
Para realizar las modificaciones que estimes convenientes, debes ejecutar

sudo gedit /boot/grub/grub.cfg
En la parte final del archivo, a partir de la linea

### BEGIN /etc/grub.d/10_linux ###

Però fent el "gedit" em surt un fitxer en blanc, per tant dedueixo que no existeix...

algú em pot ajudar? 

Moltes gràcies!

---

### Post by COMECON on 2012-11-10
La pàgina que has trobat deu estar pensada per el GRUB, i tu deus utilitzar el GRUB2...
Al GRUB2 la configuració es genera automàticament, és a dir, detecta els sistemes operatius que tens instalats, i a partir d'aquesta informació es genera un fitxer de configuració. Els "scripts" que s'utilitzen per generar-la es troben a /etc/grub.d, però, si mires per exemple 10_linux o 30_osprober (el que detecta altres SO) veuràs que són scripts en bash... De manera que no pots simplement treure les entrades que t'interessin.
Potser algú sap com evitar que s'acumulin tantes entrades, però fins a on jo sé, no hi ha manera...
Espero que aconsegueixis solucionar-ho!

---

### Post by jinglada on 2012-11-10
> **karto_on said:**
> 
El tema és que em fa molta ràbia que al menú de sel·lecció de SO em surtin totes les versions d'Ubuntu que he instal·lat i ara ja n'hi ha més de 6 o 7.


wgarcia em va dir que «Normalment convé deixar un o dos nuclis antics per si hi ha algun problema en el nucli actual poder iniciar el sistema, amb això hi ha prou. Per veure si tens molts nuclis instal·lats pots obrir una terminal i fer
```
ls /boot
```
i aquí veurem si tens moltes "imatges" instal·lades.»

Fes-ho i després et diré el que em va fe fer per a eliminar les més antigues.

---

### Post by jmaspons on 2012-11-12
Hola,
si vols eliminar els nuclis antics mira a [http://www.gnulinux.cat/2009/12/eliminacio-de-nuclis-antics-a-ubuntu/](http://www.gnulinux.cat/2009/12/eliminacio-de-nuclis-antics-a-ubuntu/)

Salut!

---

### Post by wgarcia on 2012-11-12
En les versions més noves d'Ubuntu sols venen dues línies al grub, "Ubuntu" i "Versions antigues" (o alguna cosa així), si es clica a "Versions antigues" es veuen els nuclis més antics. 

Però igualment no és mala idea eliminar-los perquè ocupen lloc innecessari.

---

### Post by karto_on on 2012-11-12
Ep!

He fet el que comentava el jmaspons i pim pam!
Moltes gràcies a tots!

Salut!

---

