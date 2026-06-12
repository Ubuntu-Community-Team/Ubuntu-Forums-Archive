---
title: "USB per a vore la tv en el portatil amb el 9.04"
date: 2009-07-15
forum: Catalan Team
---

### Post by dmartinez116 on 2009-07-15
Tinc un Compaq CQ60-125 amb el ubuntu 9.04, i m'agradaria comprar un usb per a vore el tdt i que siga compatible amb ubuntu. Algú em pot recomanar algun que estiga fent servir un d'estos aparells amb el seu portàtil i l'ubuntu 9.04.

Moltes gràcies.

---

### Post by papapep on 2009-07-15
Jo fa molt temps, com tres anys, que faig servir un Avermedia Volar  (model "A808"). Probablement ja no el venguin, però també es probable que tingui algun digne successor.
Al principi havia de compilar el controlador a cada canvi de versió, però ja fa tres o quatres versions que no cal, ja el reconeix directament el sistema.

---

### Post by dafaktor on 2009-07-15
Ara que en papapep anomena les avermedia, jo tinc una AverMedia Hybrid i no he aconseguit fer-la funcionar.

Però compte, hi ha dos models d'aquesta Aver, la A16R sembla funcionar correctament i la A16D, que és la que tinc jo, no.

Per si ho vols tenir en compte...

---

### Post by orestesmas on 2009-07-16
Jo tinc un USB d'aquests de la marca Hauppauge model WinTV, i va força bé. Porta una antena petitona però a la zona on estic la recepció no és molt bona (edificis, arbres, etc...) i em cal usar una antena exterior, però si el senyal és bo, no hi ha problema.

Per veure els programes, uso el Kaffeine.

---

### Post by dmartinez116 on 2009-07-16
Gràcies, papapep, buscaré el model a vore si el trove.

dafaktor, crec que parles de pci. Jo també tinc la A16D i encara que ho he provat de valent tampoc l'he fet funcionar al fixe de sobretaula.

orestesmas, pots dir-me el model concret del USB que tens i si fa molt de temps que el vas comprar?

Gracies a tots.

---

### Post by orestesmas on 2009-07-16
> **dmartinez116 said:**
> orestesmas, pots dir-me el model concret del USB que tens i si fa molt de temps que el vas comprar?

Gracies a tots.

És un **Hauppauge WinTV Nova-T-Stick**. Pots veure'n una foto [aquí]("http://ofertastutiplen.blogspot.com/2008/03/sintonizador-tdt-usb-hauppauge-wintv.html") (no faig propaganda, és el primer enllaç que he trobat cercant al google).

Per cert, en aquest tipus d'aparells una font d'informació essencial és [linuxtv.org]("http://www.linuxtv.org/"). Entre altres informacions interessants, al seu wiki hi pots trobar una [llista de dispositius DVB-T]("http://www.linuxtv.org/wiki/index.php/DVB-T_Devices") (és a dir, TDT) USB suportats (i no suportats) per Linux. Tingues en compte, però, que a vegades marques i models diferents utilitzen internament la mateixa electrònica, i per tant pot ser que molts dispositius estiguin suportats encara que no estiguin en aquesta llista. També pot passar que versions successives del mateix producte siguin diferents internament. En fi, un cacau. Mira't aquesta llista, que és força útil.

---

### Post by lorencillo on 2009-07-17
> **orestesmas said:**
> Jo tinc un USB d'aquests de la marca Hauppauge model WinTV, i va força bé. Porta una antena petitona però a la zona on estic la recepció no és molt bona (edificis, arbres, etc...) i em cal usar una antena exterior, però si el senyal és bo, no hi ha problema.

Per veure els programes, uso el Kaffeine.


Hola a tots,

jo també tinc un Hauppauge per veure la tele, ja he buscat informació per intentar configurar correctament el usb per veure la tele... pero no hi ha manera. :confused:

Pot indicar com configures el Keffeine per veure-la, aquesta tarda-nit ho provo... gràcies.:D

---

### Post by orestesmas on 2009-07-18
> **lorencillo said:**
> Hola a tots,

Pot indicar com configures el Keffeine per veure-la, aquesta tarda-nit ho provo... gràcies.:D

