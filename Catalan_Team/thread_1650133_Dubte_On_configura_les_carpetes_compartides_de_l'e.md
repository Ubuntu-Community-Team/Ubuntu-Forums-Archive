---
title: "Dubte: On configura les carpetes compartides de l'entorn gràfic?"
date: 2010-12-21
forum: Catalan Team
---

### Post by kukat on 2010-12-21
Estic compartint unes carpetes per a equips Windows, i he configurat el fitxer /etc/samba/smb.conf, com de costum. 
Però després un altra persona m'ha indicat com fer-ho des de l'entorn gràfic amb el "botó dreta->opcions de compartició"

On es configura aquesta compartició a Samba??? Per què al fitxer "smb.conf" no està aquesta compartició, en canvi, l'altra carpeta que havia fet manualment, evidentment està i ixen les dues juntes.....

!!!????

Gràcies!

---

### Post by vila-seca on 2010-12-24
> **kukat said:**
> Estic compartint unes carpetes per a equips Windows, i he configurat el fitxer /etc/samba/smb.conf, com de costum. 
Però després un altra persona m'ha indicat com fer-ho des de l'entorn gràfic amb el "botó dreta->opcions de compartició"

On es configura aquesta compartició a Samba??? Per què al fitxer "smb.conf" no està aquesta compartició, en canvi, l'altra carpeta que havia fet manualment, evidentment està i ixen les dues juntes.....

!!!????

Gràcies!

El que pots provar és d'instal·lar-te l'aplicació gràfica del servidor de samba que et llegirà la configuració del smb.conf

  sudo apt-get install  system-config-samba

Un cop instal·lat has d'anar a Sistema > Administració

Ja ens indicaràs

---

