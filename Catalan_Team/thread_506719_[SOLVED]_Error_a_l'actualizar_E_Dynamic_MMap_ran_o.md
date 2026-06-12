---
title: "[SOLVED] Error a l'actualizar: E: Dynamic MMap ran out of room."
date: 2007-07-22
forum: Catalan Team
---

### Post by mininomutante on 2007-07-22
Hola a tothom!
Ahir a l'intentar actualitzar els paquets l'ubuntu em dona aquest error:
E: Dynamic MMap ran out of room, E:S'ha produït un error durant el processament de firefox (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat.'
He llegit per la web que cal canviar una linia de l'arxiu per incrementar la cache, o alguna cosa semblant. Però no trobo l'arxiu al que fan referència en el meu ordinador:
/etc/apt/apt.conf
(crec que no el tinc ;) ).
Gràcies per tot.
PD: Veig que tampoc puc utilitzar el menú -> afegeix/elimina de Aplicacions...crec que pel mateix motiu.

---

### Post by papapep on 2007-07-22
El fitxer /etc/apt/apt.conf si no el tens el pots crear:

```
sudo nano /etc/apt/apt.conf
```

Per exemple, podries provar a ficar-hi la següent línia:

```
APT::Cache-Limit 10485760;
```

Si et segueix donant error, hauries de mirar de deixar al /etc/apt/sources.list els repositoris imprescindibles i comentar (posar un # al inici de la línia) dels que no et siguin necessaris.

---

### Post by mininomutante on 2007-07-23
Hola!
He provat el que m'has dit, papapep. 
Ara tinc un arxiu dintre etc/apt que es diu "apt.conf" on només hi ha una linia que és: APT::Cache-Limit 10485760;
A més crec que he fet alguna cosa malament perquè també tinc un altre arxiu a la mateixa ruta amb el nom de apt.conf.save (amb una icona amb una creu blanca).
Quan intento executar l'actualització em surt el següent error:

S'ha produït un problema irresoluble mentre s'inicialitzava la informació del paquet.

Informeu de l'error, referent al paquet update-manager, i adjunteu el següent missatge d'error:

'E: Dynamic MMap ran out of room, E:Error de lectura - read (14 Bad address), E:No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat.'

Quan he vist això he intentat llistar el source.list per "comentar" cada repositori, però no em deix "desar" i executo el terminal amb el "su" per entrar com a root.
També he intentat "eliminar" els arxius que he creat primer (apt.conf i apt.conf.save) però tampoc em deix.
Gràcies per la teva ajuda.

Actualitzo: Potser això pot ajudar. Si executo el Synaptic hem surt:
E: Dynamic MMap ran out of room
E: Error de lectura - read (14 Bad address)
E: No s'han pogut analitzar o obrir les llistes de paquets o fitxer d'estat.
E: _cache->open() failed, please report.

---

### Post by papapep on 2007-07-23
> però no em deix "desar" 

Això significa que no estàs executant correctament la ordre.

El terminal crida'l normalment, i després posa:

```
sudo nano /etc/apt/sources.list
```

veuràs com així et deixa comentar i desar. Per cert, no comentis tots els dipòsits de paquets, només els que no et calguin.

Respecte l'apt.conf.save, és símplement una "còpia de seguretat" que ha fet l'editor del fitxer original, no et preocupis.
I no t'aconsello que facis coses a la babalá, com esborrar fitxers i demés, ja que et pots carregar els sistema sense voler.

---

### Post by mininomutante on 2007-07-23
Hola!
Papapep, he provat el que m'has comentat i (després d'una mica d'assaig-error ;) ) ha anat tot bé...ja està actualitzant
Mil gràcies.

---

### Post by mininomutante on 2007-07-29
Hola a tothom!
Nomès escric per fer un petit aclariment per si amb posterioritat algú llegeix el fil amb el mateix problema.
Sembla ser (almenys a mi) que l'error el produeix l'Automatix2. Quan s'actualitza fa que surti l'error que esmentava en el post inicial.
Aclarir una cosa més, recordo que quan el vaig instal·lar (l'automatix2) em deia que la versió que tenia només funcionava amb l'ubuntu 6.10 (quan jo crec que tinc la 7.04), però també recordo haver instal·lat un parell de cops l'automatix2 (dubto que m'hagués equivocat els dos cops :biggrin:)...crec que l'enllaç que utilitzava no era el correcte. L'estrany és que ara (un cop actualitzat, però sense reinstal·lar la versió per 7.04) el automatix2 si funciona.
Gràcies per l'ajuda
Salutacions.

---

