---
title: "pontejar eth0 a wlan0 a ubuntu-server"
date: 2009-05-11
forum: Catalan Team
---

### Post by marteljorge on 2009-05-11
Es pot fer?
Tinc eth0 configurada manualment, però wlan0 no la tinc configurada...
Volia fer com un punt d'accés sense fils.

---

### Post by orestesmas on 2009-05-14
Tot es pot fer, si es pot imaginar.

Però suposo que evidentment la wlan0 l'has de tenir "configurada" i connectada a una xarxa.

Jo no ho he fet mai ni sóc expert en el tema, però si hagués de fer quelcom així (una mena de bridge que traspassi paquets entre eth0 i wlan0, sense preocupar-se del protocol) en primer lloc em miraria (i/o cercaria info al google sobre) el paquet bridge-utils.

Potser algú pot aprofondir més en el tema.

---

### Post by marteljorge on 2009-05-14
Peró, no és només un pont, també necessito fer de punt d'accés.

---

### Post by papapep on 2009-05-14
Assumint que el vols fer és de passarela de sortida per a una xarxa inalàmbrica, [aquí]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint") tens informació al respecte.

---

