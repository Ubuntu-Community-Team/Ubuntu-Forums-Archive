---
title: "hibernar portàtil i wifi"
date: 2007-09-02
forum: Catalan Team
---

### Post by guillemsola on 2007-09-02
Quant hiberno el portàtil perdo el wifi i després l'ubuntu queda penjat a l'hora d'apagar el sistema (al final de tot de la barra de progrés)

He vist aquesta ajuda [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) i diu que crei aquests scripts

      /etc/acpi/suspend.d/07-network-manager.sh

> #!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop

      /etc/acpi/resume.d/63-network-manager.sh

> #!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start

Els scripts funcionen correctament. Se suposa que han anat a parar allí on busca l'ubuntu que fer amb els serveis durant la hibernació però el resultat és que perdo el dispositiu wifi del portàtil. Després d'hibernar ifconfig ja no llista el dispositiu wifi.

Sóc conscient que potser és un tema complicat però seria fantàstic que funciones. He de considerar això un bug i posar-lo al LaunchPad?

salut!

---

### Post by ChAoS.ct on 2007-09-05
> **angrychai said:**
> He de considerar això un bug i posar-lo al LaunchPad?


A vegades buscar si el bug existeix ja en el launchpad et dóna la solució al problema :p.

Sort

---

### Post by guillemsola on 2007-09-06
Esta clar q per aquest i algun altre problema que tinc hauré de mirar més al launchpad però aquestes instruccions venen d'ubuntu, és una especie de howto. Però no tinc clar si és un bug o que no ho faig bé XD!

Salut!

---

### Post by lluisanunez on 2007-09-06
Has llegit [aquest fil sobre wicd]("http://ubuntuforums.org/showthread.php?t=543547")? A la pàgina del projecte diu que una de les *features* és recuperar la connexió després d'hibernar

---

