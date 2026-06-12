---
title: "Consum de RAM"
date: 2009-04-24
forum: Catalan Team
---

### Post by kimet on 2009-04-24
Hola ubuntistes.

 
De cares a instal.lar la nova versió d'ubuntu en màquines relativament velles, m'interesaria saber el consum de recursos d'aquest nou Jaunty J. Principalment de memòria Ram, tant amb 32 com amb 64 bits amb gnome.
 


Gràcies moltes i salutacions cordials a la comunitat.

---

### Post by SiscoGarcia on 2009-04-24
Hola kimet,

Depenent dels recursos del ferro a què et refereixis potser hauràs de triar algun escriptori lleuger; però si fem cas del que diu [ubuntu]("http://www.ubuntu.com/getubuntu/download"), els requeriments del sistema són [aquests]("https://help.ubuntu.com/community/Installation/SystemRequirements") (llàstima que no hagin actualitzat la pàgina, perquè diu que són els referents a la 8.10 encara que et remeti des de la pàgina de descàrrega de la 9.04).

EDITO: Per cert, som [ubuntaires]("https://wiki.ubuntu.com/JosepS%C3%A0nchez/documentaci%C3%B3/Ubuntaire"), no ubuntistes ;)

---

### Post by kimet on 2009-04-25
Graciés per contestar Sisco.

El que jo volia saber es el consum real de la nova versió.

He usat l'ubuntu desde el feisty i a mesura que han anat sortint les noves versions el consum de recursos ha augmentat força.

Per això, em seria d'ajuda que els que l'heu instal.lat em diguéssiu quin consum de ram hi ha al engegar la màquina. Només s'ha de obrir el monitor del sistema, no se si es troba a: aplicacions--> eines del sistema.(sense cap més programa corrent)

M'interessa de cares a instal.lar l'ubuntu (o no) en màquines de companys que s'inicien a linux.

Graciés ubuntaires):P

---

### Post by oriolsbd on 2009-04-25
Hola, Kimet.

He instal·lat Jaunty en una màquina virtual. Amb el sistema acabat d'instal·lar (sense haver-hi instal·lat cap programa ni códec extra, ni haver activat els efectes d'escriptori), les primeres línies que em surten amb la comanda "top" són aquestes:

top - 17:47:23 up 1 min,  2 users,  load average: 2.34, 0.80, 0.28
Tasks: 110 total,   1 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.3%us, 58.7%sy,  0.0%ni, 18.3%id,  0.4%wa,  0.4%hi,  1.9%si,  0.0%st
Mem:    477096k total,   263848k used,   213248k free,    20104k buffers
Swap:   353388k total,        0k used,   353388k free,   116760k cached

Salut!

---

### Post by torracastanyes on 2009-04-25
Hola Kimet.
Jo el tinc en una maquina física amb 1 giga de ram i em marca un consum del 17%. Ara, amb el firefox obert ha pujat al 22%,

---

### Post by kimet on 2009-04-25
Graciés companys.

A veure si contesta algú més, perquè em semblen molt bones aquestes dades.

Seguim l'enquesta? :P

---

### Post by SiscoGarcia on 2009-04-25
> **kimet said:**
> Seguim l'enquesta? :P

Doncs el meu top en un ferro de segona mà amb 512 MB de RAM i fent servir xubuntu jaunty és:

top - 22:56:42 up 16 min,  2 users,  load average: 1.07, 1.85, 1.20
Tasks: 148 total,   2 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s): 51.3%us,  7.0%sy,  0.0%ni, 41.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    509180k total,   498988k used,    10192k free,    51888k buffers
Swap:  1494004k total,   179968k used,  1314036k free,   128532k cached

---

### Post by RainCT on 2009-04-27
A mi m'utilitza al voltant d'uns 500MB de RAM.

Ara mateix, amb el Compiz, el GNOME Do, el Firefox i una terminal amb l'irssi:

```

[rainct, ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          3891       2250       1641          0        178       1398
-/+ buffers/cache:        673       3218
Swap:         1474          0       1474

```

