---
title: "Organització del disc dur i protecció de documents"
date: 2009-07-24
forum: Catalan Team
---

### Post by jinglada on 2009-07-24
Ja sabeu que no sóc cap expert en informàtica tot i haver treballat en un centre informàtic fa molt temps.

Fa anys que estic preocupat per a organitzar i protegir els meus documents. Sempre he anat creant directoris i subdirectoris i fent còpies de seguretat de tant en tant.

Això és molt farragós i no és segur; sempre m'oblido d'algun fitxer i, per la llei de Murphy, sempre és el que realment necessitaré recuperar.

Fa temps que penso que hi ha d'haver algun sistema d'arxiu com ara el que usa Gmail posant etiquetes en els missatges i així un missatge el pots tenir guardat amb tantes etiquetes com creus que s'interrelaciona amb altres missatges. 

Havia usat una mica el sistema de bases relacional Knosys i també un altre, el nom del qual no recordo, que feia servir un amic meu periodista, analista, escriptor, etc. per guardar tots els documents que l'interessava poder consultar-los ràpidament i fàcil en qualsevol moment.

Us agraeixo a la bestreta els vostres consells.

---

### Post by lluisanunez on 2009-07-26
Knosys i altres que hi ha tenen més sentit per organitzacions grans amb moltíssims documents, on surt a compte perdre temps amb un sistema d'indexació, etc.
Per a un escriptori personal jo recomanaria una cosa molt més lleugera (que no doni tanta feina). Jo faig servir el TomBoy, que és com un wiki personal on simplement copies un nom d'arxiu i s'hi fa un link.
El que aniria bé seria un programa que llegís les metadades dels documents Office i PDF (si les has entrades, clar), igual que fan per exemple Tracker o Rythmbox amb els mp3.
Doncs hi ha una cosa semblant, encara que no busca metadades dins dels documents sí que et permet posar tags i categoritzar d'una manera senzilla. Mirant la captura de pantalla ho veuràs més bé:
[http://icculus.org/referencer/mainwindow-1.1.0.png](http://icculus.org/referencer/mainwindow-1.1.0.png)
Referencer te'ls pots insta&#320;lar des de Synaptic

---

### Post by jinglada on 2009-07-27
Moltes gràcies lluisanunez. Provaré el que em dius i ja diré alguna cosa.

Pel que fa a l'eina de backup em pots aconsellar alguna aplicació. Cercant amb el google he trobat TimeVault i Flyback a part del SBackup. No n'he provat cap encara.

---

### Post by anna_marti_gomez on 2009-07-27
Bones,

jo pel que fa les còpies de seguretat tenia un dics dur extern usb amb rsnapshot [http://www.rsnapshot.org/]("http://www.rsnapshot.org/") que fa un còpia de seguretat incremental. Només copia allò que es nou. El pots instal·lar des de la terminal:
sudo apt-get install rsnapshot.

Després edites el fitxer /etc/rsnapshot.conf 
a les teues necessitats (interval i on ho ha de guardar) i listo!

Ara ja no ho tinc, pq el disc dur extern va passar a millor vida i ara estic en mode: no risk no fun!


Siau!

---

### Post by oriolsbd on 2009-07-27
Jo n'utilitzo un de semblant al de l'Anna. És el Grsync, i també el tens per Synaptic. També fa còpia incremental dels fitxers, però la seva configuració és des d'un entorn gràfic, en comptes d'un fitxer de configuració.

Els fitxers que et fa backup es veuen en "clar". És a dir, no et crea fitxers comprimits a partir dels quals pots restaurar, com el SBackup, sinó que et copia directament els fitxers modificats en una estructura de directoris igual a la teva original.

Pel que comenta, entenc que és el mateix comportament que el RSnapshot.

Per cert, m'ha agradat aquest mode de funcionament "no risk no fun". :-)

Salut!

---

### Post by anna_marti_gomez on 2009-07-27
Perdó per la broma (he hagut de demanar més d'un cop ajuda al fòrum per restaurar fitxers!! ho podeu comprovar)
El motiu es bastant més simple: no money no disk!

---

### Post by jaume69 on 2009-07-27
Jo crec que els **Discs Durs** interns de portátil actuals tenen més temps de vida que fa dos anys  o així.

Fa poc he comprat un Dics Dur extern de **1.5TB** [Lacie]("http://www.lacie.com/es/products/product.htm?pid=11156"),i en 2 minuts en va fer un backup de 10GB.El Disc es de mides reduïdes,igual que més o menys una capça de video VHS d´aquells temps.
Tot això fet sota Windows,en Linux també és compatible però et redueix molt la capacitat del Disc.Pot ser hi ha alguna manera de arreglar-ho..,algun dia ho provaré.
De fet aquest Disc está pensat o dissenyat per a Mac,crec.

Els **Discs Durs**en general tampoc son tan cars actualment..

Salud.

---

### Post by PatrickVogeli on 2009-07-27
per fer copies de seguretat pots fer servir el grsync, una interficie grafica a l'rsync.

salut

EDITO: ja veig que ja l'havien mencionat, no he pensat a refrescar la pagina abans de contestar :P

---

### Post by jinglada on 2009-07-27
Gràcies a totes i a tots. 

He començat a fer servir el grsync per allò de la interfície gràfica.

Pel que fa a l'organització del disc dur he començat a fer servir 'referencer' i m'agrada força. Tanmateix he trobat en el Synaptic altres programes que em sembla que també em podrien ser útils: 'Scrollkeeper' i 'Tracker'. 

El man del primer diu: ScrollKeeper - An open document cataloging and metadata management system.

El Tracker que al Synaptic diu:metadata database, indexer and search tool

Tracker is an advanced framework for first class objects with associated
metadata and tags. It provides a one stop solution for all metadata, tags,
shared object databases, search tools and indexing.

El problema és que ambdós estan instal·lats però no sé com fer-los funcionar. 

Obro un altre fil i no tanco aquest perquè encara vull preguntar sobre el tema d'organització del disc dur.

EDITO

No obro un altre fil perquè veig que potser he de llegir una mica més en el Terminal (man -k tracker i man scrollkeeper-config)

---

### Post by jinglada on 2009-07-28
He provat el flyback ([http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)) i em sembla molt bo, tot i que encara no he pogut fer proves per veure els incrementals, ja que es basa en el rsync. Tanmateix a la pàgina [http://code.google.com/p/flyback/wiki/HowItWorks](http://code.google.com/p/flyback/wiki/HowItWorks) hi ha un post que diu que el rdiff-backup és millor.

Algú en sap alguna cosa de tot això? Gràcies.

---

### Post by jinglada on 2009-07-29
> **jinglada said:**
> 
Fa temps que penso que hi ha d'haver algun sistema d'arxius com ara el que usa Gmail posant etiquetes en els missatges i així un missatge el pots tenir guardat amb tantes etiquetes com creus que s'interrelaciona amb altres missatges. 



> **jinglada said:**
> 
Pel que fa a l'organització del disc dur he començat a fer servir 'referencer' i m'agrada força. Tanmateix he trobat en el Synaptic altres programes que em sembla que també em podrien ser útils: 'Scrollkeeper' i 'Tracker'. 

El man del primer diu: ScrollKeeper - An open document cataloging and metadata management system.

El Tracker que al Synaptic diu:metadata database, indexer and search tool

Tracker is an advanced framework for first class objects with associated
metadata and tags. It provides a one stop solution for all metadata, tags,
shared object databases, search tools and indexing.

...he de llegir una mica més en el Terminal (man -k tracker i man scrollkeeper-config)

Pel que he llegit m'ha semblat entendre que ScrolKeeper és un sistema de catalogació per a la documentació d'ajuda de les aplicacions i cada veada que s'instal·la una aplicació s'encarrega d'organitzar el navegador d'ajuda.

En canvi Tracker extreu informació útil i metadades de tots els fitxers que es vulgui i permet assignar etiquetes. Sembla que és el que cercava. Ho provaré i ja informaré dels progressos.

---

### Post by lluisanunez on 2009-07-29
Tracker: un cop insta&#320;lat trobaràs al menú de Preferències alguna cosa com Preferències d'Indexació i Cerca, pots configurar quins discos ha d'indexar per documents, quines prioritats ha de tenir per indexar, etc. 
Funciona bé, busca a dins dels documents de text així com a les metadades de PDF, video i audio. Jo el faig servir per la música i els e-books
Pots engegar-lo per defecte a les Aplicacions d'inici

---

### Post by jinglada on 2009-07-29
Gràcies lluisanunez,

Una possibilitat que trobo a faltar és la cerca de fitxers per data (creació, modificació) com té el cercador dels Mac. 

He començat a mirar-me les possibilitats al Terminal i són moltes. 

joan@joan-laptop:~$ man -k tracker
bonobo-activation-server (1) - GNOME component tracker
tracker-applet (1)   - The tracker tray-icon and on-click-search-entry
tracker-extract (1)  - extract metadata from file and display them.
tracker-files (1)    - Return files filtered by the mime type or their category (called ServiceType)
tracker-info (1)     - command line tool to retrieve all metadata available in tracker for a certain file.
tracker-meta-folder (1) - return list of files indexed by tracker for a folder with their value for the selected properties
tracker-preferences (1) - Preferences editor for trackerd
tracker-query (1)    - command line tool to query tracker database
tracker-search (1)   - command line tool to search documents indexed by trackerd
tracker-search-tool (1) - Gnome Tracker Search Tool
tracker-services (1) - shows service types and propeties available in trackerd
tracker-stats (1)    - command line tool that provides statistics on files indexed by trackerd
tracker-status (1)   - command line tool that reports the trackerd status
tracker-tag (1)      - command line tool for setting and searching tags/keywords
tracker-thumbnailer (1) - create freedesktop.org compliant thumbnails (Deprecated)
tracker-unique (1)   - command line tool to ask for unique values of a property in tracker.
tracker.cfg (5)      - configuration file for the trackerd search daemon
trackerd (1)         - indexer daemon for tracker search tool

De tot això, no entenc què vol dir (1) o (5).

No entenc com funciona tracker-extract 

La informació de la data en tracker-info no recordo com es fa per convertir-la a format DDMMAAAAHHMMSS; per exemple el fitxer rentadora.png té 2651524 bytes i és de data 2009-07-17 i hora 12:29

joan@joan-laptop:~$ tracker-info rentadora.png
Defaulting to 'files' service
Results: 11 for '/home/joan/rentadora.png'
  'Image:Height' = '2231'
  'Image:Width' = '1504'
  'Image: Date' = '1247826567'
  'File:Name' = 'rentadora.png'
  'File:Ext' = 'png'
  'File: Path' = '/home/joan'
  'File:NameDelimited' = '/home/joan/rentadora.png'
  'File:Mime' = 'image/png'
  'File:Size' = '2651524'
  'File:Modified' = '1247826567'
  'File:Accessed' = '1247826570'

Salut

---

### Post by jinglada on 2009-07-30
Ja he trobat com fer funcinar tracker-extract a: [http://www.mail-archive.com/tracker-list@gnome.org/msg04589.html](http://www.mail-archive.com/tracker-list@gnome.org/msg04589.html)

joan@joan-laptop:~$ /usr/lib/tracker/tracker-extract -v 3 -f rentadora.png
Tracker-Message: Setting IO priority
Tracker-Message: Setting process priority
Initializing tracker-extract...
Tracker-Message: ---- [1]   Guessing mime type as 'image/png' for path:'/home/joan/rentadora.png'
Tracker-Message: ---- [1]   Found 3 metadata items
(tracker-extract:8139): Tracker-DEBUG: ---- [1]   Found 'Image: Date'='2009-07-17T12:29:27+0200'
(tracker-extract:8139): Tracker-DEBUG: ---- [1]   Found 'Image:Width'='1504'
(tracker-extract:8139): Tracker-DEBUG: ---- [1]   Found 'Image:Height'='2231'

Slow by slow fills the washbowl!!! (no és tan fun com el no risk... de l'anna, però mira :) :D)

---

