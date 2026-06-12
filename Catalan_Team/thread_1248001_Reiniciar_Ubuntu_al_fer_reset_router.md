---
title: "Reiniciar Ubuntu al fer reset router"
date: 2009-08-23
forum: Catalan Team
---

### Post by nickpage on 2009-08-23
Hola companys,

darrerament tinc problemes amb el meu proveidor d'ADSL (Jazztel), i durant el dia tinc talls a la connexió, he de fer cada vegada un reset del router per tenir altre vegada connexió a internet, però l'ubuntu no se'm connecta fins que no el torno a reiniciar, després del reinici ja tinc la connexió, això m'extranya molt perquè tinc un altre PC vell amb un Windows XP i no li cal reiniciar per tenir la connexió a internet. Això em fa pensar que potser per l'Ubuntu cal fer alguna cosa a la configuració o potser he de fer servir alguna instrucció que desconec. Algú sap que puc fer?

Gràcies.

---

### Post by papapep on 2009-08-23
Hi ha un paquet de nom [ifplugd]("http://packages.ubuntu.com/jaunty/ifplugd"), que serveix per a que la connexió de xarxa es configuri o desconfiguri automàticament en funció de si té connectivitat o no, que probablement t'arregli el problema.

Amb un:

```
sudo aptitude install ifplugd
```

el tens instal·lat.

---

### Post by nickpage on 2009-08-24
Gràcies per la resposta però no em va be,

ara quan perdo la connexió a internet i faig un reset del router l'ordinador es queda penjat, i l'he de reiniciar "a la brava".

Puc fer alguna cosa més?

Gràcies.

---

### Post by PatrickVogeli on 2009-08-24
desinstal·la l'ifplugd i, quan reiniciis el router, un cop reiniciat, al network manager clicka per reconnectar-te. El cable en el meu cas es mostra com a eth0.

---

### Post by nickpage on 2009-08-24
Hola Patrick,

quan dius network manager vols dir Sistema->Administració->Eines de xarxa?

és que vaig fins aquí i no veig cap opció de reconectar.

---

### Post by PatrickVogeli on 2009-08-24
no, dic una icona que, en la instalació per defecte, esta a la barra de dalt, a la dreta. Igual tu veus 2 ordinadors o algo aixo. Jo que vaig per wifi veig 4 ratlles que indiquen la qualitat de la connexio

---

### Post by nickpage on 2009-08-24
Ok, si, tinc una icone de connexió, el tema és que després de reiniciar l'ordinador, hi ha l'opció de Habilita la xarxa i està marcada i continuo sense connexió, si desmarco i torno a marcar continuo amb les mateixes.

---

### Post by PatrickVogeli on 2009-08-24
si apretes a sobre, amb el boto esquerre, no el dret, reconecta amb xarxa amb fil. No habilitis / deshabilitis, a veure que pasa.

---

### Post by nickpage on 2009-08-25
Be, ja he trobat la forma de fer-ho després de molts d'intents.

Quan el router queda penjat i no tinc connexió el que he de fer és deshabilitar la xarxa ABANS de reiniciar el router, quan el router ja ha reiniciat és quan habilito la xarxa i ja torno a tenir connexió.
No ho entenc, però cap altra combinació d'accions em permetia tenir la connexió.

Gràcies

---

