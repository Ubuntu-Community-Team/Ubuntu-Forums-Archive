---
title: "m'ha petat ..."
date: 2007-02-19
forum: Catalan Team
---

### Post by roquet on 2007-02-19
Hola companys. resulta que estava actualitzant via internet del kubunt 5.1 al 6.1 i pel que es veu no ho vaig fer bé i ara no s'engega la intarface gràfica, però si per consoloa.

com no tinc massa idea m'agradaria saber que he de fer per recuperar el que tenia, i com a mal menys dolent, si torno a instalar l'ubuntu o kubuntu perdré el que tinc a la partició de windows? (necessito alguns programes que no em funcionen amb el wine)

---

### Post by chalimac on 2007-02-19
Proba escrivint a la consola:

sudo dpkg-reconfigure xserver-xorg

i seleccionant el driver que tenies abans per la teva targeta gràfica. O a males selecciona "vesa" per mirar d'entrar a l'entorn gràfic.

En principi, el que has fet no ha d'afectar la partició de windows. SI ho tornes ha instal·lar, has de vigilar les opcions de l'instal·lador (no formategis ni tornis a fer particions a la partició de windows)

---

### Post by orestesmas on 2007-02-19
Passar de la 5.10 a la 6.10 és potser una mica gran. Segurament l'actualització ha donat errors i com que surten per consola no te n'has assabentat.

Jo faria el següent:
1) Obre una consola
2) Fes "sudo apt-get -f install" i mira els missatges que surten. És probable que hi hagi errors però que instal·li més coses. Prova de fer-ho diverses vegades fins que no dóni més errors o arribis a un punt reiteratiu.
3) En aquest segon cas, el pas següent serà en funció de l'error que et dóni.

També pot ser útil saber perquè no engeguen les X. Prova de teclejar "X" en un terminal i anotar les línies d'error (comencen per "(EE)").

Ja diràs.

Orestes.

---

### Post by roquet on 2007-02-21
moltes gràcies, finalment m'he decidit en refomartejar-me tot el pc, i donar més disc dur a linux, ja que per algunes aplicacions encara necessitaré utilitzar el windows.

---

