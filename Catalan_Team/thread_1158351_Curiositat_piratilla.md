---
title: "Curiositat piratilla"
date: 2009-05-13
forum: Catalan Team
---

### Post by PatrickVogeli on 2009-05-13
Hola gent!

La següent pregunta potser no és molt ética i no estarà molt ben vista, però tinc la curiositat..

La meva impressora, una canon iP3000, funciona de meravella amb els drivers integrats a l'ubuntu, l'únic que li trobo a faltar és, si de cas, poder veure l'estat dels cartutxos, que tampoc es que m'importi massa, però bé.

Hi ha el programa [turboprint]("www.turboprint.info") que ho implementa pràcticament tot, però que evidenment paso de pagar.

Bé, el que em "molesta" és el fet de no saber com cony fan aquests tios per a que, desprès d'instal·lar-lo i havent-lo borrat (dpkg --purge i borrant manualment el que queda), segueix fixant la data final de demo al tornar-lo a instal·lar.

Algú se li acut res? Podria ser que miressin d'alguna manera quan es va instal·lar el seu paquet per primera vegada a la base de dades de l'apt? Aquesta base de dades la puc consultar jo mateix? 

Se us acut alguna cosa?

Es mera curi

---

### Post by tanreb20 on 2009-05-13
Quants no ens hem fet aquesta pregunta!

AMb el croosover hem passa el mateix!

Ara especulo, pero hi ha un arxiu que conté la informació de TOTS els programes instalats, desinstalats etc...

Suposu que esborrant el programa d'aquell arxiu es podria fer...

Ja buscaré quin és!

---

### Post by tanreb20 on 2009-05-13
T'envio un PM ok?

---

### Post by PatrickVogeli on 2009-05-13
ja ho provat pero res... es una mera referencia a que s'ha instal·lat el programa, pero no diu res d'hora ni fitxers ni res.. a seguir buscant!

---

### Post by kimet on 2009-05-14
> Algú se li acut res? Podria ser que miressin d'alguna manera quan es va instal·lar el seu paquet per primera vegada a la base de dades de l'apt? Aquesta base de dades la puc consultar jo mateix?


Aquests programes solen deixar un script quan els desinstal.les, busca'l per "/var/lib/dpkg/info" amb la extensió ".postinst".

Salut.

---

### Post by PatrickVogeli on 2009-05-15
ningu més té curiositat? Només en kimet i jo?

Jo li segueixo donant voltes i ni idea. Al windows normalment hi ha entrades de registres i coses aixi... pro a l'ubuntu?

---

### Post by guillemsola on 2009-05-16
Això demostra que no val la pena instal·lar aquest tipus de programes. Ja han deixat llufes al sistema que no pots arribar a controlar. Si cada programa fes el mateix en quatre dies ja estàs formatejant i reinstal·lant de nou.

Està clar que si linux fos un SO majoritari serien els fabricants de software  els que el desgraciarien amb les seves "aportacions".

salut!

---

### Post by enricXIII on 2009-05-16
Totalment d'acord amb l'angrychai. Des del moment enque qualsevol programa prèn el domini i no el pots controlar de cap manera...queda descartat de qualsevol possibilitat de que jo el faci servir. Si de cas ho faria amb un pindows...que si peta tant si val, tard o d'hora acabaria petant igualment!:p
Entenc, de totes maneres, la curiositat..si se m'acut res o faré saber!
Salut!

---

### Post by CarlesOriol on 2009-05-17
Jo també estic d'acord amb els comentaris anteriors... però ja que hi som anem a jugar una mica.

El primer és descobrir com desa la informació de la instal·lació.

Jo començaria fent el següent: executaria el programa amb alguna eina de debug com pot ser el strace per veure les crides al sistema. (per cert per crackejar windows cercar al registre a cegues és una mala idea -excepte si sols poses directament la solució - el que cal fer sempre és monitorejar l'activitat del programa al registre.)

[FONT="Courier New"]strace -o surt.txt nomdelprograma[/FONT]

entrant i sortint ràpidament a fi que la llista (surt.txt) no es torni massa gran (tot i això serà prou gegantina)

Un cop fet això assumiria que el programa desa la configuració en algun arxiu, per tant cal arremangar-se i començar a llegir el resultat d'alguna cosa com:

[FONT="Courier New"]cat surt.txt | grep open > surt2.txt
gedit surt2.txt[/FONT]

si existeix algun tipus de comptador ... també pots fer:

[FONT="Courier New"]cat surt.txt | grep O_RDWR[/FONT]

... ara si el programa està instalat en mode usuari et serà més fàcil identificar els arxius propis d'ell...

au...

Ara et deixo seguir, comenta com et va.

---

### Post by PatrickVogeli on 2009-05-23
Sento per haver tardat tant en contestar!!

fent l'strace no he vist res anormal, pero clar, hi ha el problema de que quan faig un strace turboprint el strace es tanca amb un segmentation fault, aixi que... tampoc puc mirar molt.

He provat a fer el strace de la instal·lació, però passa el mateix, no hi veig res.

En fi.. putos programes! xD

Merci igualment CarlesOriol!

---

### Post by jdk9 on 2009-05-30
Edito el misstage per tal de corregir-lo.

Demano disculpes per l'enlllaç, no tornarà a passar

---

### Post by papapep on 2009-05-30
Senyors, aquí **[COLOR="Red"]NO[/COLOR]** es pot fer això. Hi ha multitud de llocs per a fer-ho.

---

