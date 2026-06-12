---
title: "[SOLVED] Actualització"
date: 2007-09-27
forum: Catalan Team
---

### Post by Curial on 2007-09-27
A Maria!

Avui he actualitzat l'ubuntu con sempre i m'ha avisat que l'actualització no estava autenticada. (m'avisava que pot haver el risc que algú altre prengui el control de l'ordinador propi).

Les opcions que em surten son "NO AUTENTICAT" I "PER ACTUALITZAR".

Les preguntes són: Podem passar de les actualitzacions sense autenticar, en aquest cas quedaran pendents per les pròximes actualitzacions?

Passa res si actualitzo integrament els paquets que apareixen, sense preocupar-me? Gairebé mai miro que és el que estic actualitzant!

Interpreto que si selecciono l'opció "no autenticat" me'ls instalarà tots. És correcte?

Gràcies i perdoneu tantes preguntes que a alguns us semblaran una obvietat.

Salut i Ubuntu a tots.

---

### Post by Ferri on 2007-09-27
No estic massa segur perquè, però és un problema que passa de tant en tant. A vegades canviant de servidor desapareix i d'altres en uns dies.
En principi, si no has canviat res al teu sources.list, és poc probable que hi hagi cap problema real i, per tant, és raonablement segur intal·lar aquests paquets igualment.
Si tens algun dubte, però, millor no els instal·lis. Si et funciona bé el sistema, tampoc passa res per no tenir la darreríssima versió i, com ja he dit, normalment en pocs dies s'arregla sol.

---

### Post by CarlesOriol on 2007-09-27
No autenticat ens avisa que hem afegit un paquet per insta&#320;lar / actualitzar del que no podem comprovar-ne la procedència.

Això passa quan afegim altres fonts al sources.list i no afegim les clau digitals necessàries per validar-ne la informació.

És important tenir-ho en compte, ja que és l'unica forma de saber del cert que el paquet està fet per el repositori en el que confiem. Imagineu que algú peta un web on hi ha un repositori que tenim al sources.list i canvia el contingut dels paquets per agafar el control del nostre ordinador. L'insta&#320;lador li donarà tots els permisos i confiances i nosaltres no sabrem mai que ens ha passat.

Per tant... sempre que afegiu una font de tercers cerqueu-ne les signatures digitals.

---

### Post by Curial on 2007-09-28
Gràcies per l'aclariment.

Salut.

---

