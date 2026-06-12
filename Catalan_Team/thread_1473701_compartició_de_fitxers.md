---
title: "compartició de fitxers"
date: 2010-05-05
forum: Catalan Team
---

### Post by telejet on 2010-05-05
Hola a tothom,

Un company meu utilitza l'ubuntu i no se'n surt de veure la xarxa de windows, quan jo no he tingut mai cap problema.

Ara s'ha actualitzat a la 10.04 i continua igual, avui m'he connectat remotament a la seva màquina per mirar d'arreglar-ho però no hi ha manera, al anar a la xarxa em diu error no s'han pogut muntar blablabla.

Quan vaig a sistema-preferencies-compartició de fitxers NO puc seleccionar comparteix els fitxers públics a la xarxa ja que em diu que No es pot habilitat aquest servei perquè no disposa dels paquets necessaris.

Normalment sortia una finestra que et deia que si els volies instal·lar i llestos, aquí no.

Entrant per terminal i posant shares-admin també m'ho hauria de preguntar però no ho fa.

Té instal·lat el samba smbfs samba-client i tots els relatius al samba. Els he desinstal·lat, purgant la configuració i tornant-los a instal·lar però no hi ha manera.

Algú sap els paquets que li fan falta?

Gràcies,

Ivan

---

### Post by wgarcia on 2010-05-05
sudo apt-get install apt-rdepends
apt-rdepends samba

---

### Post by papapep on 2010-05-05
Ivan, aquí veuràs totes les dependències:

[http://packages.ubuntu.com/lucid/samba](http://packages.ubuntu.com/lucid/samba)

i un:

```
sudo apt-cache show samba
``` 

també t'ho dirà.

---

