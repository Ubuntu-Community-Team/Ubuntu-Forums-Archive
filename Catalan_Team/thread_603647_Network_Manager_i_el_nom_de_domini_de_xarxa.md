---
title: "Network Manager i el nom de domini de xarxa"
date: 2007-11-05
forum: Catalan Team
---

### Post by guillemsola on 2007-11-05
No és el primer cop que faig aquesta pregunta però, l'esperança és l'últim que es perd...

EL que us comentaré em passa amb 3 portàtils diferents i tant amb festy com amb Gutsy. Així que suposo que li passa a tothom.

Resulta que els portàtils es connecten a una xarxa wifi amb el network manager. Ara bé, resulta que sembla ser que com el mode "itinerant" està activat a paràmetres de xarxa és impossible deixar un "nom de domini" sempre el mateix. Això em suposa que per poder accedir a recursos de xarxa tipus discs durs he d'obrir sempre els paràmetres de xarxa i posar un nom de domini cada vegada manualment.

Sembla ser que el network manager escriu automàticament l'arxiu /etc/resolv.conf cada vegada que es connecta a una xarxa nova, de manera que m'hes impossible fixar-lo aquí.

No se si ho faig de manera correcta però és "una mica rotllo" haver de configurar-ho cada cop per poder accedir a recursos de xarxa. Hi ha alguna manera més còmode de fer-ho sense desactivar el mode itinerant? 

He buscat força informació al respecte i no he trobar res. També hem qüestiono si això és un bug i hauria de reportar-ho al LaunchPad, al menys perquè estigues a la "wishlist".

Gràcies

---

### Post by jodufi on 2007-11-05
Com tens compartits els recursos?

Jo tinc un disc dur i m'hi connecto amb el portàtil sigui amb ethernet o amb wifi (mode itinerant). De fet puc estar treballant a un fitxer en la xarxa, desconnectar el cable ethernet, es connecta automàticament amb wifi, i puc continuar treballant amb el mateix arxiu, sense haver de tornar a obrir-lo ni res.

Això ho faig mitjançant una xarxa Samba.

Salut

---

### Post by guillemsola on 2007-11-05
Quina enveja  ;)

Tot ho tinc en una xarxa i treballo amb samba. Basicament tinc un petit NAS i un mini-servidor amb debian a part dels ordinadors.

Faig servir l'explorador del nautilus per navegar pels recursos de la xarxa. Però fins que no tinc un nom de domini a Sistema/Administració/Xarxa no puc explorar els recursos. El nom no ha de necessàriament el del grup de treball, amb qualsevol nom em funciona. Aleshores no tinc cap problema per entrar i explorar els recursos.

Com ja he dit al principi només tenia l'Ubuntu a un portàtil i pensava que seria un problema particular, però ja l'he instal·lat a 3 de diferents amb el mateix resultat.

Així doncs cada vegada que poso un nom de grup de treball quant torno re-iniciar la màquina em queda la casella en blanc. El que tu em comentes de poder treure el cable i passar al wifi sense ni que la màquina s'enteri ja em sembla la hòstia!

Salut!

---

### Post by marcoil on 2007-11-05
> **angrychai said:**
> Sembla ser que el network manager escriu automàticament l'arxiu /etc/resolv.conf cada vegada que es connecta a una xarxa nova, de manera que m'hes impossible fixar-lo aquí.
Gràcies

No és exactament així. Qui canvia el resolv.conf és el client DHCP. Si vols canviar el domini que et ve des de la xarxa, has d'editar /etc/dchp3/dhclient.conf i activar la opció

```
supersede domain-name "domini.cat"
```

Crec que així t'hauria de funcionar...

---

### Post by SiscoGarcia on 2007-11-05
Jo no sé si no entenc quin és el problema que tens, però amb el meu portàtil configurat amb IP dinàmica (DHCP), no tinc cap problema per veure els recursos de xarxa que tinc compartits; i això ho puc fer tant a casa com a la feina. L'únic que he de fer és anar a llocs>connecta al servidor>navega la xarxa>... i fins que trobo aquell recurs que m'interessa, llavors li dic "connecta't al servidor" i li dono el nom amb el qual vull que m'aparegui a l'escriptori. Semblant a crear una drecera amb el finestres, no? Potser és tan senzill com això o estic del tot equivocat?:confused:

---

### Post by guillemsola on 2007-11-05
hola a tothom

primer, he provat a canviar l'opció de /etc/dchp3/dhclient.conf

supersede domian-name "workgroup"

Sense éxit.

Per poder navegar per la xarxa no m'hes tan senzill com clicar a un enllaç directe. Tinc els enllaços fets a les carpetes de xarxa però per que funcioni primer he d'anar a Sistema/administració/Xarxa pestanya general, i on diu nom del domini posar-hi un nom qualsevol. Aleshores ja puc fer servir els enllaços directes i explorar la xarxa sense més incidències.

El problema el tinc perquè aquest nom del domini que poso es perd cada cop que reinicio la màquina.

