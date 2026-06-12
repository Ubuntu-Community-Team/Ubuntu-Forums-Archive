---
title: "modem V92"
date: 2007-09-12
forum: Catalan Team
---

### Post by josep-maria on 2007-09-12
He ficat un modem intern conceptronics V92 de 56 kbs i no funciona. A Ubuntu 6.10.

A sistemes>adminstració>treball en xarxa. Llavors: connexions>connexió modem> propietats> general.
Faig clic a habilitar, li dic el num de telf: *99#, usuari: [email]telefonica.net@telefonica.net[/email], contras.: telefonica.net.
Vaig a la pestanya modem. port del modem: /dev/modem, marcatge: pulsos.

pestanya opcions:
estableix el modem ruta predeterm.: sí
servidor de domini: no
reintenta connexió: no

sistemes>administració>treballen xarxa> DNS.
servidor dns: 80.58.61.250  i  80.58.61.254

però si surto d'aqest menúí i hi torno a entrar a sistemes>adminst.>treball xarxa,  em diu que la interfície del modem no està configurada.
El disc que ve amb el modem i el disc que m'han donat els de la telefònica només són per al windows.

Què haig de fer?

---

### Post by papapep on 2007-09-12
Hola Josep Maria,

Tingues present que nosaltres no sabem què has fet exactament i, per tant, si no ho sabem els consells que et podem donar poden ser bastant fora de lloc.
Ens hauries d'explicar millor què has fet quan dius "fico la configuració que m'han dit", ja que pot ser que sigui correcta, o que no.
Així mateix, quan dius "però si surto i hi torno a entrar" a què et refereixes? si surts del programa de configuració, o si surts d'Ubuntu?

En conclusió, que ho expliquis una mica més detallat, si us plau.

I dona't per benvingut a la nostra comunitat!

---

### Post by orestesmas on 2007-09-13
Estàs completament segur que el nucli de linux reconeix el xipset que utilitza el mòdem?

Si et plau, obre un terminal, executa:

lspci

i posa'ns el resultat. Així sabrem si el maquinari és reconegut o no.

---

### Post by josep-maria on 2007-09-14
com s'obre el terminal?

---

### Post by papapep on 2007-09-14
Aplicacions > Accessoris > Terminal

(parlo de memòria, però crec que es diuen així).

---

### Post by josep-maria on 2007-09-24
Perdó, però no he pogut contestar abans, ja sabeu que no tinc accés a internet.

Si fico lspci al terminal em diu moltes coses. Em sembla que les que ens afecten són:

00:0b.0 communication controller: Connexant unknown device 2f30 (rev 01)

00:11.6 communication controller: VIA technologies, inc. AC'97 modem controller (rev. 80)

Fins aviat.

---

### Post by orestesmas on 2007-09-24
El teu missatge em despista una mica, perquè no sé si el "VIA AC'97 modem" és només una part del mòdem o tot. Ho dic perquè normalment els xipsets de Conexant o són mòdems o són wireless, i la sortida del lspci no ajuda massa a identificar-ho. Jo per exemple tinc un mòdem Conexant al meu portàtil, i la informació és una mica més completa:

02:04.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)        Subsystem: Compaq Computer Corporation Unknown device 8d89

Està clar que no és el mateix que el teu, i per tant la meva experiència pot diferir de la teva, però en el meu cas jo només vaig aconseguir fer-lo funcionar amb controladors privatius, que vaig pagar religiosament. Això era per quan necessitava el mòdem. Per sort, ara ja tinc ADSL i ja no em cal emprar-lo.

L'empresa que els programa es diu "Linuxant" ([http://linuxant.com/](http://linuxant.com/)), i té una versió gratuïta dels controladors, que està "capada" quant a la màxima velocitat que et deixa assolir. Pots provar-la a veure què tal.

El meu consell és que, si pots, no utilitzis el mòdem. Jo sóc partidari d'instal·lar el mínim programari privatiu possible, però potser les teves necessitats són diferents. Hauràs de valorar-ho tu mateix.

