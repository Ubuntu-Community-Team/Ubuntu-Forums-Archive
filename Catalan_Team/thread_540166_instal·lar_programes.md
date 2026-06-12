---
title: "instal·lar programes"
date: 2007-09-01
forum: Catalan Team
---

### Post by muleta on 2007-09-01
Intento instal·lar el  ShareDaemon-wxInterface-0.2.0 i, com que no està en els repositoris, l'he descarregat i l'intento instal·lar amb el terminal però ho dec fer malament perque em surt això dee la captura. 

També he donat l'ordre al Synaptic d'afegir el paquet baixat indicant-li el directori on el tinc, però sembla que passa de mi.

Com el puc instal·lar?.

---

### Post by muleta on 2007-09-01
Em sembla que la captura no surt bé. La repeteixo:

---

### Post by papapep on 2007-09-01
L'apt-get, aptitude i synaptic només saben instal·lar programari de les fonts definides al fitxer /etc/apt/sources.list.

A partir d'aquí, si vols instal·lar un paquet .deb que t'has descarregat pots fer:

```
sudo dpkg -i nom_del_paquet
```

Tot i això, ves amb compte amb els problemes dependències i les incompatibilitats que pots crear instal·lant paquets que  no estan control·lats per les fonts oficials. (no dic que no ho facis, dic que vagis amb compte ;-))

---

### Post by muleta on 2007-09-01
I ara, què he fet malament?.

---

### Post by papapep on 2007-09-01
No ho deus haver fet dins el directori on tens el paquet. 
També li pots dir a l'ordre on el tens.

Suposem que el tens a /home/muleta/descarregues:

```
sudo dpkg -i /home/muleta/descarregues/nom_del_paquet
```

---

### Post by muleta on 2007-09-01
No hi ha manera. 

Què vol dir "dpkg"?. Com saps les paraules màgiques que li has de dir?.

Aquesta ordre no l'he vist en cap tutorial. Com ho he de fer per entendre'm amb el terminal?.

No hi ha un compendi d'ordres bàsiques?.

---

### Post by papapep on 2007-09-01
> No hi ha manera. 

Ho sento, però amb això no entenc què et passa.

> No hi ha un compendi d'ordres bàsiques?. 

Hi ha compendis, però sempre trobaràs coses noves que no saps i has de buscar. L'important és no oblidar el coneixment que es va acumulant. És qüestió de temps.

