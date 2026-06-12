---
title: "[SOLVED] Problema amb els locale"
date: 2007-11-21
forum: Catalan Team
---

### Post by lluis.dalmau on 2007-11-21
Sembla que al fer la instal·lació des de zero de Gusty, la màquina va quedar amb un locale que no li correspon, això em dóna algun problema, com es pot arreglar ?

ldalmau@foratnegre:~$ locale -a
C
ca_AD
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

---

### Post by CarlesOriol on 2007-11-21
A sistema > administració > suport d'idioma

---

### Post by lluis.dalmau on 2007-11-21
Encara hi ha alguna cosa que no tinc controlada, abans em funcionava correctament però ara no.

Hi ha un programa per administrar un router que l'haig de fer córrer amb el Wine, des de la instal·lació de la gusty que s'engega correctament peró enlloc de lletres tots els menús queden amb símbols i és impossible usar-lo

[IMG]http://esparta.dyndns.org/screenshot.png[/IMG]

---

### Post by orestesmas on 2007-11-26
Dissabte passat vaig poder comprovar com el "locale" andorrà donava problemes en una kubuntu: concretament, no es funcionaven les lletres accentuades en les aplicacions KDE.

Canviant-ho per ca_ES.UTF-8 solucionava aquest problema.

Per saber si els teus problemes venen d'aquí, prova d'executar l'aplicació conflictiva des d'un terminal, precedint-la de l'ordre "export LANG=ca_ES.UTF-8"

---

### Post by CarlesOriol on 2007-11-26
Orestes.

Tinc entès que aquest problema el va solucionar en Toni Hermoso ABANS de la gutsy.

Encara no va?

En qualsevol cas la captura de pantalla indica un problema més de tipografies que de joc de caràcters.

---

### Post by orestesmas on 2007-11-26
M'ha semblat entendre que la captura de pantalla i el primer problema eren dues coses diferents, i jo responia només a la primera.

I si, em sona que el Toni Hermoso va parlar dels problemes amb els locale andorrans. No sé si ho van arreglar, però aquest dissabte vam poder comprovar en una kubuntu Gutsy (que segons el Miquel Chicano estava instal·lada de zero) el locale ca_ES anava i el ca_AD no.

---

### Post by CarlesOriol on 2007-11-26
Ok.

Faré una prova aquest cap de setmana de muntar una maquineta de 0 en kde a veure que passa. 

Recordo d'haver-ho parlat amb ell després de la sortida del feisty i que m'havia comentat que ho havia pujat...

---

### Post by CarlesOriol on 2007-11-26
Per cert... OFFTOPIC COM UNA CASA DE PAGES indigne de cap moderador de fòrum:

El KDE 4 té un aspecte xulissim felicitats!

---

### Post by papapep on 2007-11-26
Últimament els offtopics s'estan convertint en els teus tòpics.... L :-D

---

### Post by trinkus on 2007-11-29
Jo puc confirmar que amb una instal·lacio des de zero de la Gutsy el locale andorra donava aquest tipus de problemes. A mi no em deixava escriure accents amb el Kile (KDE). En canviar el locale tot es va arreglar... pero esbrinar-ho em va portar de cap gairebe una nit...

---

### Post by lluis.dalmau on 2007-12-12
He provat d'executar com m'heu comentat però surt amb els mateixos símbols:

ldalmau@foratnegre:~$ export LANG=ca_ES.UTF-8
ldalmau@foratnegre:~$ wine winbox.exe

s'executa igual de malament :(

---

### Post by lluis.dalmau on 2007-12-15
Ja està resolt, m'han comentat :

[I]Sembla un problema amb les fonts. Prova amb:

sudo apt-get install msttcorefonts

Tinc el winbox en un parell de Gutsy funcionant sense problema. En els dos veig que hi tinc instalat aquest paquet.[/I]

Ho he provat i ha sigut oli en un llum !

Gràcies a tots ;)

---

