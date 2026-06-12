---
title: "adaptador wifi compatible linux"
date: 2007-11-16
forum: Catalan Team
---

### Post by raukonak on 2007-11-16
Hola nois i noies!

Estic pensant en comprar-me un adaptador (es a dir, no un router, sino el catxarro per conectar-se a aquest) i volia saber si hi ha algun que vingui amb els drivers per ubuntu o com a minim amb les fonts per compilar.

He mirat amb el google i no he trobat re, he mirat al forum i he trobat això: [http://ubuntuforums.org/showthread.php?t=367917](http://ubuntuforums.org/showthread.php?t=367917), pero m'agradaria saber l'opinió d'algu d'aqui. Merci

---

### Post by motec on 2007-11-18
hola,
jo no se quin pot ser bo d'adaptador wifi, pero el que no et recomanaria mai es el conceptronics c54ru, jo el trobo molt complicat de instalar sota linux.

---

### Post by raukonak on 2007-11-18
Doncs si et dic que es el que em pensava comprar (més que res, perque posats a fer es el mes barat i porta un chipset de ralink que sembla que es facil d'instalar) Pero he trobat un de wifisafe que venen al pricoinsa que sembla que et ve amb els drivers.

---

### Post by elbuit on 2007-11-18
Jo tinc un conceptronic USB (un ralik) i la veritat és que m'ho ha pillat sense problema.
La qüestió és que el conceptronic usb li varen canviar el xipset (també per un altre ralink) que també crec que estava suportat (ralink proveeeix els drivers amb el codi font).
El problema d'eixe model, és que era un poc "sord" i no pillava molta senyal. En un PCI va molt millor (també ralink), i en el portatil m'he pillat un conceptronic pcmcia (també ralink, concretament rt61). Tots ha estat detectats bé des d'ubuntu (la versió anterior no t'el mostrava en el gestor de xarxa, pero en l'actual si).
De totes formes jo empre un programa per a les ralink (rutilt) que està prou bé i està als repositoris de gusty.

---

### Post by patrickfromspain on 2007-11-19
jo estic fent servir un Conceptronic PCI amb xipset RT2500 de ralink. Amb els drivers incluits a ubuntu i el wicd 1.3.6 va molt be.

Salut!

---

### Post by raukonak on 2007-11-27
Gràcies per la informació, crec que agafaré el conceptronic. Merci

---

### Post by CarlesOriol on 2007-11-29
Vigila el conceptronic... jo tinc un parell amb xipset ralink rt61 de "florero"

---

### Post by patrickfromspain on 2007-11-30
> **CarlesOriol said:**
> Vigila el conceptronic... jo tinc un parell amb xipset ralink rt61 de "florero"
el driver rt61pci no et va?

---

### Post by CarlesOriol on 2007-11-30
No em va anar res... vaig agafar un atac de ralinkufobia ;-)

Un dia (d'aquí dos o tres kernels) les torno a provar i us comento.

---

### Post by rroca1 on 2008-02-20
SMC:

N'he tingut tres i tots tres m'hi han funcionat

El que tinc ara i que apareix com a eth2 és del model ez Connect (per la resta no tinc les ulleres  a mà!)

---

### Post by Tomàs M. on 2008-02-22
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) 

:-)

---