Respecte dpkg: [http://ca.wikipedia.org/wiki/Dpkg](http://ca.wikipedia.org/wiki/Dpkg)

---

### Post by muleta on 2007-09-01
Em passa que faci el que faci, la resposta és sempre la mateixa.

Però d'on ho has tret que és un fitxer deb?, si no porta pas l'extensió .deb...

A més, els .deb, no són autoexecutables?.

Ja desisteixo de intentar instal·lar programes que no són en el repositori  i no es deixen instal·lar amb el synaptic. També desisteixo de trobar algun substitut de l'amule, que avui m'ha deixat de funcionar per sempre. No sé què faré.:(

---

### Post by muleta on 2007-09-01
He trobat un manual i m'indica que s'han de desempaquetar els codis amb la consola. Jo ho havia fet per "Extreure aquí".

Dono l'ordre i mireu què em respon (per no variar):

---

### Post by pespin on 2007-09-01
Ah, esk el fitxer es un arxiu comprimit tar.gz i no un deb!

A la screen es pot veure al escritori k ja tens descomprimit l'arxiu en una carpeta, aixi que no cal k el descomprimeixis mitjançant la terminal jeje.

De totes maneres no et descomprimeix pq estas situada a la teva carpeta home, i l'arxiu pel que es veu esta a la teva carpeta home/Desktop (la carepta escriptori, k es on tens totes les icones i carpetes que es veuen al fons.

llavors seria:

```
tar zxvf Desktop/nom_del_fitxer.tar.gz
```

Tot i com que ja t'he dit, veig que ja el tens descomprimit. Els tar.gz solen portar el codi font per a que el compilis i aconsegueixis el binari/executable.

per això situa't dins la carpeta descomprimida:

```
cd /home/muleta/Desktop/ShareDaemon-noseque
```

Alla dins tindras un README o un INSTALl que et dira que has de fer, pero normalment per a compilar s'utilitzen 3 comandes:

```
1 -> ./configure
```
Aixo mira que tinguis les dependencies necessaries per a compilar. Si et dona un error normalment es perque et falta instal·lar algun paquet o perque el arxiu configure no existeixi. Si es el 2n cas passa al make.

```
2 -> make
```
Aixo compila el programa. Pot ser que tardi una mica


```
2 -> sudo make install
```
Aixo instal·la el programa. Es a dir, copia els arxius i llibreries i tota la pesca a on toqui.

NOTA: Normalment per a compilar necesitaras el paquet build-essential, que incorpora diferents compiladors i altres paquets. -> sudo aptitude install build-essential

---

### Post by papapep on 2007-09-01
> Però d'on ho has tret que és un fitxer deb?, si no porta pas l'extensió .deb...

No ho he tret d'enlloc. Tu no has dit quin tipus de fitxer era i jo ho he assumit. És alló de "si no ens dones la informació, només podem fer suposicions".

> A més, els .deb, no són autoexecutables?.

No, no són autoexecutables.

---

### Post by papapep on 2007-09-01
Muleta, quan tens problemes d'aquesta mena, pell fòrum es fa extremadament complicat sol·lucionar-te'ls, ja que és un mitjà poc adeqüat per a consultes i respostes ràpides i curtes.
Si vols, aquesta tarda soc al canal d'irc, passa-t'hi i hi fem un cop d'ull.

---

### Post by muleta on 2007-09-01
Me'n he anat al cinema per desconnectar d'aquest joc dels disbarats i ara ho he tornat a provar amb el mateix resultat. He repassat pas per pas, mirant les instruccions. Tot el que em diu l'INSTALL és això:

"INSTALLATION NOTES

Please note that this program is  only a user interface to ShareDaemon core. It
sends  commands to the  core and acts based on what core sends back. If no core 
is running, this program doesn't do anything.

* Compilation
	Just run ./configure at top level of source hierarchy, it should detect
	most  things automatically.  The most  common flags  for configure  are
	--with-wx-config,  which can  be used  to  specify  path  to  wx-config 
	script,  and  --disable-colours,  which,  naturally,  disables  colours
	during configure/make procedure. Run ./configure --help to see the full
	list of options.

  -- wxWindows patching: src/generic/listctrl.cpp (listctrl.patch)
	As  wxListCtrl doesn't  support columns  with width less  than 10 under
	wxGTK  ( and  possibly  under wxMac  also ),  you will  need  to  patch 
	wxWindows  using the  listctrl.patch  to completely  hide columns.  The 
	column-hiding code will work even if you do not patch wxWindows (column
	is considered hidden  if its size is  less than or equal to 10, but the 
	'hidden' columns  will then  have width  10 instead of zero.  Apply the 
	patch in src/generic/  directory in  wxWindows  sources, and recompile.
 
  -- wxWindows patching: src/common/sizer.cpp (flexgridsizer.patch)
	Due   to   missing    wxFlexGridSizer::RemoveGrowableCol()   method  in 
	wxWindows library,  it is  also needed  to  patch  src/common/sizer.cpp 
	file in wxWindows  sources  for  sidebar  hiding  code  to work.  Do so 
	using flexgridsizer.patch file  (apply in the  src/common  directory of 
	wxWindows  sources), and  add --has-patched-wxsizer  flag to configure.

* Note about GTK2
	As  GTK2   support  in  wxWindows   library  is,   according  to  them,
	EXPERIMENTAL,  I will  not officially support GTK2 either. This doesn't 
	mean this  application won't run with  GTK2, it simply means if you run 
	into  problems  with  GTK2,  don't  come  back  crying,  switch to GTK1 
	instead. You have been warned."

Ho faré una vegada més i us enviaré una captura, per si hi veieu alguna errada.

---

### Post by muleta on 2007-09-01
Aquesta vegada hi he introduït la modificació d'eliminar cd: de la primera ordre, per provar.

---

### Post by papapep on 2007-09-01
Tens problemes de concepte Muleta. 

Intentes canviar amb "cd" no a un directori, sinó indicant un fitxer i, clar, el sistema t'ho diu: **Not a directory**

Has de fer el "cd" al nom del fitxer, però SENSE l'extensió .tar.gz. Si mires al teu escriptori (si no has canviat res) ha d'haver-hi la carpeta i fixa't en el seu nom. És igual que el fitxer però sense l'extensió.

Després invoques el fitxer sense més i el sistema no sap què pretens fer.

Seguidament, intentes fer el "./configure", però no ets al directori adeqüat i, per tant, no el troba i et dona error. 
La resta d'errors són conseqüència dels anteriors.

Cal ser molt estricte en executar les ordres a un terminal, sinó res et funcionarà. Ho sento, però és així.

Crec que et cal fer una bona llegida al meu, o qualsevol altre, manual de terminal.

---

### Post by muleta on 2007-09-01
> **papapep said:**
> No ho he tret d'enlloc. Tu no has dit quin tipus de fitxer era i jo ho he assumit.

Perdona Papapep, és que en la carpeta descomprimida no hi diu l'extensió i, al fer tu la suposició, he pensat que ho devies haver deduït d'alguna manera.

Sí, potser hauria estat bona idea entrar al xat. Un altre día m'ho plantejaré. Gràcies.

---

### Post by muleta on 2007-09-01
> **papapep said:**
> Tens problemes de concepte Muleta. 


Crec que et cal fer una bona llegida al meu, o qualsevol altre, manual de terminal.

Crec que sí que em cal i "estoy en ello". El teu és massa tècnic per a mi, però crec que n'he trobat un en la lengua del imperio, força al meu abast. Si tampoc no l'entenc, ja preguntaré.

Però, clar, mentre ho faig, hauria d'anar configurant les coses que encara no funcionen perque, després de tant d'esforç, no voldria haver de tornar a Windows.

---

### Post by papapep on 2007-09-01
El meu massa tècnic??? :-)

Crec que et seria més profitós connectar-te al irc i preguntar el que no entens del manual, de veritat. És el més bàsic que pot ser (això no vol dir que el redactat sigui immillorable, clar) i el contingut no pot anar més avall.

Només és un consell. Agafa-t'ho com a tal, si us plau.

---

