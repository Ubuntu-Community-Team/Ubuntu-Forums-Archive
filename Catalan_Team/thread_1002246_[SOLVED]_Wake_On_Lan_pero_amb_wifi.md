---
title: "[SOLVED] Wake On Lan pero amb wifi"
date: 2008-12-04
forum: Catalan Team
---

### Post by tanreb20 on 2008-12-04
hola!

Avui he instalat el **wake on lan** seguint aquest manual:

[http://andalinux.wordpress.com/2008/11/14/encender-un-ordenador-desde-la-otra-punta-de-la-casa-y-sin-pulsar-el-boton/](http://andalinux.wordpress.com/2008/11/14/encender-un-ordenador-desde-la-otra-punta-de-la-casa-y-sin-pulsar-el-boton/)

Tot va correcte, pero cuan intento fer aixo amb la tarjeta de xarxa inalambrica(aka wifi) no em deixa. em diu:

 bernat @ portatil > sudo ethtool -s wlan0 wol g 
[sudo] password for bernat:                                
**Cannot set new wake-on-lan settings: Operation not supporte not setting wol**

m'encantaria poder fer-ho amb el wifi, alguna idea?

---

### Post by RafaelCarreras on 2008-12-05
Jo no hi entenc gaire d'aquestes coses, però no n'he sentit a parlar mai de Wake on Lan amb wifi. Entenc que el Wake on Lan funciona gràcies a un impuls elèctric pel cable de xarxa i no veig com es pot fer això sense el cable. Amb l'ordinador apagat, el wifi no funciona, clar.

És així?

---

### Post by argggg on 2008-12-05
Lo primer que has de fer es mirar si la tarja wireless suporta wowl (Wake on Wireless Lan), que jo sàpiga no es tan habitual com el wol

---

### Post by tanreb20 on 2008-12-05
és al revés.

el despertador té wifi

i el despertat te lan

---

### Post by papapep on 2008-12-05
Si el dormilega no té wifi, per què executes aquesta ordre amb l'interfície wifi (wlan0)?
O és que l'executes al despertador?, amb el qual tampoc té sentit, ja que el que ha de tenir el suport de wol és el dormilega...?

---

### Post by tanreb20 on 2008-12-06
a veure que no ens entenem...

el meu portatil (amb l'inbtrepid) vol fer de despertador de l'altre, si? Va conectat al router amb Wifi.

l'altre, es a dir el dormilega, es una torre conectada a LAN, el dormilega ja té activada la WOL i desde el portatil conectat per LAN si que s'engega.

LA pregunta és: hi ha una manera per fer que jo a través d ela wifi li envii una senyal al router que fagi engegar el sobretaula(LAN?)

---

### Post by papapep on 2008-12-06
Jo t'he entès perfectament des del primer moment...però no respons el meu anterior post :-)

El senyal, NO li envies al router, sinó a la placa de xarxa que vols despertar. Si hi ha un router per mig, doncs has de fer el que calgui per a que el router la redirigeixi, però no és l'objectiu el router. Llegeix-te bé la documentació que has referenciat, que ho explica prou bé.

---