Ara bé, si el mòdem és aquest VIA, possiblement estigui suportat (pel mòdul del nucli anomenat "slamr"):

[http://hardware4linux.info/component/16099/](http://hardware4linux.info/component/16099/)
[http://hardware4linux.info/module/slamr/](http://hardware4linux.info/module/slamr/)

Busca una mica a veure si hi ha sort.

Orestes.

---

### Post by josep-maria on 2007-10-11
He entrar a linuxant i no ha entès res. No diu ni què has de fer ni com ho has de fer. Hi ha un munt d'instruccions inintel·ligibles. Em rendeixo. Esperará a que surti una altra edició de l'ubuntu i ja hi hagin ficat el driver. Si no és així, no tinc cap més sol·lució que ficar-hi el windows.

---

### Post by CarlesOriol on 2007-10-11
En aquests casos també és important valorar la llibertat. Jo faria un esforç i si no pugues buscaria algun altre modem. Segurament en pots trobar a preus gairebé regalats a botigues de segona ma.

---

### Post by josep-maria on 2007-10-22
Si canvio el modem per un de més antic, funcionarà? Sense afegir-hi cap programa? On en venen de vells?

Com puc saber quin model s'acceptarà? M'han dit que al disc de l'ubuntu diu quins models accepta, però jo no ho he trobat.

És que sembla mentida que jo sigui el primer a fer servir modems. Ningú no ho ha fet abans? I com entràveu a internet?

---

### Post by papapep on 2007-10-22
La qüestió no és si entràvem o no, que clar que ho feiem, sinó que fa temps que no en fem servir de mòdems (com a mínim parlo per mi).
A banda d'això, molta gent feia servir un altre SO quan encara es connectava a internet per mòdem. ;-)

---

### Post by orestesmas on 2007-10-23
> **josep-maria said:**
> He entrar a linuxant i no ha entès res. No diu ni què has de fer ni com ho has de fer. Hi ha un munt d'instruccions inintel·ligibles. Em rendeixo. Esperará a que surti una altra edició de l'ubuntu i ja hi hagin ficat el driver. Si no és així, no tinc cap més sol·lució que ficar-hi el windows.

A veure: t'ho has mirat bé? jo no ho veig tan inintel·ligible...

1) Entres a la web de linuxant. A dalt hi ha una pestanya que posa "drivers", d'acord? es el que tu vols, un driver, no? som-hi. En passar el ratolí per damunt de la pestanya hi ha 2 opcions: "conexant modems" i "WLAN driverloader". Res de WLAN. Això és xarxa sense fils. Cliquem damunt els mòdems.

2) En la pàgina que ens apareix el segon paràgraf diu ben clar (però en anglès) "Està suportat el meu dispositiu? quins drivers necessito?" Naturalment, són aquestes les preguntes que hem de respondre primer. Anem al menú de l'esquerra i veiem "General -> Identifying your modem". Per tant, cal anar aquí per tal d'aprendre com esbrinar el mòdem que tenim. Cliquem.

3) Al primer paràgraf diu bàsicament que usis alguna eina per preguntar al sistema sobre el tipus de mòdem que tens. Entre els diversos mètodes proposats hi ha el que et vaig dir jo: usar el programa "lspci"cridat des d'un terminal. Segons un missatge teu anterior a tu et surt:

00:0b.0 communication controller: Connexant unknown device 2f30 (rev 01)

El codi del dispositiu és "2F30". Ja és quelcom. Ara tornem a la pàgina web. Al menú de l'esquerra hi ha 2 grans opcions: "HCF (controllerless) driver" i "HSF (Softmodem) driver". Clicant l'una o l'altra se'ns desplega una llista amb els codis dels xipsets suportats. Jo crec que he trobat el teu a l'apartat "HSF (softmodem) driver", concretament a la línia

PCI ID 14F1:{2F20,2F30}

