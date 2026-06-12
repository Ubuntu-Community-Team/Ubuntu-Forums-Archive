---
title: "Quins adaptadors inalambrics feu servir?"
date: 2007-11-19
forum: Catalan Team
---

### Post by patrickfromspain on 2007-11-19
Hola gent! Igual estaria bé fe una especie de base de dades sobre quins adaptadors inalambrics fem servir, si funcionen be o si s'ha de tunejar algun cosa per a que vagin fins. Hem sembla que pot ser de gran ajuda per a la gent que es vol comprar un adaptador wifi nou o es nova a ubuntu i no sap com procedir. També es podria penjar al wiki (jo m'ocuparia de transcriure la informació d'aquest post al wiki, si voleu algun moderador i/o responsable del wiki catala enviu-me un missatge personal i ho comentem). Bé, començo jo:


**MARCA i MODEL:** Conceptronic C54Ri
**FORMAT:** pci
**XIPSET: **Ralink RT2500 (11b/54g)
**DRIVERS:** rt2500pci (lliure)
**OBSERVACIONS: **no s'ha de fer res per a que funcioni, te l'agafa al principi. L'unic però es que sempre marca un -1 de senyal. Jo he desinsta&#320;lat el network manager i l'he substituit per la versió 1.3.6 del wicd, que permet veure el senyal en dBm. I va de conya.


**MARCA i MODEL:** US Robotics 5416 Turbo
**FORMAT:** pci
**XIPSET:** Texas Instruments tnet1130 (11b/54g)
**DRIVERS: **acx / ndiswrapper
**OBSERVACIONS: **la tarjeta te l'agafa automaticament amb el driver acx, pero no va fina: als logs hi han molts missatges de paquets perduts i recalibració de radio. Hem funciona compilant ndiswrapper 1.44 (i desinsta&#320;lant linux-ubuntu-modules del kernel. Altres versions d'ndiswrapper o l'incluit als repos d'ubuntu hem penjen el sistema al cap d'una estona) i carregant el driver una tarja wg311 versio 2 de Netgear.

Bé, seguiu vosaltres. SI US PLAU, feu servir el mateix format i no demaneu ajuda de com fer anar una tarja wifi (obriu un tema a part per aixo). Les observacions haurien ser breus i clares.

Gracies i salut!

---

### Post by papapep on 2007-11-19
**MARCA i MODEL:** Intel Corporation PRO/Wireless 2200BG
**FORMAT:** mini-pci (Incrustada a la placa mare)
**XIPSET:** Intel 2200BG
**DRIVERS: ** [Ipw2200]("http://ipw2200.sourceforge.net/") (802.11a/bg-Lliure)
**OBSERVACIONS:** No s'ha de fer res per a que funcioni. Com en d'altres casos, el Network Manager no el gestiona massa bé. Jo també utilitzo el Wicd, que sembla que s'hi aclareix millor, tot i que no faig servir massa el wifi.

---

### Post by lluisanunez on 2007-11-19
Tinc el mateix que en Papapep, Intel 2200BG. Al principi va ser un malson, m'havia de baixar i insta&#320;lar un mòdul de kernel cada vegada que aquest s'actualitzava. 
Ara va molt bé.

---

### Post by patrickfromspain on 2007-11-19
Una altra:
**MARCA i MODEL:** Ambit INPROCOMM 2220
**FORMAT:** mini-pci
**XIPSET:** INPROCOMM 2220
**DRIVERS:** ndiswrapper (driver neti2220.inf)
**OBSERVACIONS:** encara que s'ha de fer servir ndiswrapper, la tarja funciona molt be. Faig servir el WICD per connectar, buscar xarxes, etc. A Gutsy, sembla que ha donat alguns problemes, encara que jo encara no els he notat (faig servir el portatil molt poc)

---

### Post by patrickfromspain on 2007-11-19
**MARCA i MODEL:** Intel Pro Wireless 3945
**FORMAT: **mini-pci
**XIPSET:** Intel 3945abg
**DRIVERS:** ipw3945 (driver lliure, firmware privatiu)
**OBSERVACIONS: **funciona bé sense fer res (cal tenir insta&#320;lat els restricted modules i el linux-ubuntu-modules). Detecta xarxes i es connecta tant en network-manager com amb el Wicd

---

### Post by torracastanyes on 2007-11-19
MARCA i MODEL:  Philips SNN6500
FORMAT:  PCMCIA
XIPSET:  Atheros 5006x 802.11abg NIC
DRIVERS: ath_pci
OBSERVACIONS:  Jo tampoc la faig servir gaire, en Gutsy encara no la he provat, però Feisty la va instal.lar sence haver de tocar res.

---

### Post by patrickfromspain on 2007-11-22
AMUNT!!!!

Si feu servir una tarjeta wireless, colaboureu i digueu quina i que tal va! Si en teniu una que no va, digueu quina!

Salut!

---

### Post by PellRoja on 2007-11-22
a [www.gnuinos.com](www.gnuinos.com) em vaig comprar una inalambirca que em va molt be.

---

### Post by patrickfromspain on 2007-11-22
Ains...

MARCA i MODEL:
FORMAT:
XIPSET:
DRIVERS: 
OBSERVACIONS: 

gracieeeeees

;)

---

### Post by Tomàs M. on 2007-11-22
MARCA i MODEL: D-Link System Inc DWL-520+ 22Mbps PCI Wireless Adapter
FORMAT: PCI
XIPSET: Texas Instruments
DRIVERS: [acx100]("https://help.ubuntu.com/community/WifiDocs/Driver/acx100")
OBSERVACIONS: "[out of the box]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")"

---

### Post by girotix on 2007-11-24
Salutacions,

Al tanto! Potser poso alguna dada imprecisa (aquestes dades suposo que es treuen des de: *System/Preferències/Hardware Information)*


**MARCA i MODEL:** Broadcom Corporation BCM94311MCG wlan mini-PCI
**FORMAT**: pci
**XIPSET:*** (no ho sé)*
**DRIVERS:** ndiswrapper *(no sé si falta quelcom més)*
**OBSERVACIONS:** Amb l'anterior versió de Ubuntu funcionava bé una vegada ho havies instal·lat amb el ndiswrapper. Des que tinc la darrera versió l'ordinador no em memoritza algun dels comandaments en línia per configurar-la (poso un altre post per explicar-ho). En quant a la marca i model, recordo que l'altra vegada que vaig fer un Hardware Information em va sortir aquestes dades: Dell Wireless 1390 WLAN Mini-PCI Card. En canvi, ara em surt les dades de marca i model de dalt? Potser que l'Ubuntu m'identifiqui de diferent manera la tarja? 


SVP, digueu-me d'on trec les dades que falten.

A reveure,
Carles.

---

