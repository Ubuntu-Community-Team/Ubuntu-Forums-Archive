---
title: "edició de videos"
date: 2009-06-15
forum: Catalan Team
---

### Post by auska1714 on 2009-06-15
Bones gent,

aviam si em podeu ajudar, necessito un programa que em permeti (de forma senzilla, no vull viraries) editar els vídeos que grabaré amb el "gtk-recordmydesktop"

Quin m'aconselleu? Preferiblement algun que pugi veure algun tutorial ràpid per aprendre a fer-lo anar... :p

Moltes gràcies,

Salut!

---

### Post by akyra on 2009-06-15
Jo vaig preguntar el mateix no fa gaire, i el que semblava més senzill era el Kdenlive. Hi ha tutorials e informació que es poden trobar de forma fàcil.

Et paso l'enllaç del fil que jo ho demanava.

Adeu

[http://ubuntuforums.org/showthread.php?t=1148321&highlight=video](http://ubuntuforums.org/showthread.php?t=1148321&highlight=video)

---

### Post by auska1714 on 2009-06-25
tal com m'has dit he instal·lat el kdenlive, des dels repositori, però ara tinc un problema. Quan l'intento executar s'obre i es tanca a l'instant. Alguna idea de que pot passar? 

Moltes gràcies,


P.D.: em sap greu haver tardat en contestar...

---

### Post by oriolsbd on 2009-06-25
Intenta executar-lo des d'un terminal, a veure quin missatge et dóna:
```
kdenlive
```

Salut!

---

### Post by auska1714 on 2009-06-26
roser@roser:~$ kdenlive
kbuildsycoca running...
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
QSocketNotifier: invalid socket 9 and type 'Read', disabling...
QSocketNotifier: invalid socket 4 and type 'Read', disabling...
Unable to start Dr. Konqi
roser@roser:~$

---

### Post by papapep on 2009-06-26
Quina versió d'ubuntu fas server? i quina versió de kdenlive intentes executar'

Per cert, mira: [http://lmgtfy.com/?q=ubuntu+Unable+to+start+Dr.+Konqi](http://lmgtfy.com/?q=ubuntu+Unable+to+start+Dr.+Konqi)

---

### Post by auska1714 on 2009-06-26
l'ubuntu es el 8.10 (no m'atreveixo a passar al 9.04 pq si la liu ma mare m'els talla pq es el seu ordinador i vol conservar el finestres) i la versio del kdenlive no ho se. És la que hi ha als repositoris...


P.D.: m'he mirat això que m'has passat i alguns posts no els entenc :S i altres no troben la solució...

---

### Post by akyra on 2009-06-26
Podries mirar la versió en el synaptic, buscar el kdenlive i mirar quina versió és (ho posarà al costat).
Adeu

---

### Post by auska1714 on 2009-06-26
versió kdenlive: 05.svn20071228-0.0ubuntu3

---

### Post by orestesmas on 2009-06-26
És una versió mooolt antiga (ara ja van per la 0.7.4). Vés a saber perquè peta. A mi em petava fa temps perquè el meu directori de treball tenia un accent (Vídeos), però no era en arrencar. 

Al [web del kdenlive]("http://kdenlive.org") hi ha [instruccions sobre com baixar-se una versió més moderna que la teva]("http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages") (la 0.7.2) ja precompilada per la 8.10, però de totes totes jo et recomano que provis de compilar-lo tu, obtindràs una versió més nova i probablement ja no et petarà. No t'espantis encara! Per fer-ho pràctic per a "usuaris normals" hi ha una eina que funciona prou bé: un assistent a la compilació del Kdenlive.

Segueix els següents passos:

[LIST=1]
[*]Crea't un directori buit per fer la compilació. Per exemple, es pot dir "devel".
[*]Baixa't l'assistent d'[aquest enllaç]("http://kde-apps.org/content/download.php?content=85826&id=1&tan=70631226"). Grava'l al directori anterior.
[*]Obre un terminal i posa't al directori "devel"
[*]Descomprimeix-lo amb ```
bunzip2 85826-kdenlive_builder_wizard.kmdr.bz2
``` i fes-lo executable:```
chmod u+x 85826-kdenlive_builder_wizard.kmdr
```
[*]Això que t'acabes de baixar és un script que s'ha d'executar amb el programa "kommander". Com que no deus utilitzar KDE, no el deus tenir instal·lat. Instal·la'l ara:```
sudo apt-get install kommander
```
[*]Executa l'script:```
kmdr-executor 85826-kdenlive_builder_wizard.kmdr
```
[*]Ara cal seguir les instruccions de l'script. Aquest script baixarà les fonts dels programes adients (frei0r, ffmpeg, mlt, mlt++ i kdenlive), les compilarà i les instal·larà allà on li hagis indicat. En aquest punt et deixo que ho remenis tu, i si tens problemes torna a preguntar.
[/LIST]

Creu-me, l'esforç val la pena. És un gran programa.

**[SIZE="3"][COLOR="Red"]ATENCIÓ! Edito: Sembla que algú ha fet paquets del kdenlive 0.7.4 per la intrepid[/COLOR][/SIZE]**. Segueix les instruccions d'[aquest enllaç]("http://kdenlive.org/forum/kdenlive-074-launchpad-debs-jaunty-and-intrepid"). Això fa obsolet tot aquest procés de compilació, però ho deixo tal qual perquè el procés serveix per estar al dia de les darreres versions del programa, per si algú encara usa altres versions d'ubuntu més antigues i, què caram, perquè ja havia fet la feina d'escriure-ho i així queda per a la posteritat.

---

### Post by auska1714 on 2009-06-26
No entenc que he de fer seguint l'enllaç a la primera part, la que posa el seguent:

A/ sudo gedit /etc/apt/sources.list

Jaunty

##Kdenlive 0.7.4
deb [http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu](http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu) jaunty main
##deb-src [http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu](http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu) jaunty main

intrepid

##Kdenlive 0.7.4
deb [http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu](http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu) intrepid main
##deb-src [http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu](http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu) intrepid main

Alguna ajuda?

Moltes gràcies.

Salut!

---

### Post by oriolsbd on 2009-06-26
Hola, 

Com que tens Ubuntu 8.10 (Intrepid Ibex) has d'editar el fitxer /etc/apt/sources.list:
```
sudo gedit /etc/apt/sources.list
```

I afegir-hi les línies següents:
```
##Kdenlive 0.7.4
deb http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu intrepid main
##deb-src http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu intrepid main
```

Salutacions,

---

### Post by jhnotario on 2009-06-26
No se si et servirá, pero jo utilitzo [Kino]("http://es.wikipedia.org/wiki/Kino_%28software%29"). Es molt fácil d'instal·lar i serveix per capturar des de cameras digitals a traves del port IEE1394.

---

### Post by jinglada on 2009-06-27
> **oriolsbd said:**
> Hola, 

Com que tens Ubuntu 8.10 (Intrepid Ibex) has d'editar el fitxer /etc/apt/sources.list:
```
sudo gedit /etc/apt/sources.list
```

I afegir-hi les línies següents:
```
##Kdenlive 0.7.4
deb http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu intrepid main
##deb-src http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu intrepid main
```

Salutacions,

Jo també necessitava un editor de vídeo i he seguit aquestes instruccions però m'ha instal·lat la versió 0.6.0 svn en ll0c de la 0.7.4

He fet res malament?

---

### Post by orestesmas on 2009-06-27
Has actualitzat els repositoris abans d'instal·lar?

```
sudo apt-get update
```

Si entres amb un navegador a l'adreça del repositori indicat es pot observar que efectivament els paquets de la 0.7.4 són allí posadets.

---

### Post by jinglada on 2009-06-27
> **orestesmas said:**
> Has actualitzat els repositoris abans d'instal·lar?

```
sudo apt-get update
```

Si entres amb un navegador a l'adreça del repositori indicat es pot observar que efectivament els paquets de la 0.7.4 són allí posadets.

Gràcies per la resposta. No he actualitzat els repositoris. Si ho faig ara, després he de repetir el procés anterior?

---

### Post by oriolsbd on 2009-06-27
No, només has d'executar la comanda que t'ha dit l'Orestes, i el sistema et dirà que tens una actualització del Kdenlive.

Salut!

---

### Post by orestesmas on 2009-06-27
Bé, el que dius és cert, però el sistema no ho fa immediatament. Només explora els repositoris en busca de noves versions cada cert temps, i això despista els usuaris novells.

Per accelerar el procés, després d'actualitzar els repositoris pots demanar-li d'instal·lar el kdenlive altre cop, i ja hauria de trobar la nova versió.

---

### Post by jinglada on 2009-06-28
Gràcies companys,

he fet el apt-get update i al final surt:
68,0kB descarregats en 2s (33,3kB/s)  
S'està llegint la llista de paquets... Fet
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 2380DF3029E526FC
W: Potser voldreu executar apt-get update per a corregir aquests problemes

Torno a instal·lar el kdenlive o he de fer alguna cosa abans?

Salut!

---

### Post by SiscoGarcia on 2009-06-28
Li hauries de dir on és la clau gpg, que és [aquesta]("http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu/dists/intrepid/Release.gpg").

---

### Post by orestesmas on 2009-06-28
Ep, Sisco, potser cal ser una mica més explícit...

Jinglada: Et dóna aquest error perquèno pot assegurar que la persona que ha fet i signat el paquet del kdenlive sigui qui diu que és.
Si tu confies en aquesta persona (en aquest cas pots córrer el risc amb certa tranquil·litat) cal baixar-te la seva clau i instal·lar-te-la al teu anell de claus, i aleshores repetir la instal·lació:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2380DF3029E526FC

```

---

### Post by jinglada on 2009-06-29
> **SiscoGarcia said:**
> Li hauries de dir on és la clau gpg, que és [aquesta]("http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu/dists/intrepid/Release.gpg").

Gràcies Sisco. Com es fa per dir-li-ho?

EDITO! No havia vist la resposta de l'Orestes. Gràcies Orestes. Ara ho provaré.

Bé, ja ho he provat i dóna això:
joan@joan-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2380DF3029E526FC
[sudo] password for joan: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 2380DF3029E526FC
gpg: requesting key 29E526FC from hkp server keyserver.ubuntu.com
gpg: key 29E526FC: public key "Launchpad PPA for Dominik Stadler" imported
gpg: Nombre total processat: 1
gpg:               importades: 1  (RSA: 1)
joan@joan-laptop:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg

...

47,7kB descarregats en 1s (29,4kB/s)  
S'està llegint la llista de paquets... Fet
joan@joan-laptop:~$ sudo apt-get install melt
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
E: [COLOR="Red"]No s'ha pogut trobar el paquet melt[/COLOR]
joan@joan-laptop:~$ sudo apt-get install kdenlive
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
[COLOR="Red"]kdenlive ja es troba en la versió més recent.[/COLOR]
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 0 no actualitzats.
joan@joan-laptop:~$

-------------

Arranco el kdenlive i segueix sent la versió 0.6.0-svn (Using KDE 3.5.10)

Alguna cosa no faig bé o això del melt que no troba n'és la causa?

---

### Post by orestesmas on 2009-06-30
Caram, quines coses et passen...
anem a veure: obre un terminal i ves fent això:

Primer mirarem quin fitxer concret estàs executant
```
which kdenlive
```

Ara mirarem a quin paquet correspon aquest fitxer:
```
dpkg -S `which kdenlive`
```

En la darrera ordre, la "cometa" que surt (`) és l'accent greu, que el pots obtenir prement la tecla d'accent greu seguida immediatament per un espai en blanc. Posar una ordre entre aquests accents fa que s'insereixi en aquell punt el resultat d'executar l'ordre.

Un cop sàpigues el nom del paquet, que suposo que serà el "kdenlive", mira't la versió concreta que tens instal·lada:
```
dpkg -l nom_del_paquet
```

I ara mira la versió del repositoris. hauria de ser la nova
```
apt-cache search kdenlive
```

Si n'hi ha una de nova, fent el següent s'hauria d'instal·lar:
```
sudo aptitude install kdenlive
```

Si no és així, prova de desinstal·lar primer la versió antiga:
```
sudo aptitude purge kdenlive
sudo aptitude install kdenlive
```

Si no és així, torna a preguntar.

---

### Post by jinglada on 2009-07-01
Primer de tot, gràcies per la paciència; no sé si mai n'aprendré. Potser estic predestinat a ser un patidor del finestres :-k

> **orestesmas said:**
> Caram, quines coses et passen...
anem a veure: obre un terminal i ves fent això:

Primer mirarem quin fitxer concret estàs executant
```
which kdenlive
```

joan@joan-laptop:~$ which kdenlive
/usr/bin/kdenlive
joan@joan-laptop:~$ 

> 
Ara mirarem a quin paquet correspon aquest fitxer:
```
dpkg -S `which kdenlive`
```

joan@joan-laptop:~$ dpkg -S `which kdenlive`
kdenlive: /usr/bin/kdenlive
joan@joan-laptop:~$ 

> 
En la darrera ordre, la "cometa" que surt (`) és l'accent greu, que el pots obtenir prement la tecla d'accent greu seguida immediatament per un espai en blanc. Posar una ordre entre aquests accents fa que s'insereixi en aquell punt el resultat d'executar l'ordre.

He copiat i he enganxat i m'he estalviat d'escriure; serveix, oi?

> Un cop sàpigues el nom del paquet, que suposo que serà el "kdenlive", mira't la versió concreta que tens instal·lada:
```
dpkg -l nom_del_paquet
```

joan@joan-laptop:~$ dpkg -l kdenlive
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom            Versió        Descripció
+++-==============-==============-============================================
ii  kdenlive       0.5.svn2007122 A Non-Linear Video Editing Suite for KDE
joan@joan-laptop:~$ 

> 
I ara mira la versió del repositoris. hauria de ser la nova
```
apt-cache search kdenlive
```

joan@joan-laptop:~$ apt-cache search kdenlive
kdenlive - A Non-Linear Video Editing Suite for KDE
kdenlive-data - A Non-Linear Video Editing Suite for KDE - data files
joan@joan-laptop:~$ 

[COLOR="Red"]M'aturo ací perquè no ho veig clar ja que la resposta a la penúltima instrucció és: 0.5.svn2007122 i quan arranco kdenlive des d'Aplicacions (mode gràfic) diu que és la versió 0.6.0-svn (Using KDE 3.5.10)
[/COLOR]
Què he de fer ara?
> 
Si n'hi ha una de nova, fent el següent s'hauria d'instal·lar:
```
sudo aptitude install kdenlive
```

Si no és així, prova de desinstal·lar primer la versió antiga:
```
sudo aptitude purge kdenlive
sudo aptitude install kdenlive
```

Si no és així, torna a preguntar.

---

### Post by jinglada on 2009-07-05
Hola Orestes,
He migrat de l'Intrepid al Jaunty i he repetit la instal·lació del kdenlive i no m'ha donat cap problema (aparentment). L'he intentat executar des d'Aplicacions/So i Vídeo i em dóna el missatge del gràfic adjunt.

He passat altra vegada les comandes que em deies i surt:

joan@joan-laptop:~$ [COLOR="Lime"]which kdenlive[/COLOR]
/usr/bin/kdenlive
joan@joan-laptop:~$ [COLOR="Lime"]dpkg -S `which kdenlive`[/COLOR]
kdenlive: /usr/bin/kdenlive
joan@joan-laptop:~$ [COLOR="Lime"]dpkg -l kdenlive[/COLOR]
Desitjat=desconegUt/Instal·la/SupRimeix/Purga/Retín(h)
| Estat=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Estat,Err: majúsc.=dolent)
||/ Nom                               Versió                           Descripció
+++-=================================-=================================-==================================================================================
ii  kdenlive                          0.7.4+svn3592-1ubuntu2~ppa1       a non-linear video editor
joan@joan-laptop:~$ [COLOR="Lime"]apt-cache search kdenlive[/COLOR]
kdenlive-data - a non-linear video editor (data files)
kdenlive - a non-linear video editor
kdenlive-dbg - a non-linear video editor (debugging symbols)
joan@joan-laptop:~$ 

S'em resisteix molt el kdenlive, oi?

Salutacions

---

### Post by papapep on 2009-07-05
Prova a instal·lar aquestes llibreries, que sembla que és del que es queixa:

```
sudo aptitude install libmlt++1 libmlt1 libmlt-data
```

---

### Post by sianeu on 2009-07-05
Fa poc temps (al voltant d'un mes) em funcionava perfectament. Pero ara m'ha sorgit el mateix problema....... coses de les actuatitzacions. Ho he provat en un altre ordinador, tambè amb Jaunty, i el mateix.

Finalment he trobat la sol·luciò desinstalant un fitxer:

> sudo rm /usr/lib/frei0r-1/facedetect.so


font:  [http://doc.ubuntu-fr.org/kdenlive]("http://doc.ubuntu-fr.org/kdenlive")

Salut

---

### Post by jinglada on 2009-07-05
Gràcies papapep per l'interés; la resposta de sianeu ha funcionat perfectament. Gràcies sianeu. 
Finalment tinc Kdenlive versió 0.7.4 Usant el KDE 4.2.2 (KDE 4.2.2) funcionant.
És la primer vegada que entro a Kdenlive i no en tinc ni idea. Hi ha algun lloc on aprendren?

---

### Post by SiscoGarcia on 2009-07-05
> **jinglada said:**
> Hi ha algun lloc on aprendren?

Jo no el faig servir però suposo que des de consola podràs fer "man kdenlive" i tindràs el manual de l'aplicació... això sí, en anglès.

També pots fer [això]("http://tinyurl.com/l74dsl") ;)

EDITO: a la primera entrada que surt hi ha video tutorials i també indica un manual.

---

### Post by quitus on 2009-07-05
[http://es.wikibooks.org/wiki/Kdenlive/Gu%C3%ADa_r%C3%A1pida](http://es.wikibooks.org/wiki/Kdenlive/Gu%C3%ADa_r%C3%A1pida)

Jo si que el faig servir, de debò que es molt fàcil, la única cosa que em va resultar estranya van ser les transicions, has de fer servir dues pistes de vídeo i superposar els dos vídeos el temps que vulguis que duri la transició. La guia que et dono ho explica tot.

salut

---

### Post by orestesmas on 2009-07-05
> **quitus said:**
> la única cosa que em va resultar estranya van ser les transicions, has de fer servir dues pistes de vídeo i superposar els dos vídeos el temps que vulguis que duri la transició.

Bé, això no és pas res estrany. És com funcionen els editors de vídeo multipista professionals.

De fet, per certs efectes no cal que superposis les pistes. Per exemple si vols un fos a negre seguit d'una entrada des de negre, ho pots fer amb una sola pista, però per efectes més xulos caldrà usar dues o tres pistes simultàniament.

Com heu dit, el programa és força autoexplicatiu encara que, no, Sisco, no hi ha pàgina de "man" per aquest programa perquè no n'hi acostuma a haver per aquells programes que usen bàsicament la IGU.

Una cosa important a tenir en compte és crear un projecte nou per cada vídeo que vulguem fer, indicar-li quin volem que sigui el format final del vídeo, procurar col·locar els clips en el directori de treball per no tenir-los dispersos per tot el disc, i anar desant sovint.

Apa, bona feina.

---

### Post by SiscoGarcia on 2009-07-06
> **orestesmas said:**
> Com heu dit, el programa és força autoexplicatiu encara que, no, Sisco, no hi ha pàgina de "man" per aquest programa perquè no n'hi acostuma a haver per aquells programes que usen bàsicament la IGU.

Merci Orestes, m'ho apunto.

---

### Post by jinglada on 2009-07-06
Gràcies Sisco, quitus i Orestes. 
Espero sortir-me'n.
Salut.

---

### Post by orestesmas on 2009-07-06
Bé, jo hauria pogut ser més explícit o acurat (és difícil ser-ho a 2/4 de 3 de la matinada).

De fet, gairebé tots els programes tenen un pàgina "man" o altra. Tanmateix, els programes gràfics acostumen a tenir una pàgina "man" mínima i força inútil, perquè bàsicament descriuen les opcions de crida al programa a través de la línia d'ordres, cosa que no és pas la forma habitual de cridar-los.

Ara bé, en alguna ocasió pots trobar informació interessant, com per exemple com cridar l'OpenOffice per tal que només imprimeixi un document i surti tot seguit. Mira't el "man ooffice".

---

### Post by jinglada on 2009-07-06
> **orestesmas said:**
> De fet, gairebé tots els programes tenen un pàgina "man" o altra. Tanmateix, els programes gràfics acostumen a tenir una pàgina "man" mínima i força inútil, perquè bàsicament descriuen les opcions de crida al programa a través de la línia d'ordres, cosa que no és pas la forma habitual de cridar-los.

Això ja m'aclareix el que has dit en el missatge de la matinada:

> **orestesmas said:**
> no hi ha pàgina de "man" per aquest programa perquè no n'hi acostuma a haver per aquells programes que usen bàsicament la IGU.

He cercat amb el google "IGU" i he trobat coses com ara: 

[http://ca-es.facebook.com/people/Igu-Xupi/757042564](http://ca-es.facebook.com/people/Igu-Xupi/757042564)
Una noia que no m'ha estranyat que tingui 266 amics.

[http://acronyms.thefreedictionary.com/IGU](http://acronyms.thefreedictionary.com/IGU)
Acronym	Definition
IGU	International Gas Union
IGU	International Geographical Union
IGU	Iguassu Falls, Parana, Brazil (Airport Code)
IGU	Indian Geophysical Union
IGU	I Give Up
IGU	Internationale Gruppe für Umweltstudien (Zurich, Switzerland)

etc.:mad:

He conclòs que no anava bé i he pensat que ja ho preguntaria. Amb el missatge últim he deduït que la "G" deu voler dir "gràfic" i tornant a google "IGU gràfic", pàgines en català, i ja ho tenim.:p

Bé, els camins de l'aprenentatge són insondables...;)

---