(La segona línia, on diu "Mem:" indica el consum de memòria considerant les dades que el nucli ja ha carregat per a fer successives operacions més ràpids o pel que sigui que la faci servir -ja sabeu, el Linux sempre prova d'aprofitar tota la memòria disponible-, i el consum *real* està indiciat a la línia següent, ara mateix 673 MB).

---

### Post by kimet on 2009-05-01
Gràcies per les respostes.

Aqui deixo els resultats de consum de RAM en dos ordinadors diferents.
Un amb ubuntu hardy amb gnome,  i l'altre amb debian i kde. Tots dos sense cap extra innecesari, compiz, desklets, emerald, etc. i al arrencar l'ordinador.

Amb ubuntu hardy heron:

```
           total       used       free     shared    buffers     cached
Mem:           500        431         68          0         18        195
-/+ buffers/cache:        217        282
Swap:            0          0          0
```

Amb debian lenny i kde-base.

```
      total       used       free     shared    buffers     cached
Mem:           499        227        271          0          9        113
-/+ buffers/cache:        104        395
Swap:         1168          0       1168
```

Salut.

---

### Post by CarlesOriol on 2009-05-01
Aquestes proves que feu no serveixen per res. Us posaré un exemple:

Es com si comparéssim dos cotxes un circulant per una autopista i l'altre per la carretera de l'arrebassada (on la carretera seria la memòria).
Evidentment el cotxe que circula per l'autopista aprofitarà aquesta situacio' per tal de còrrer més. Això no vol dir que sigui millor o estigui mes ben dissenyat que l'altre, simplement que aprofitarà les condicions del seu entorn.

Això mateix fan els sistemes operatius i els programes que fan us intens dels recursos. Adaptar-se al que troben. I molt sovint aquells que et poden semblar més intrusius son els que fan una millor feina, mentre els que no ho fan... simplement no estan tant ben dissenyats.

Però també pot ser exactament el contrari: que un programa faci un mal us de recursos. 

De tota manera i com deia al començament aquestes reflexcions simplement sobre l'"alocatacio'" dinàmica que fa un programa de la memòria no serveixen de res.

---

### Post by kimet on 2009-05-01
No estic d'acord.

Quant més memòria deixi lliure un SO mes memòria queda lliure per a carregar els programes i quant menys memòria SWAP utilitzin els programes mes ràpid aniràn aquests. Pots fer la prova.

---

### Post by CarlesOriol on 2009-05-02
Doncs no. No puc estar més en contra. Un bon sistema operatiu és aquell que gestiona més eficientment els recursos dels que disposa en cada moment. No aquell que no en fa us.

I els programes funcionaran més ràpid aquells que estiguin més ben dissenyats, aquells que aprofitin millor les tecnologies que es considerin critiques per fer la feina per la que han estat dissenyats.

A més un programa que les allocatacions de memòria siguin paginades a la swap no té per que ser més lent que un que hagi de fer acrobacies per no superar un determinat limit de memòria.

---

### Post by kimet on 2009-05-02
Hola CarlesOriol:

> Doncs no. No puc estar més en contra. Un bon sistema operatiu és aquell que gestiona més eficientment els recursos dels que disposa en cada moment. No aquell que no en fa us.

I els programes funcionaran més ràpid aquells que estiguin més ben dissenyats, aquells que aprofitin millor les tecnologies que es considerin critiques per fer la feina per la que han estat dissenyats.

A més un programa que les allocatacions de memòria siguin paginades a la swap no té per que ser més lent que un que hagi de fer acrobacies per no superar un determinat limit de memòria.

Donç si home en això tens tota la raó.

Però no és aquest el problema, Del que tú dius se'n podría deduir que dona igual la memòria que tingui un equip, perquè el sistema operatiu la gestionarà sempre correctament, i això és fals.
Si fem una comparació, entre diferents distribucions, i de la memòria que consumeixen al inici, podem saber la que ens queda disponible, no hi ha volta de full. Estem parlant del mateix sistema operatiu i distros diferents.

Per quina raó ubuntu consumeix més recurssos que d'altres distribucions? Segurament per la quantitat d'automatismes que inclou per tal de "facilitar-ne" l'ús als menys experts...O per crear-ne dependència?....O per vendre equips més potents amb ubuntu preinstal.lat, cosa per la qual en treu un rendiment económic? Jo em decantaria per la primera. Però és innegable que s'esta abandonant la filosofia que sempre s'havia defensat desde linux, de funcionar en els ordinadors més modestos i amb menys recursos.

Tot i això crec que l'ubuntu compleix una molt bona feina de difussió i de porta d'entrada al món linux. Encara que tinc seriosos duptes de les intencións de la companyía Canonical.

Salut i programari lliure!!

---

### Post by CarlesOriol on 2009-05-03
> **kimet said:**
> ...de la memòria que consumeixen al inici, podem saber la que ens queda disponible, no hi ha volta de full. 

No en cap cas. La gestio' de la memòria és dinàmica. Això no et serveix de cap tipus de referència de rendiment ni de disponibilitat d'aquesta.

> Per quina raó ubuntu consumeix més recurssos que d'altres distribucions? Segurament per la quantitat d'automatismes que inclou per tal de "facilitar-ne" l'ús als menys experts...O per crear-ne dependència?....

Doncs no. Els recursos es resesrven per tal de aconseguir la màxima potencia del sistema. Inicis ràpids, accessos a discs fluids amb bones estructures de caches i sistemes de càrrega que intenten posar a la disposició del programa dades abans fins i tot que aquest les requereixi, us de buffers en cache de disc...,  i si... evidentment pre-carrega de detectors per avisar i poder instal.lar amb facilitat nous dispositius, aixi com dobles buffers d'imatge a di d'aconseguir una interficie amb l'usuari fluida... i un munt de coses més.

> O per vendre equips més potents amb ubuntu preinstal.lat, cosa per la qual en treu un rendiment económic? Jo em decantaria per la primera. Però és innegable que s'esta abandonant la filosofia que sempre s'havia defensat desde linux, de funcionar en els ordinadors més modestos i amb menys recursos.

Malauradament hi ha molt pocs ordinadors amb ubuntu preinstal.lat i comentar-ho com una estrategia per conseguir ves a saber que em sembla fora de lloc.

A més xubuntu existeix com a distribució especialment pensada per fer aquesta missió. El que no pots demanar és un ordinador antic funcionant amb les darreres tecnologies com si fos un de nou, no... cada cosa té el seu lloc.

> Tot i això crec que l'ubuntu compleix una molt bona feina de difussió i de porta d'entrada al món linux. Encara que tinc seriosos duptes de les intencións de la companyía Canonical.

Ubuntu és un gran sistema, per a molts com jo: la millor implementació de debian existent fins el moment, i deu el seu contingut tant en programes com en el que l'envolta a milers de desenvolupadors i voluntaris de tot el mon.
Canonical és una empresa que ha fet una bona feina (i de tot cor espero que amb el temps sigui un gran negoci per ells) creant ubuntu. 
El més gran del programari lliure és que sempre tindrem la llibertat d'elegir si estem d'acord o canviem de distribució... així de fàcil.

---

### Post by kimet on 2009-05-03
> No en cap cas. La gestio' de la memòria és dinàmica. Això no et serveix de cap tipus de referència de rendiment ni de disponibilitat d'aquesta.

Entenc que és dinamica la que està en caché o buffer, però no la que està  realment ocupada.

> i si... evidentment pre-carrega de detectors per avisar i poder instal.lar amb facilitat nous dispositius, aixi com dobles buffers d'imatge a di d'aconseguir una interficie amb l'usuari fluida... i un munt de coses més.

I aquests són etèris :)

