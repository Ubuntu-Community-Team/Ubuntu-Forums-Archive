---
title: "Gestor de red no detecta la wifi"
date: 2009-10-30
forum: Catalan Team
---

### Post by MorlanXaos on 2009-10-30
He instal.lat la nova versió, 9.10. En termes generals no crec que sigui molt mes ràpida. Però m'agrada.

L'únic inconvenient es que m'he quedat sense Wi-Fi.

El controlador la targeta està present. El nou Gestor de xarxes detecta la red ethernet (wlan?)- Estat Desconnectat. Però no em dona opció a connectar-me a la inalambrica. He configurat la connexió de xarxa sense fil, pero no hi ha manera.

Fent servir lshw em mostra la wi-fi.

xavier@xavier-casa:~$ sudo lshw -C network
[sudo] password for xavier: 
  *-network               
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 03
       serial: 00:1e:2a:47:44:17
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8335 driverversion=1.55+Marvell,02/22/2005,3.1.1.7 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:febf0000-febfffff memory:febe0000-febeffff

---

### Post by MorlanXaos on 2009-10-30
Això es una mica frustrant. De cop i volta la Wi-Fi a començat a funcionar, després de haver repassat la configuració de la meva connexió 35 vegades des de "Connexions de xarxes". 

Peró en el nou gestor de xarxes no veig les del meu voltant. (La icona de la barra superior dreta GNOME)

---

### Post by rroca1 on 2009-11-29
Jo faig servir com a gestor WICD en lloc del networkmanager i he resolt problemes com aquest (quan n'instal·les un et demana de treure l'altre)

Espero que serveixi

---

### Post by MorlanXaos on 2009-12-02
Gracies, ho provaré! ;)

---