Per tant, tens esperances de que la cosa funcioni. T'has de baixar el driver "HSF". En aquest apartat hi ha submenús, un d'ells és "download". Som-hi.

4) Has d'acceptar la llicència abans de prosseguir. Advertència: és una llicència de programari NO lliure. A banda de les qüestions ètiques que pot comportar, vol dir que estàs completament a les mans del fabricant.

5) Si l'has acceptat se t'obrirà una pàgina amb instruccions sobre com baixar el programa i instal·lar-lo. Imprimeix les instruccions per futures referències i segueix els passos. T'hauria de funcionar. He vist que hi ha drivers per Ubuntu, de manera que la complicació és mínima.

6) Advertència 2: la versió gratuïta del driver no suporta la màxima velocitat. Si vols eliminar aquesta restricció hauràs de pagar una llicència i instal·lar-la.

Fa temps jo em vaig comprar un portàtil i la única manera que tenia de fer anar el mòdem era a través d'aquests controladors privatius. Els vaig estar utilitzant un temps i la veritat és que anaven força bé. Després, feliçment, vaig contractar ADSL i ja no els he necessitat més.

---

### Post by josep-maria on 2007-11-08
Gràcies per l'explicació, ja tinc el driver a un llapis de memòria. Ara com el fico al meu PC?

M'han dit que si hi poso un modem extern, ja no cal cap driver. És veritat? Si és així, quin modem haig de comprar?

---

### Post by orestesmas on 2007-11-09
Precisem-ho: Si el mòdem extern es connecta al PC a través d'un port sèrie convencional (RS-232C), efectivament no et cal cap driver perquè Linux ja sap com gestionar el port sèrie, i les aplicacions només han d'enviar les ordres al mòdem a través d'aquest port. Qualsevol programa de comunicacions ho sap fer això.

En canvi, si el mòdem extern es connecta per USB, podria ser que tinguessis problemes, no pas per l'USB, que Linux ja sap com tractar, sinó perquè alguns d'aquests trastos enlloc d'emular un port sèrie utilitzen un protocol de comunicacions específic entre el PC i el mòdem, i el nucli no sap com "parlar" amb el dispositiu (aquests acostumen a portar un CD amb un driver només per windows, que ensenya al sistema a "parlar" amb el mòdem) . Això és el que passava sovint a l'inici de l'ADSL, quan les companyies telefòniques et subministraven uns "mòdems ADSL" que es connectaven per USB i alguns no eren reconeguts per Linux.

Afortunadament, d'això ja fa algun temps i probablement avui en dia deu ser estrany trobar-te amb un mòdem USB que no sigui reconegut per Linux. Potser aquesta és l'opció, perquè el port sèrie s'està quedant obsolet i no sé si trobaràs al mercat algun mòdem de port sèrie que no sigui una relíquia...

Quant a la pregunta "com instal·lo el driver?", la resposta depèn del format del fitxer. A la pàgina de linuxant veig que el distribueixen de 2 maneres:

1) Un instal·lador executable
2) Un paquet .DEB comprimit específic per ubuntu gutsy.

Si estàs en el cas 1) has de copiar el fitxer en el teu /home, donar-li permisos d'execució (chmod u+x "nom_del_fitxer") i executar-lo amb "sh cnxtinstall.run". Encara que al web no ho posa, potser aquest darrer pas l'has de fer com a root (amb sudo).

Si estàs en el cas 2) copia el fitxer al /home, descomprimeix-lo ("unzip nom_del_fitxer") i instal·la el paquet amb "sudo dpkg -i nom_del_paquet".

En tot cas, mira't les instruccions de la pàgina web des d'on te'l vas baixar.

---

### Post by josep-maria on 2007-11-12
No em deixa ficar l'arxiu .deb.zip al directori /home. Diu que no tinc permisos. L'he ficat al home>pep. L'he descomprimit i l'he executat. M'ha dit al final "license". Crec que ha anat bé. Però tot segueix sense funcionar.

