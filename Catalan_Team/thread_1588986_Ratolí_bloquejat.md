---
title: "Ratolí bloquejat"
date: 2010-10-05
forum: Catalan Team
---

### Post by Rafael Carbonell on 2010-10-05
Hola, 
M'acabo de passar a l'ubuntu, després que se'm passés el pànic de no conèixer ningú amb qui compartir els problemes.
 i... alguna cosa m'ha bloquejat el funcionament del ratolí (d'aquells  d'endoll rodó, com els d'abans), però afortunadament funciono  alternativament amb un de port USB
Quan incio amb windows, a la 2a vegada, SÍ que em funciona el ratolí normal
Però si entro a l'ubuntu, abans d'aparèixer les lletres de ubuntu amb  els cinc piquets vermells a sota, una finestra em diu que s'ha bloquejat  nosé què.

Hi ha alguna solució?

Gràcies per endavant per la vostra resposta.

---

### Post by wgarcia on 2010-10-06
El primer que pots provar, tot i que soni xorra, és desendollar i tornar a endollar el ratolí a veure si comença a funcionSar.

Si continua sense funcionar, prova d'instal·lar un parell de coses que serveixen per detectar aquest tipus de ratolins. Per instal·lar-lo pots fer-lo a través d'una terminal, si ho saps fer, i sinó fer ALT-F2 i entrar el següent:

sudo apt-get install --reinstall xserver-xorg-input-mouse mdetect xbase-clients

Et demanarà la teva clau. A veure si a partir d'instal·lar aquests paquests addicionals comença a funcionar, i sinó continua posat en el fòrum el que et diu, a veure si algú finalment pot arribar a la solució.

---

### Post by Rafael Carbonell on 2010-10-06
Gràcies wgarcia, provaré això que dius de prémer ALT+F2 i escriure aquell codi, però en quin moment ho haig de fer, un cop a dins de ubuntu...?

---

### Post by Rafael Carbonell on 2010-10-06
Molt bé, el que m'has dit ha funcionat:).... però ara no hi puc escriure la contrassenya:(

---

### Post by wgarcia on 2010-10-07
La instrucció amb ALT-F2 l'has d'aplicar un cop estiguis dins l'escriptori.

O sigui, has pogut entrar ALT-F2 i la instrucció, i el ratolí ha començat a funcionar, o no has arribat a poder fer-ho perquè et demana la contrassenya i no la pots entrar?

---

### Post by Rafael Carbonell on 2010-10-07
Mercès de nou....


He pogut entrar ALT-F2 i la instrucció, i aleshores em demanava la contrassenya
però no em deixava escriure-hi: hi sortia una mena de cursor, però no podia.
Obrint altres coses si podia escriure-hi.

Rafael

---

### Post by wgarcia on 2010-10-08
Bé, una altra manera de fer-ho és obrint una "terminal", que és una espècie de consola on pots entrar instruccions d'aquest tipus. Si ho vols tornar a provar clica al menú Aplicacions -> Accessoris -> Terminal, i a la finestra que s'obre entra 

sudo apt-get install --reinstall xserver-xorg-input-mouse mdetect xbase-clients

i quan et demani la contrassenya després de donar-li a l'intro, entra-la.

---

