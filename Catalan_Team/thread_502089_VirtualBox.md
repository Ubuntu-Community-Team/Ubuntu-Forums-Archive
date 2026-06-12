---
title: "VirtualBox"
date: 2007-07-16
forum: Catalan Team
---

### Post by prostata on 2007-07-16
He instal-lat des de synaptic VirtualBox, però tinc unes dubtes:
Segons aquest manual [http://www.kriptopolis.org/virtualbox-ii-windows-fundamentals-bajo-linux](http://www.kriptopolis.org/virtualbox-ii-windows-fundamentals-bajo-linux) sembla que hi ha un moment en que es produeix un "format", ¿es sobre la màquina virtual o sobre el disc dur?, el dimensionament també?, ¿on és virtualbox, no el veig per en lloc, s'ha d'arrencar des de terminal?

Bé moltes gràcies i si en conegueu un altre manual més bo, doncs gràcies

---

### Post by prostata on 2007-07-16
A veure, haig de ser més específic:

Tinc instal-lat al disc dur, tant win-XP, com la feysti. Quan vull wXP, faig un reset i treballo amb WXP. Dins WXP, faig servir Daemon-Tools. Al meu dubte es:

Un cop configurat virtualbox, aquest treballa com el Daemon-Tols, es dir de forma virtual??

Gràcies

---

### Post by papapep on 2007-07-16
El virtualbox el tens a Aplicacions > Eines del sistema, hauries de tenir una entrada que es diu "innotek VirtualBox".
I el virtualbox et permet tenir un sistema operatiu dins un altre. 
Quan tu l'executis, i instal·lis el sistema operatiu que vulguis dins el virtualbox, veuràs que dins una finestra tens un altre sistema operatiu real el qual es pensa que està solet en una màquina real.
Si és a això al que tu et refereixes com a virtual, sí, és una abstracció (virtualització) del maquinari d'un sistema informàtic.

---

### Post by prostata on 2007-07-16
> **papapep said:**
> El virtualbox el tens a Aplicacions > Eines del sistema, hauries de tenir una entrada que es diu "innotek VirtualBox".
I el virtualbox et permet tenir un sistema operatiu dins un altre. 
Quan tu l'executis, i instal·lis el sistema operatiu que vulguis dins el virtualbox, veuràs que dins una finestra tens un altre sistema operatiu real el qual es pensa que està solet en una màquina real.
Si és a això al que tu et refereixes com a virtual, sí, és una abstracció (virtualització) del maquinari d'un sistema informàtic.

Gràcies papapep:
el que jo vull no es altre cosa que per mitja de virtualbox, es pasar d'ubuntu a wxp i viceversa, sense necessitat de fer un reset. Com he dit ja tinc instal-lat els dos SO, i això es tot, d'ubuntu a wxp i viceversa. ¿es possible?...gràcies

---

### Post by papapep on 2007-07-16
> el que jo vull no es altre cosa que per mitja de virtualbox, es pasar d'ubuntu a wxp i viceversa, sense necessitat de fer un reset
Doncs amb virtualbox, el que podràs tenir és una màquina virtual Windows Xp dins l'Ubuntu la qual tu executaràs i tancaràs a voluntat igual que un programa qualsevol.
El que has de fer és crear la màquina virtual nova amb el virtualbox i instal·lar-hi el WXP i els programes que et plaguin.

---

### Post by prostata on 2007-07-16
> **papapep said:**
> Doncs amb virtualbox, el que podràs tenir és una màquina virtual Windows Xp dins l'Ubuntu la qual tu executaràs i tancaràs a voluntat igual que un programa qualsevol.
El que has de fer és crear la màquina virtual nova amb el virtualbox i instal·lar-hi el WXP i els programes que et plaguin.

company, això no ho entenc:

crear la màquina virtual nova amb el virtualbox i instal·lar-hi el WXP 

jo ja tinc instal-lat wxp, per tant, que vol dir, que l'haig d'instal-lar de nou el wxp??

salut

---

### Post by papapep on 2007-07-16
Clar. Una màquina virtual és una mena de "fitxer" que s'executa dins uns sistema operatiu real i una màquina real, per a enganyar al sistema operatiu que s'instal·la dins la màquina virtual (en el teu cas XP) per a no haver de reiniciar l'OS cada cop que el vols executar. Dins l'entorn "virtual" que el virtualbox crea al fitxer, l' XP es pensa que està solet en una ordinador real. (per això es diu màquina virtual)
Evidentment, amb aquest plantejament, has de tornar a instal·lar l'XP, i tots els programes que hi tens i vols seguir tenint. Però pensa que POTS ESBORRAR EL WINDOWS D'ON EL TENS. 
A partir d'aquí, pots tenir la màquina virtual en un disc dur extraïble, un pendrive USB, un DVD (si no hi has d'escriure res), etc...un nou món s'obre ;)