Entro a sistema>administració>treball en xarxa. Ho configuro tot tal com vaig explicar. Faig clic al quadret "habilitar". Faig clic a "tancar". Si torno a entrar a sistema>administració>xarxa, el quadret "habilitar" s'ha esborrat. També s'ha esborrat part de la configuració que hi havia ficat.

I si espero la versió 7.10 de l'ubuntu? Pot ser que ja tingui el driver a dins? Pot ser que el número que marca per entrar a internet ( és el 
*99#) no sigui bo? Perquè esborra la configuració? Sembla que ho esborra tot sense arribar a comprovar el modem. Sembla que no arriba a llegir el driver.

---

### Post by josep-maria on 2007-11-14
Ja tinc l'ubuntu 7.10 i ja l'he instal·lat. Ara ja no esborra la configuració de sistema>administració>xarxa. Però segueix sense funcionar.

El driver (.deb) és al directori home/pep: l'haig de canviar de lloc?

Una altra cosa: tots els menús són en anglès. Quan s'instal·lava tot era en català, però després ja no. He entrat a sistema>administració>suport d'idioma i li he dit que en català. Però no en fa cas i això que he reengegat el pc, tal com m'ha dit.

---

### Post by josep-maria on 2007-12-01
He comprat dos modems: un amb connector usb i l'altre amb RS232. No funciona cap dels dos. Què faig ara?

---

### Post by orestesmas on 2007-12-01
El mòdem USB funcionarà o no depenent del xipset que porti dins. Quina marca és?

El mòdem RS-232 ha de funcionar segur, vaja, si és que el teu PC té un port sèrie operatiu. Què has fet per provar-lo?

---

### Post by josep-maria on 2007-12-03
Tots tres modems són de la marca conceptronics.
No he fet cap prova del connector. Com es fa?

---

### Post by orestesmas on 2007-12-03
No sé massa bé què vols dir amb això de la "prova del connector" (que m'ha sonat a la "prova del cotó, ha ha... :-)

Si el que vols és provar el mòdem extern, fes el següent:

Endolla el mòdem al port RS-232 del PC a través d'un cable sèrie adient (que no sigui creuat). Suposo que el teu PC té ports sèrie, no? Ho dic perquè és un port que està bastant en desús avui en dia, i si el PC és molt nou potser no en porta cap.

Un cop endollat per testejar la comunicació pots fer-ho amb el programa "minicom", que probablement hauràs d'instal·lar prèviament. El seu ús és relativament senzill, només li has d'indicar el port sèrie a usar (segurament /dev/ttyS0 o /dev/ttyS1).

Ara bé, si només vols fer una prova senzilla, obre 2 finestres de terminal. A la primera hi poses:

cat /dev/ttyS0

així totes les respostes del mòdem t'aniran a parar a la consola.

En el segon terminal poses:

```
 echo "AT" >/dev/ttyS0 
```
o bé
```
 echo -e "AT\r" >/dev/ttyS0 
```
o bé
```
 echo -en "AT\r" >/dev/ttyS0 
```

Així envies l'ordre "AT" al mòdem, per tant, si el mòdem és accessible i entén les ordres Hayes, hauria de respondre "OK" a l'altre terminal. Aleshores ja podràs configurar el teu programa de comunicacions (per exemple KPPP en KDE) per trucar al teu proveïdor d'accés internet i establir una connexió telefònica.

---

### Post by josep-maria on 2007-12-19
Si contractés l' ADSL, podria entrar a internet sense cap modem? L' ubuntu funcionaria sense afegir-hi res?
No caldria cap driver ni res per l'estil?

---

### Post by papapep on 2007-12-19
De l'únic que has de tenir cura és de que et portin un router ETHERNET i no un mòdem usb, els quals en algun cas porten problemes.
A partir d'aquí, sigui per wifi (si el router i el teu ordinador ho tenen), o per cable ethernet, si el teu ordinador té placa de xarxa, podràs connectar-te sense problema.

---