> Malauradament hi ha molt pocs ordinadors amb ubuntu preinstal.lat i comentar-ho com una estrategia per conseguir ves a saber que em sembla fora de lloc.

No ho afirmo, només m'ho pregunto.

> Ubuntu és un gran sistema, per a molts com jo: la millor implementació de debian existent fins el moment, i deu el seu contingut tant en programes com en el que l'envolta a milers de desenvolupadors i voluntaris de tot el mon.
Canonical és una empresa que ha fet una bona feina (i de tot cor espero que amb el temps sigui un gran negoci per ells) creant ubuntu.

Estàs en nòmina? :P:P:P

> El més gran del programari lliure és que sempre tindrem la llibertat d'elegir si estem d'acord o canviem de distribució... així de fàcil.

El més gran del programari lliure és que sigui accesible a tothom. :lolflag:

---

### Post by CarlesOriol on 2009-05-03
> **kimet said:**
> Entenc que és dinamica la que està en caché o buffer, però no la que està  realment ocupada.
Tota la memòria és dinàmica i no existeix la memòria no ocupada realment.

> Estàs en nòmina? :P:P:P
I tant... cada sis mesos a canònical em regala un ubuntu nou :-)

> 
El més gran del programari lliure és que sigui accesible a tothom. :lolflag:
... i no sols això... però aqui' estem d'acord.

Si vols seguim xerrant a la festa el proper cap de setmana... que aqui aburrirem al personal. :-D

---

### Post by marteljorge on 2009-05-03
> **kimet said:**
> Hola ubuntistes.

 
De cares a instal.lar la nova versió d'ubuntu en màquines relativament velles, m'interesaria saber el consum de recursos d'aquest nou Jaunty J. Principalment de memòria Ram, tant amb 32 com amb 64 bits amb gnome.
 


Gràcies moltes i salutacions cordials a la comunitat.

Bé, 160MB amb Gnome, Alsa, wifi...
Ara el tinc amb 330MB(+FF, +ftp)
Edito:
marteljorge@cecilia-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        933         59          0        106        486
-/+ buffers/cache:        341        651
Swap:         2996          0       2995

---