---

### Post by prostata on 2007-07-17
> **papapep said:**
> Clar. Una màquina virtual és una mena de "fitxer" que s'executa dins uns sistema operatiu real i una màquina real, per a enganyar al sistema operatiu que s'instal·la dins la màquina virtual (en el teu cas XP) per a no haver de reiniciar l'OS cada cop que el vols executar. Dins l'entorn "virtual" que el virtualbox crea al fitxer, l' XP es pensa que està solet en una ordinador real. (per això es diu màquina virtual)
Evidentment, amb aquest plantejament, has de tornar a instal·lar l'XP, i tots els programes que hi tens i vols seguir tenint. Però pensa que POTS ESBORRAR EL WINDOWS D'ON EL TENS. 
A partir d'aquí, pots tenir la màquina virtual en un disc dur extraïble, un pendrive USB, un DVD (si no hi has d'escriure res), etc...un nou món s'obre ;)

Estimat company: gràcies per tota la teva info. sobre les màquines virtuals. Ja ho sabia però de totes totes moltes gràcies pel teu interès. A mi el que em sorpren, es que si ja tinc instal-alt wxp, l'hagi de des instal-lar  i tornar-lo a instal-lar amb el virtualbox. A mi em semblaria molt més útil que qualsevol programa d'aquesta mena, ja en reconegues directament tot el que hi és al disc dur, SO em refereix-ho. Perquè si no fer els procediments de des instal-lació  d'un SO, i desprès tornar a fer novament l'insta. via VB o d'altre, em sembla una mica "¿ferragos"?.

Bé, si de cas ja m'ho pensaré, sobre tot per la part "ferragosa", creia que era més "amigable". Com et deia jo a WXP faig anar el Daemons Tools, que com saps crea una unitat virtual, per fer el que vulguis amb aquesta unitat. Creia jo, erradament, que crear una màquina virtual seria quelcom fàcil com Daemon Tools, en quant a concepte, però segur que potser es que els conceptes son diferents.

Gràcies

---

### Post by eselma on 2007-07-17
> **prostata said:**
> ...  A mi el que em sorpren, es que si ja tinc instal-alt wxp, l'hagi de des instal-lar  i tornar-lo a instal-lar amb el virtualbox. A mi em semblaria molt més útil que qualsevol programa d'aquesta mena, ja en reconegues directament tot el que hi és al disc dur, SO em refereix-ho. Perquè si no fer els procediments de des instal-lació  d'un SO, i desprès tornar a fer novament l'insta. via VB o d'altre, em sembla una mica "¿ferragos"?.

Bé, si de cas ja m'ho pensaré, sobre tot per la part "ferragosa", creia que era més "amigable". Com et deia jo a WXP faig anar el Daemons Tools, que com saps crea una unitat virtual, per fer el que vulguis amb aquesta unitat. Creia jo, erradament, que crear una màquina virtual seria quelcom fàcil com Daemon Tools, en quant a concepte, però segur que potser es que els conceptes son diferents.


Els sistemes MS-Windows, en general són "autistes": és a dir, que es pensen que són l'únic S.O. a l'ordinador i que no en calen d'altres. Una bona prova d'això és que al reinstal·lar-los acostumen a esborrar tot el que hi hagi al MBR i se situen com "l'únic i verdader" S. O. D'altra banda, qualsevol S.O. instal·lat directament sobre una màquina física veu també tots els perifèrics físics directament (discos durs, tarja gràfica, teclat, ratolí, etc). 

En canvi, si el mateix S.O. s'instal·la en una màquina virtual els perifèrics que veu són uns altres genèrics, simulats per la màquina virtual. El disc dur real pot tenir una arquitectura determinada (ext3fs) i 200 GB de capacitat, però el virtual potser només té 4 GB i és del tipus FAT32: en realitat és un fitxer que simula el disc virtual. La pantalla real potser té una geometria de 1280 x 1024, però la virtual és més petita, de 1024 x 768 i fins i tot dimensions no estàndard. Per això cal instal·lar aquest S.O. virtualitzat d'acord amb el nou "maquinari virtual" i segurament també amb nous controladors. Quan instal·les les extensions de VirtualBox, en realitat afegeixes nous controladors que li permeten al ratolí esbrinar si està en "zona VirtualBox" o "zona màquina física", per exemple, donar-li més velocitat a la representació gràfica, etc. 

