---
title: "[SOLVED] Connecto pero no puc navegar per internet (Feisty)"
date: 2007-10-08
forum: Catalan Team
---

### Post by manelolesa on 2007-10-08
Feisty

Hola,
em connecto be  a Internet el Servidor em dona una adreça IP i via consola puc pingar a qualsevol adreça.
Però des de el Firefox, Epiphany,Elinks, no puc navegar.
La connexió es amb 3g. Al mateix equip tinc Windows i  si que funciona el Navegador (no mel puc treure de sobra el malparit).
Salut

Manel

---

### Post by scrooge_74 on 2007-10-08
Tienes alguna muralla de fuego instalada? Revisa la configuración del mismo navegador, que diga conexión directa a internet.

---

### Post by CarlesOriol on 2007-10-09
Pot ser que et falti el dns.

Prova d'afegir-ne un manualment: 193.152.63.197

---

### Post by scrooge_74 on 2007-10-09
Correcto, puede ser el DNS

Aquií hay instrucciones  [http://opendns.com/](http://opendns.com/)

---

### Post by manelolesa on 2007-10-09
Els DNS no crec que siguin, per que puc pingar a URL'S.

Si no estic equivocat vaig desactivar alguna cosa del IPV6.

Podria ser aixo ?

Salut

---

### Post by papapep on 2007-10-09
No, a no ser que el teu proveidor d'accés a internet utilitzi aquesta versió del protocol, fet altament improbable (vaja, que no és això).

Si pots fer ping a tot arreu, pinta que sigui problema de tallafocs que estàs tallant la sortida pel port 80 (cosa absolutament curiosa).

Tens el firestarter instal·lat??

---

### Post by manelolesa on 2007-10-09
A veure ara no tinc l'equip davant pero l'Ubuntu esta amb la instal.lació neta. No se si ja ve el Firestarter.

El tema del IPV6 ho vaig desactivar per recomanació  en un article de Optimitzacio de l'Ubuntu.

El que es clar es que alguna cosa he tocat perque abans si que anaba.


Salut

---

### Post by scrooge_74 on 2007-10-09
Seguro tienes bloqueado el puerto 80, algún proxy instalado?

---

### Post by manelolesa on 2007-10-09
Ara mirare el tema del Tallafocs i el port 80.
El que si que he comprovat es quue el Correu, el Sinaptyc i els programilles de RSS si que funcionen.

Estic flipant.

Salut

---

### Post by manelolesa on 2007-10-09
Ja puc navegar.

El problema venia per el IPV6
En un article d'optimització de Ubuntu, posaba que per desactivar el IPV6 es tenia que crear un fitxer a /etc/modprobe.d/, anomenat bad_list e insertar el texte: alias net-pf-10 off.

Mirant en un post he vist que aixo també es configura en el fitxer /etc/modprobe.d/aliases on Jo tenia :alias net-pf-10# ipv6, no se si el IPV6 s'estaba fent la pixa un lio o que.

Bé donç m'he pelat el fitxer bad_list i despres de reiniciar puc navegar sense problemes.

Salut i gracies

---

### Post by Ferri on 2007-10-09
Per inhabilitar IPV6 jo faig servir [això]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4"), sense cap problema.

---