Si tens el receptor connectat al USB, en obrir el kaffeine ja el reconeix automàticament i a la pantalla principal apareix un botó "TV digital" i també un menú addicional "DVB".

El primer que has de fer és escollir l'estació emissora. Ves al menú "DVB" i escull l'última opció "Configura la DVB". En les opcions del dispositiu escull la Font "es-Collserola" (o la que convingui en el teu cas). També pots deixar-la a AUTO, però això obliga al programa a fer passes addicionals, cosa que no cal.

A continuació s'ha de fer un escaneig dels canals. Vas al menú "DVB -> Canals" i esculls el botó "Comença l'exploració". Els canals que va trobant queden a la dreta (a la llista "Trobats"), i en acabat selecciona els que vulguis i traspassa'ls a la llista de l'esquerra ("Canals"). Aquests últims són els que tindràs disponibles per escollir a l'hora de mirar-los.

Fet això, a la pantalla principal del Kaffeine prem el botó "TV Digital" i fes doble clic a qualsevol canal de la llista de l'esquerra. S'hauria de començar a veure immediatament. Doble clic a la pantalla la maximitza.

Que vagi bé.

---

### Post by dmartinez116 on 2009-07-31
Ara en app tenen el Hauppage wintv ministick hd, algú el te o sap si funcionarà amb el 9.04?

He buscat a la xarxa i no he tret una conclusió clara.

---

### Post by Rubunter on 2009-08-01
> **orestesmas said:**
> Si tens el receptor connectat al USB, en obrir el kaffeine ja el reconeix automàticament i a la pantalla principal apareix un botó "TV digital" i també un menú addicional "DVB".

El primer que has de fer és escollir l'estació emissora. Ves al menú "DVB" i escull l'última opció "Configura la DVB". En les opcions del dispositiu escull la Font "es-Collserola" (o la que convingui en el teu cas). També pots deixar-la a AUTO, però això obliga al programa a fer passes addicionals, cosa que no cal.

A continuació s'ha de fer un escaneig dels canals. Vas al menú "DVB -> Canals" i esculls el botó "Comença l'exploració". Els canals que va trobant queden a la dreta (a la llista "Trobats"), i en acabat selecciona els que vulguis i traspassa'ls a la llista de l'esquerra ("Canals"). Aquests últims són els que tindràs disponibles per escollir a l'hora de mirar-los.

Fet això, a la pantalla principal del Kaffeine prem el botó "TV Digital" i fes doble clic a qualsevol canal de la llista de l'esquerra. S'hauria de començar a veure immediatament. Doble clic a la pantalla la maximitza.

Que vagi bé.

Merci per la informació company. Em van regalar la teva mateixa targeta per Nadal i per falta de temps no m'havia assegut a intentar fer-la anar.
He provat el que comentes i funciona perfectament. Tinc poca senyal i veig pocs canals, però ja és prou.
La pregunta que et vull fer jo és si et funciona el comandament a distància.Jo el provo i no dona senyals de vida.

Gràcies

---

### Post by orestesmas on 2009-08-01
> **Rubunter said:**
> 
La pregunta que et vull fer jo és si et funciona el comandament a distància.Jo el provo i no dona senyals de vida.
Gràcies

La veritat és que no l'he provat (no m'ha calgut), però segons [aquest post]("http://javierarias.wordpress.com/2008/07/01/hauppauge-wintv-nova-t-stick-y-mando-a-distancia-funcionando-¡por-fin/"), hauria de funcionar. L'únic que cal fer és configurar una mica el sistema descodificador d'infrarojos del GNU/Linux.

Salutacions.

---

### Post by dmartinez116 on 2010-09-14
> **dafaktor said:**
> Ara que en papapep anomena les avermedia, jo tinc una AverMedia Hybrid i no he aconseguit fer-la funcionar.

Però compte, hi ha dos models d'aquesta Aver, la A16R sembla funcionar correctament i la A16D, que és la que tinc jo, no.

Per si ho vols tenir en compte...

dafaktor, amb el 10.04 m'ha funcionat la sintonitzadora A16D d'avermedia... Més val tard que mai...

David.

---