Potser que estigui relacionat amb que, quant es connecta, es queixi que el servei AVAHI de descoberta de recursos de xarxa no es pugui inicialitzar?

gràcies

---

### Post by guillemsola on 2007-11-07
Per que una imatge val mes que mil paraules us enganxo el menú en qüestió que no soc capaç que "recordi" els valors. Allà on i diu "nom del domini" és no si està en blanc no puc explorar la xarxa.

Com us he comentat el problema és que cada vegada que reinicio l'ordinador aquesta casella està en blanc.

[IMG]http://usuarios.lycos.es/solasoft/xarxa.png[/IMG]

Gràcies

---

### Post by papapep on 2007-11-07
Igual és una pregunta tonta, no et sàpiga greu, però, ja deses el perfil un cop has afegit el nom del domini??

A banda, quan parles "d'explorar la xarxa", a què et refereixes en concret?

---

### Post by guillemsola on 2007-11-07
No tinc cap problema amb les preguntes tontes ja que de cagades tontes en faig sovint, però a que et refereixes amb "desar el perfil"?

Jo escric un "nom de domini" i premo "Tanca". Aleshores aquest "nom de domini" es manté si torno a obrir "xarxa". Aleshores quan reinicio el portàtil la casella torna a estar en blanc. He provat a desar-ho com a una "ubicació" sense èxit tampoc.

Respecte a "explorar la xarxa" em refereixo a Llocs/xarxa. Aleshores mostra un nautius amb ubicació "network:///" per on no puc navegar fins que tinc un "nom de domini" qualsevol.

Salut!

---

### Post by jaume69 on 2007-11-07
Doncs jo quan entro a Llocs,Xarxa,em surt Red windows.Si clikes al cim de la mateixa no em surt res.


Però el que jo voldria saber i em sembla que és com anava dirigit en principi el post,és saber com poguer canviar el nom de la xarxa que et dona el proveïdor.A mi em conecta més ràpid en mode Itinerant,que pas DHCP,em sembla.
[IMG]http://godlike.cl/up/im/19/pantalhyjo.png[/IMG]
Merci.

---

### Post by guillemsola on 2007-11-07
Jo connecto amb mode intinerant.

Jaume69 em sembla que tu el que vols canviar és el nom de la xarxa wifi? per això hauràs de referir-te a la documentació del teu router o buscar a internet. Solen tenir una ip per configurar-los mitjançant web.

He d'aclarir que jo quan entro a "xarxa" també hi diu "xarxa de windows" i que és quan hi intento accedir que esgota el temps de sol·licitud i no pot resoldre res per navegar-hi.

Salut!

---

### Post by lluisanunez on 2007-11-07
> **angrychai said:**
> ... a que et refereixes amb "desar el perfil"?
Jo escric un "nom de domini" i premo "Tanca". Aleshores aquest "nom de domini" es manté si torno a obrir "xarxa". Aleshores quan reinicio el portàtil la casella torna a estar en blanc. He provat a desar-ho com a una "ubicació" sense èxit tampoc.


Fixa't en la imatge que envia Papapep, hi ha una icona amb una fletxa verda que serveix per "Desar" 
Cal dir que la cosa no és molt intuitiva, i que la majoria de finestres de configuració desen automàticament els valors entrats.

---

### Post by guillemsola on 2007-11-07
Al portàtil que estic ara i ha una festy i no hi ha la fletxeta verda però és el mateix que el disquet.

[IMG]http://usuarios.lycos.es/solasoft/xarxa704.png[/IMG]

El que passa és que quan premo el disquet o la fletxeta el que fa és demanar-me un nom per la ubicació. Aleshores creo una ubicació i després quant reinicio el portàtil aquesta ubicació no està seleccionada per defecte i em quedo igual. De fet he provat un munt de combinacions jugant amb aquests botons sense èxit.

Afegiré que per exemple la opció "cerca automàtica de serveis" la puc seleccionar i deseleccionar i que quant reinicio no es perd el seu valor. Però el "nom del domini" sempre es perd.

També he observat que quan arrenco el portàtil el valor que hi ha a /etc/resolv.conf es manté al mateix valor que abans d'apagar-se.

domain=workgroup

Però en quant es connecta a una xarxa wifi perd el  valor del domain. De fet ja avisa que el fitxer no serveix de res de modificar perquè el genera el network manager cada cop.

Ja us dic que no entenc...

---

### Post by jaume69 on 2007-11-11
Ah,doncs tenies raó tu **Angryxai** respecte a poguer canviar el nom de xarxa Inal.làmbrica que s'ha de  fer des de el web.

Però ara tinc un altre problema,el **Network** que no em busca xarxes continuament i només ho fa al principi d'iniciar l'ordinador....¿?

Respecte al teu problema si que no l'entenc gaire bé....
(Prou feina tinc a conectar-me i que funcioni una mica...,pc.),pot ser (**Llocs,Conectar-se a un Servido**r) deu servir més per compartir arxius o navegar  en xarxes locals.

---

