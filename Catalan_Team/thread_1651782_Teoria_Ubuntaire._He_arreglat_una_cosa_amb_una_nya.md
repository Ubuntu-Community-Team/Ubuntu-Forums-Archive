---
title: "Teoria Ubuntaire. He arreglat una cosa amb una nyapa. I ara què?"
date: 2010-12-23
forum: Catalan Team
---

### Post by lpargemi on 2010-12-23
Hola

Us demano una mica de paciència i de pedagogia. Hem resolt un problema amb una nyapa, però que de moment funciona. El cas en concret és aquest: [http://ubuntuforums.org/showthread.php?t=1640907]("http://ubuntuforums.org/showthread.php?t=1640907"), però a aquest fil no m'interessa aquest problema en particular sinó entendre les conseqüències que es deriven de fer servir la solució. No serà pitjor el remei que el mal?

Per solucionar el problema hem acabat descarregant directament d'una pàgina un fitxer, que és el que estem fent funcionar enlloc del que ve al repositori d'Ubuntu. En concret és una mena de flashplayer, per a 64 bit, anomenada "Adobe Flash Square". 

La primera qüestió és que amb això ens refiem de la font d'on l'hem tret. Ja sabem que no hi ha Ubuntu al darrera per garantir la bona fe del paquet.

Una altra és que jo no he explicat de cap manera al "synaptic" ni a la seva base de dades que he canviat el programa instal·lat. Per tant m'imagino que quan hi hagi una actualització del primer programa, si la valido se'm canviarà el programa que jo he copiat, i potser torni a no funcionar. Això vol dir que en principi no he d'acceptar les actualitzacions d'aquest programa, i que si n'hi hagués del nou hauria de seguir-ho jo de tant en tant. N'hi hauria prou desinstal·lant-lo? 

Es suposa que a cada canvi de versió dels programes que s'hi relacionen jo hauria de provar de nou així "a mà" (és a dir no en automàtic) a veure com queda?

Com es suposa que hauríem de seguir, així de forma genèrica, sense entrar en particularitats? (Si és que te sentit el plantejament)

Agraït

Lluís

---

### Post by kimet on 2010-12-23
El paquet que ve amb ubuntu,igual que aquest que has descarregat, son programes de codi tancat, per tant, tan poc confiable es un com l'altre.

desinstal·la el dels repositoris si no et va bé, no hi ha mes problema.


Salut.

---

### Post by PatrickVogeli on 2010-12-24
tal com t'han dit, en aquest cas es igual, el codi es tancat i tant el que te l'ubuntu com aquest surten del mateix lloc, encara que en versions diferents.

Desintal·la el flash des de el synaptic i instal·la el que ja t'has posat i no tindras problemes. Synaptic no en sabra res i no te l'actualitzara, pero no tindras cap problema de funcionament ni res.

salut

---

### Post by lpargemi on 2010-12-24
Gràcies als dos pel comentaris, ja he desinstal·lat el del synaptic (el dels repositoris). 

Entenc que des d'ara enlloc d'esperar les actualitzacions automàtiques -que van tan bé!- caldrà que miri regularment al lloc d'on he tret el programa per veure si hi ha canvis. O hi ha una altra manera de fer-ho?

Lluís

---

### Post by wgarcia on 2010-12-24
Pots mirar si algú manté un dipòsit de programari PPA amb aquesta versió més actualitzada. Si n'hi ha, llavors afegint aquest depòsit amb 

sudo add-apt-repository ppa:...

i instal·lant aquesta versió, ja queda actualitzable si algú manté aquest dipòsit.

---

### Post by kimet on 2010-12-24
Una altra cosa útil que podries fer es reportar el bug, i com l'has sol.lucionat, si no ho ha estat ja, i a part de col.laborar amb la comunitat, es possible trobis mes properament aquesta versió als repositoris.

Salut.

---

### Post by PatrickVogeli on 2010-12-24
aixo del bug no caldra fer-ho. Primer, perque no crec que es puguin enviar bugs sobre el funcionament de programes dels quals ubuntu en té el codi, i segon perque la solucio es instal·lar una versio mes nova que esta en fase beta i la versio anirà cambiant mes o menys ràpidament.

Per últim: aixo no és una nyapa! ;)

---

### Post by kimet on 2010-12-24
Dons si que que es pot fer, una cosa es el binari d'adobe i una altra es el paquet compil.lat que hi ha als repositoris, (pots consultar els bugs que hi ha reportats sobre flashplayer-nonfree). que depèn d'un o uns mantenidors que pot ser-lis d'utilitat la informació que els hi donem.

Encara que la versió pot estar en experimental i pot entrar en un futur, si es útil la informació sobre incompatibilitats que podem proporcionar.

---

