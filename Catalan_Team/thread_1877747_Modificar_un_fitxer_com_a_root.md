---
title: "Modificar un fitxer com a root"
date: 2011-11-08
forum: Catalan Team
---

### Post by JUSTERINI1 on 2011-11-08
Com puc modificar un fitxer com a root?

Perquè?:
Tinc un disc multimedia iomega director que té la possibilitat de conectarse per wifi. El fet és que cada vegada haig d'introduïr el password del router ja que no guarda la configuració, un rotllo.
Un dia me la va guardar (fet insòlit, dit pel mateix SAT de iomega) i vaig veure que quedava guardada en un fitxer anomenat wynetwork.conf i en vaig copiar el contingut per si les mosques. Les mosques les necessito ara, pq al canviar el router m'ha eliminat el contingut de wynetwork.conf. Com que ja sé el que hi ha d'anar a dins (instruccions de configuració tipus txt) el vull modificar manualment, però no hi puc accedir perquè només hi té accés root.

Gràcies
Justerini.

---

### Post by wgarcia on 2011-11-09
Per treballar com a superusuari per una estona, es pot fer servir la comanda "gksudo". Per exemple entrar ALT F2 i aquí entrar "gksudo nautilus", t'obrirà un navegador de fitxer com a superusuari.

Molt de compte amb aquesta comanda perquè des d'aquest navegador es pot fer TOT, per exemple esborrar o canviar fitxers de sistema que afectin els seu funcionament.

---

### Post by JUSTERINI1 on 2011-11-09
Molt bona la solució. Gràcies wgarcia.
Aprofitant, el disc multimèdia té 4 particions, 2 visibles i 2 ocultes en format linux. Alguna idea de com accedir-hi? allí hi ha tot el programari (lliure gnu) que controla el disc dur i m'hi agradaria remenar una mica (actualizar codecs,format dels subtitols etc etc) , no em fa por carregar-me res, pq sempre tinc la possibilitat de formatejar tot i tornar a carregar el firmware via usb.

gràcies per endavant.

---

### Post by wgarcia on 2011-11-10
No entenc del tot bé què vols fer i com tens el disc. Què vol dir particions visibles i ocultes? Quan endolles el disc, quina partició és munta a l'escriptori?

---

### Post by JUSTERINI1 on 2011-11-11
Hola,
és un disc de 2Tb, que a l'escriptori em surten 1,8TbNtfs, 1,1Gb jfs, 256 Mb FAT i llavors hi ha 2 particions més que no es munten i que són: 
271Mb Memoria intermèdia de linux és el deb/sdb1
271Mb ús desconegut i és de tipus LInux (0x83) és el deb/sdb2

Aquestes són les 2 particions que m'agradaria accedir.


Disculpeu la tardança en el feedback, faig el que puc...

---

### Post by wgarcia on 2011-11-13
Suposo que et refereixes a "dev" i no "deb". 

Per muntar aquestes altres dues particions que menciones, pots provar de crear alguna carpeta i anomenar-les com ho consideris oportú, per exemple a la teva carpeta inicial pots crear una que es digui "disc1"  l'altra "disc2" o de qualsevol altra manera que t'agradi. Després obrir una "terminal" i entrar:

```
sudo mount /dev/sdb1 ~/disc1
sudo mount /dev/sdb2 ~/disc2

```

i amb el navegador de fitxers hauries ara se ser capaç de veure aquestes carpetes a la teva carpeta d'inici i el contingut de les particions en elles.

---

### Post by JUSTERINI1 on 2011-11-15
En el dev/sdb1 em diu que és un sistema d'intercanvi i em demana el tipus de fitxers:
sudo mount -r /dev/sdb1 ~/director1
/dev/sdb1 sembla espai d'intercanvi - no s'ha muntat
mount: haureu d'especificar el tipus del sistema de fitxers

En el dev/sdb2 em diu que tb necessita el sistema de fitxers, 

Com ho puc saber?

---

### Post by wgarcia on 2011-11-15
Entrant a una terminal

```
sudo fdisk -l
```

et llistarà les particions i el tipus de sistema de fitxer que és.

---

