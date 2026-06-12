---
title: "[SOLVED] Serveis Xarxa inhabilitat"
date: 2007-10-21
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2007-10-21
Bones.
Recienment he instal·lat un nou Routter Thomson model ST516 v6. Tinc Ubuntu 7.04 Cada cop que inicio Ubuntu hem sur un missatge que abans no surtia: "El servei de descoberta de serveis a la xarxa està inhabilitat. la vostra xarxa actual té un domini .local, que no és recomanat i és incompatible amb la descoberta de serveis a la xarxa Avahi. S'ha inhabilitat el servei."
De totes maneres, internet hem va perfecte, només tinc curiositat que carai vol dir aixó.
Moltes gracies.

---

### Post by lluisanunez on 2007-10-21
Avahi és el que diu al missatge, un servei de descoberta de xarxes wifi que necessites quan vas viatjant amb el portàtil. Si sempre et connectes a la mateixa, no et cal l'Avahi. Pots aturar el servei amb:
```
sudo /etc/init.d/avahi-daemon stop
```
Alternativament, depenent de la configuració de xarxa que tinguis, potser la pots corregir (domini, host...) perquè l'Avahi funcioni,

---

### Post by Miquel Ubuntero on 2007-10-21
Resolt!
Moltes gracies. Era una mica emprenyador el missatget. De fet no hem cal cap servei wifi amb routter que no te wifi.

---

