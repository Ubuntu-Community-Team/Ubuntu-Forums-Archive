---
title: "Actualitzacions"
date: 2008-12-11
forum: Catalan Team
---

### Post by jaff77 on 2008-12-11
Hola sóc nou amb això del linux i l'ubuntu. Quant a les actualitzacions, com ho he de fer? les que posa actualitzacions de seguretat importants les puc posar sense mirar? i les recomanables, convé posar-les o només si me fan falta?

---

### Post by tanreb20 on 2008-12-11
Hola!

Benvingut jaff77 al ubuntu! Esperem que t0agradi.

En quant a les actualitzacions, jo et recomano que si ni has tocat les fonts de programarti les instalis totes.

Una altre cosa es si has retoat les fonts de programari i has activat els backports doncs si.. llavors vigila.

Per en principi no hi ha problema!

---

### Post by oriolsbd on 2008-12-11
Hola,

Hauries de deixar activades les "actualitzacions de seguretat importants" (intrepid-security) i les "actualitzacions recomanades" (intrepid-updates).

Les "actualitzacions disponibles abans del seu alliberament" (intrepid-proposed), jo no les tinc activades. Normalment no dónen problemes, però algun cop m'ha entrat alguna actualització d'aquestes que m'ha provocat errors (encara que no massa greus) en algun programa. No m'ha passat massa vegades, però vaig decidir desactivar-les (ja venen desactivades de manera predeterminada). És qüestió de gustos.

Per últim, hi ha les actualitzacions no suportades (intrepid-backport). Aquestes són una mica més delicades que les proposed. Jo et recomanaria no activar-les (excepte si vols tenir l'última versió dels programes, encara que no hagin estat massa provats).

Salutacions,

---

### Post by jaff77 on 2008-12-12
Gràcies. Esper quedar-me a l'ubuntu. Ja he renegat del Windows i tots els seus desastres...

---

### Post by jaff77 on 2008-12-12
OK, però ara per tenir la versió 3.0 d'openoffice he afegit els repositoris

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

I ara al gestor d'actualitzacions me surten les actualitzacions d'openoffice però amb l'avís de que estic a punt d'instal·lar programari que no es pot autenticar i que algú pot danyar o fer-se amb el control del sistema.
Potser falten les claus per firmar el software?

---

### Post by papapep on 2008-12-12
Un tema diferent requereix un fil nou.

---

### Post by RainCT on 2008-12-14
> **jaff77 said:**
> Potser falten les claus per firmar el software?

El paquet de l'OpenOffice.org 3.0 està en una PPA (Personal Package Archive) del [Launchpad](https://launchpad.net), i aquestes no permet signar els paquets (tot i que està previst que, per fi, d'aquí a unes setmanes sí que els signin).

---