Per això no fa ús del programari instal·lat en qualsevol altra partició (que potser ni veu), perquè segurament no li resultaria útil. Tanmateix, hi ha alguns conversors (crec que VMWare en té un) que poden fer, des de dins del S.O. a "clonar" (que ha de ser MS-Windows) una màquina virtual amb el programari que hi tens instal·lat, suposo que amb nous controladors. No l'he provat (entre altres coses perquè fa temps que vaig esborrar la partició MS) i no sé si cal fer alguns ajustos posteriors. Alguna vegada he sentit a dir que tant VMWare com VirtualBox poden fer ús d'una partició física tal com tu volies, però sempre amb l'afegit que és una operació perillosa i no massa aconsellable. 

He provat VirtualBox i m'agrada més que VMware, però en el meu cas cal que usi aquest darrer perquè amb VirtualBox no he sabut activar de manera adequada el port sèrie (que és l'única necessitat que encara tinc del programari de Redmond).

---

### Post by CarlesOriol on 2007-07-17
A més cal pensar que l'xp detectaria un canvi important de maquinari que bloquejaria la llicència.

---

### Post by prostata on 2007-07-17
> **eselma said:**
> Els sistemes MS-Windows, en general són "autistes": és a dir, que es pensen que són l'únic S.O. a l'ordinador i que no en calen d'altres. Una bona prova d'això és que al reinstal·lar-los acostumen a esborrar tot el que hi hagi al MBR i se situen com "l'únic i verdader" S. O. D'altra banda, qualsevol S.O. instal·lat directament sobre una màquina física veu també tots els perifèrics físics directament (discos durs, tarja gràfica, teclat, ratolí, etc). 

En canvi, si el mateix S.O. s'instal·la en una màquina virtual els perifèrics que veu són uns altres genèrics, simulats per la màquina virtual. El disc dur real pot tenir una arquitectura determinada (ext3fs) i 200 GB de capacitat, però el virtual potser només té 4 GB i és del tipus FAT32: en realitat és un fitxer que simula el disc virtual. La pantalla real potser té una geometria de 1280 x 1024, però la virtual és més petita, de 1024 x 768 i fins i tot dimensions no estàndard. Per això cal instal·lar aquest S.O. virtualitzat d'acord amb el nou "maquinari virtual" i segurament també amb nous controladors. Quan instal·les les extensions de VirtualBox, en realitat afegeixes nous controladors que li permeten al ratolí esbrinar si està en "zona VirtualBox" o "zona màquina física", per exemple, donar-li més velocitat a la representació gràfica, etc. 

Per això no fa ús del programari instal·lat en qualsevol altra partició (que potser ni veu), perquè segurament no li resultaria útil. Tanmateix, hi ha alguns conversors (crec que VMWare en té un) que poden fer, des de dins del S.O. a "clonar" (que ha de ser MS-Windows) una màquina virtual amb el programari que hi tens instal·lat, suposo que amb nous controladors. No l'he provat (entre altres coses perquè fa temps que vaig esborrar la partició MS) i no sé si cal fer alguns ajustos posteriors. Alguna vegada he sentit a dir que tant VMWare com VirtualBox poden fer ús d'una partició física tal com tu volies, però sempre amb l'afegit que és una operació perillosa i no massa aconsellable. 

He provat VirtualBox i m'agrada més que VMware, però en el meu cas cal que usi aquest darrer perquè amb VirtualBox no he sabut activar de manera adequada el port sèrie (que és la única necessitat que encara tinc del programari de Redmond.

gràcies per ampliar l'info. el que passa es que jo tinc un determinat soft astronòmic a wxp, que només funciona sota wxp. no hi ha equivalents en linux, per això se'm fa...bufff!!! tornar a instal-lar tot novament. si de cas esperaré un hipotètic "moment de caos" i a les hores ja no tindré més remei....de qualsevol forma moltes gràcies, ja tinc un bon manual sobre VB i si arriba el moment, ja ho faré....

salut

---

