---
title: "problema connexió inalàmbrica d-link dwl g-122"
date: 2009-05-22
forum: Catalan Team
---

### Post by socderafel on 2009-05-22
hola a tots!
resulta que estic tenint prolemes amb la targeta wifi(la que he posat dalt). Quan arranca el sistema, entro al firefox i funciona, però sols per 30 segons...
Després res de res. Faig un ping al router (192.168.1.1) i no em respon. si deshabilite la connexió inalàmbrica i la torne a habilitar, torna a funcionar uns altres 30 segons...
La targeta la detecta bé, i es connecta amb la xarxa, però no envia ni rep paquets...
Ho he provat a windows i funciona bé. 

Gràcies per adelantat!!

---

### Post by CarlesOriol on 2009-05-22
Envia copia de les darreres linies del dmesg a veure si ens diu res.

---

### Post by kukat on 2009-05-22
Al terminal:

**dmesg | grep "wlan0"**

algo així he vist [per la xarxa]("http://ubuntuforums.org/showthread.php?t=977352&page=2")

---

### Post by papapep on 2009-05-22
Prova amb alguna versió anterior de nucli.

---

