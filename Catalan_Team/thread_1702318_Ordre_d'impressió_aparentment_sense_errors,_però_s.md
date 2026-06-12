---
title: "Ordre d'impressió aparentment sense errors, però sense imprimir."
date: 2011-03-07
forum: Catalan Team
---

### Post by Funk'u on 2011-03-07
Hola a tot-hom!, m'és difícil trobar on cercar ja que no em dona cap  error, si més no com a usuari, com a root ho poso més abaix.

Senzillament  al voler imprimir un document, és posa a la cua d'impressió, com si  anés bé, i al cap d'un parell de segons em diu que ja està fet, però  l'impressora no s'ha immutat.

El sistema reconeix l'impressora,  marca i model, és una multifunció Epson Stylus dx3800, val a dir que  escaneja sense problemes i la tinta és nova.

Coincideix que abans  sortia l'icona de l'impressora a la barra d'estat al connectar-la, ara  no, tant sols surt quan li dius que imprimeixi i després desapareix,  això com a usuari, com a root ni surt. I com a root no puc obrir el  pre-visualitzador de documents (Document Viewer 2.32.0). Tot va passar  d'un dia per altre, potser a causa d'una actualització no ho puc  confirmar, com a root  quan el vols visualitzar surt un missatge al  terminal que diu;

"No protocol specified
Cannot parse arguments: No es pot obrir la pantalla: "

"caution: filename not matched:  Thumbnails/thumbnail.png
convert: no decode delegate for this image format `/tmp/magick-XXBsgH1n' @ error/constitute.c/ReadImage/532.
convert: missing an image filename `png:/tmp/.gnome_desktop_thumbnail.CIH4RV' @ error/convert.c/ConvertImageCommand/2970.
composite: no decode delegate for this image format `/tmp/.gnome_desktop_thumbnail.CIH4RV' @ error/constitute.c/ReadImage/532.
composite: missing an image filename `/tmp/.gnome_desktop_thumbnail.CIH4RV' @ error/composite.c/CompositeImageCommand/1607."

"Error: Unknown Metadata type: '???'"

"sys:1: GtkWarning: IA__gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed"

El maquinari és el següent;

Portàtil
Acer Aspire 5741g,
Intel Core i5-450M (2.4GHz, 3MB L3),
4GB DDR3, Nvidia GeForce GT 320M (1GB dedicat),
Multifuncío Epson Stylus DX3800

El SO Ubuntu 10.10 de 64-bits

Gràcies per interessar-vos per el post. :smile:

---

### Post by akyra on 2011-03-08
Hola Funk'u,

A mi em pasa una cosa semblant amb una multifunció Brother wifi cada vegada que actualitzo el Ubuntu. En la meva imperssora s'ilumina la pantalla que porta durant dos segons i després no fa absolutament res (també em diu que s'enviat el document a l'impressora).

Com et connectes a la impressora, per xarxa o per USB?

Proba a fer en el navegador [http://localhost:650](http://localhost:650)
T'apareixerà el servidor d'impressió i veuràs l'estat de la impressora.
Jo normalment la donc de baixa i la torno a donar d'alta i acaba funcionant (a vegades ho faig uns quants cops), i no torna a fallar fins que no torno a instal·lar novament l'Ubuntu.

Ja diràs com evoluciona.

---

### Post by Funk'u on 2011-03-08
Hola akyra, gràcies per contestar tant ràpid!

La connecto per usb, posant [http://localhost:650/](http://localhost:650/) em diu el següent:

"Error d'anàlisi XML: entitat no definida
Ubicació: jar:file:///usr/lib/firefox-3.6.14/chrome/toolkit.jar!/content/global/netError.xhtml
Número de línia 60, Columna 12:    <title>&loadError.label;</title>
-----------^"

He probat d'eliminar i tornar a posar l'impresora, i ha funcionat el que imprimeixi alguna cosa (però malament), he mirat els controladors, i d'entrada no n'hi cap per aquesta impressora a la llista, he mirat al netbook que hi tinc l'Ubuntu 10.04 i el controlador és [COLOR=DarkSlateGray]Epson Stylus DX3800 - CUPS+Gutenprint v5.2.5 Simplified[/COLOR], el curiós és que ja ho tinc instal·lat tot el referent al Gutenprint, fins hi tot ho he tornat a reinstal·lar.

Doncs la veritat és que no l'havia agut de configurar i anava perfectament, al 10.04 tampoc l'havia hagut de configurar. :-k

Moltes gràcies igualment ;-)

---

### Post by akyra on 2011-03-08
Hola Funk'u,
L'error que et dóna sembla d'un problema en algun plugin de java del navegador que utilitzis, sembla que sigui el firefox, però em despista el directori de "chrome". Si pots prova un altre navegador, a veure que succeix.

Has provat de canviar les opcions en el [http://localhost:650/](http://localhost:650/) ?

Has mirat el post que he pasat sobre el Webmin? Potser et pot ajudar.

Ja diràs.

---

### Post by kimet on 2011-03-08
1-El port de la impresora es el 631 (si  no l'has canviat)[http://localhost:631/](http://localhost:631/) 
2-Esta aixecat cups? ```
sudo cupsd
```
3-Estàn instal.lats: hplib, hplib-gui, hplib-cups etc...?

Salut

---

### Post by Funk'u on 2011-03-08
Hola kimet i akyra!, doncs sembla "l'Expediente X", ara posant el [http://localhost:650/](http://localhost:650/) ja no surt l'error esmentat avans, surt sencillament:
"No s'ha pogut connectar
El Firefox no ha pogut establir una connexió amb el servidor a localhost:650."

Per altra banda posant com diu en kimet [http://localhost:631/](http://localhost:631/) si que em surt el CUPS, el navegador per defecte és el Firefox, i secundari el Iron Linux, tot i que hi tinc el Seamonkey, Chromium, ELinks, Epiphany i l'Opera, per anar testejant, (la carpeta "chrome" podria ser d'importació d'adreces d'interès del Chromium?).

> 
2-Esta aixecat cups?      Code:
     sudo cupsd 
Això ja està fet

> 
3-Estàn instal.lats: hplib, hplib-gui, hplib-cups etc...?
Això també hi és
> L'error que et dóna sembla d'un problema en algun plugin de java del navegador que utilitzis, sembla que sigui el firefox...Provaré d'anar treguent els connectors a veure que hi passa.
> Has provat de canviar les opcions en el [http://localhost:650/](http://localhost:650/) ?La veritat és que no hi he remenat mai res al Cups.
> Has mirat el post que he pasat sobre el Webmin? Potser et pot ajudar.M'ho havia estat mirant abans, però és per administrar servidors, no?, de tota manera sembla primer de tot alguna cosa de connectors, si li dic que m'ho cerqui ell mateix no en surt cap a la llista, no sé pas d'on ha tret el 10.04 el [COLOR=DarkSlateGray][COLOR=Black]Epson Stylus DX3800 - CUPS+Gutenprint v5.2.5 Simplified. En aquesta versió veig al synaptic que és el 5.2.6.

Vaig remenant a veure que en trec, gràcies als dos!!
[/COLOR] [/COLOR]

---

### Post by akyra on 2011-03-08
Perdó, error greu, és el [http://localhost:631/](http://localhost:631/)

Torna a provar a veure que surt.

Ho sento, però no tenia l'ordinador davant.

adeu

---

### Post by Funk'u on 2011-03-08
> Perdó, error greu, és el [http://localhost:631/](http://localhost:631/)Tranqui, ja m'ho ha semblat que volies dir això, encara que no entenc perquè em sortia aquell error posant el 650, que curiós, no?.



Salut!

---

### Post by Funk'u on 2011-03-11
M'han comentat que el més segur és que s'hagi carregat el firmware de l'impressora al
actualitzar el kernel.

Bé, i dic jo, és possible, que encara ho tingui i només l'hi hagi de dir a on para?, algú sap a quina carpeta és guarden els controladors de l'impressora?, potser només és qüestió de restaurar, que us sembla?.



Salut!

---

### Post by wgarcia on 2011-03-13
Coses que es poden provar:

1) Arrencar el grub des d'un nucli (kernel) més antic a veure si la impressora et funciona.

2) Crear un altre usuari al teu ubuntu i provar si imprimeix des d'aqueste altre usuari, no sigui que s'hagi desconfigurat alguna cosa al teu usuari habitual.

3) Donar de baixa la impressora de de "Sistema -> impressió" i donar-la d'alta amb el menú que se t'obre navegant amb algun navegador a "http://localhost:631". Jo ho vaig haver de fer amb una impressora HP però no havia sentit que aquest problema estigués present també amb les EPSON, però qui sap.

---

### Post by Funk'u on 2011-03-14
> **wgarcia said:**
> Coses que es poden provar:

1) Arrencar el grub des d'un nucli (kernel) més antic a veure si la impressora et funciona. És el primer que vaig provar, i fèia el mateix.
> **wgarcia said:**
> 
2) Crear un altre usuari al teu ubuntu i provar si imprimeix des d'aqueste altre usuari, no sigui que s'hagi desconfigurat alguna cosa al teu usuari habitual.
Està igual, també ho he provat.
> **wgarcia said:**
> 
3) Donar de baixa la impressora de de "Sistema -> impressió" i donar-la d'alta amb el menú que se t'obre navegant amb algun navegador a "http://localhost:631".
També ho he provat, a la llista de controladors no surt cap del meu model ni semblant, he provat diferents models per veure si colava algun, però res, cap[COLOR=DarkGreen] Epson Stylus DX3800[/COLOR] ni DX el que sigui, ni cap controlador semblant al de l'Ubuntu 10.04 que tinc al netbook el [COLOR=DarkSlateGray][COLOR=Black][COLOR=DarkGreen]CUPS+Gutenprint v5.2.5 Simplified[/COLOR], de fet no em surt cap CUPS+Gutenprint tot i que el tema del Gutenprint ho tinc instal·lat.


Moltes gràcies wgarcia, perdona el retard!



Salut!
[/COLOR][/COLOR]

---

### Post by wgarcia on 2011-03-15
Mira a veure si els controladors que ofreixen en aquesta pàgina:

[http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do)

et serveixen. 

El més semblant que es veu al teu model és Epson PRO 6800

---

### Post by kimet on 2011-03-15
A open printing hi ha els drivers que s'han provat a les diferents impresores i la valoració.

[http://www.openprinting.org/printer/Epson/Epson-Stylus_DX3800](http://www.openprinting.org/printer/Epson/Epson-Stylus_DX3800)

---

### Post by Funk'u on 2011-03-15
> **wgarcia said:**
> Mira a veure si els controladors que ofreixen en aquesta pàgina:

[http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do)

et serveixen. 

El més semblant que es veu al teu model és Epson PRO 6800

Osti gràcies!, miraré també si hi és a la llista de configuració.

L'error el pujo amb ".txt" , bé, l'he comprimit amb ".gz" perquè em deia que no podia coma ".txt"

Vaig a provar el que m'has comentat, moles gràcies wgarcia!!

---

### Post by wgarcia on 2011-03-15
En aquests casos de textos tan llargs és que s'ha de fer és usar un editor de text (Accessoris - Editor de text), enganxar el text, desar un fitxer (error.txt per exemple) i adjuntar-lo al missatge.

---

### Post by Funk'u on 2011-03-15
He estat mirant, aquí surt el meu model [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
i suposo que hauria d'agafar "for CUPS", però només hi és en ".rpm" o bé ".tar.gz", el controlador per l'escàner si que hi és en ".deb", però ja em funciona perfectament això.

Ho he intentat instal·lar amb ".tar.gz" però al fer "./configure" em dona un error, (poso les últimes línies i prou);

"...[COLOR=DarkRed]checking whether to build shared libraries... yes
checking whether to build static libraries... yes[/COLOR]
[COLOR=DarkOrchid]checking whether -lc should be explicitly linked in... no
creating libtool
checking for cups-config... no
./configure: line 7470: test: =: unary operator expected
configure: error: *** 'cups-config' missing, please install CUPS or fix your $PATH ***[/COLOR]
[COLOR=DarkRed]joma@joadma:~/bin/pips-scx3700-2.6.3$ [/COLOR]"

i clar al fer "make" o "make check" o "sudo make install" em diu;

[COLOR=DarkOrchid][COLOR=Black]"[/COLOR]joma@joadma:~/bin/pips-scx3700-2.6.3$ make
make: *** No targets specified and no makefile found.  Stop.[COLOR=Black]"[/COLOR][/COLOR]

I dic jo; al instal·lar això no pot tenir cap conflicte amb el Gutenprint?, i per altra banda si instal·lo un controlador només d'impressora suposo que deixaria de funcionar l'escàner, oi?.

El "ltdl7" ja el tinc instal·lat, suposo que és el que em fa anar l'escàner.


Merci per la paciència, salut!

---

### Post by wgarcia on 2011-03-15
També hi ha controladores per l'escàner (i em sembla quer per la copiadora i el fax) al mateix lloc. 

Ara bé, el missatge que et surt sembla com si no estigués ben instal·lat "cups", perquè "cups-config" l'hauria de trobar. 

Des d'una terminal si es dóna la instrucció:

sudo dpkg -l cups

es podrà veure si està ben instal·lat el cups.

---

### Post by Funk'u on 2011-03-15
Doncs em dona això;

[COLOR=DarkRed]joma@joadma:~$ sudo dpkg -l cups
[sudo] password for joma: 
Desitjat=desconegUt/Instal·la/supRimeix/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom            Versió        Descripció
+++-==============-==============-============================================
ii  cups           1.4.4-6ubuntu2 Common UNIX Printing System(tm) - server
joma@joadma:~$ [/COLOR]

Tornaré a reinstal·lar CUPS, gràcies, comento el resultat.

Ostres kimet perdona, no havia vist el teu post, m'apunto l'enllaç, moltes gràcies.


Salut!

---

### Post by wgarcia on 2011-03-16
El cups sembla bé instal·lat, posa "ii" al principi cosa que vol dir que està instal·lat. 

Què et surt quan fas des del terminal:

which cups-config

?

---

### Post by Funk'u on 2011-03-16
> **wgarcia said:**
> ... Que et surt quan fas des del terminal:

which cups-config?

Doncs sembla que no faci res;

joma@joadma:~$ which cups-config
joma@joadma:~$ 

I mirant no sembla que hagi canviat res... 8-[



Salut!

---

### Post by wgarcia on 2011-03-16
Aquesta comanda "which" no ha de fer res, sols dir-te on tens el programa "cups-config" que és el que sembla que el programa de configuració per instal·lar el controlador no troba. 

Ara m'estranya que no digui res, hauria de dir-te on està (a mi em surt /usr/bin/cups-config) o dir "no trobat" o alguna cosa així. 

Què et surt si fas 

ls /usr/bin/cups*

?

---

### Post by Funk'u on 2011-03-16
Hola, posant el que em demanes;

[COLOR=DarkRed]joma@joadma:~$ ls /usr/bin/cups*
/usr/bin/cups-calibrate  /usr/bin/cupsdoprint  /usr/bin/cupstestppd
/usr/bin/cupsdconf       /usr/bin/cupstestdsc
joma@joadma:~$ [/COLOR]

M'has donat l'idea de proporcionar-li a la configuració de la impressora el fitxer PPD, hi ha tres opcions, la de buscar el model a la llista, cosa que no hi es, la de proporcionar el fitxer PPD i la de cercar un controlador que no en troba cap, la segona no l'havia probada. Val a dir que al dir-li on és, he suposat que era aquest [COLOR=DarkRed] /usr/bin/cupstestppd[/COLOR] i no el trobava com un fitxer PPD, ossigui que no ho deu ser, oi?.

[COLOR=DarkRed]No s'ha pogut llegir el fitxer PPD, aquests en poden ser els motius:
/usr/bin/cupstestppd: FAIL
      **FAIL**  Unable to open PPD file - Line longer than the maximum allowed (255 characters) on line 1.
                REF: Page 15, section 3.1.
        WARN    File contains a mix of CR, LF, and CR LF line endings!

[COLOR=Black]
Gràcies wgarcia, Salut![/COLOR]
[/COLOR]

---

### Post by wgarcia on 2011-03-16
És estrany, jo tinc tots aquests fitxers que tens tu, però a més tinc cups-config.


/usr/bin/cups-calibrate  /usr/bin/cupsdconf    /usr/bin/cupstestdsc
/usr/bin/cups-config     /usr/bin/cupsdoprint  /usr/bin/cupstestppd


No sé què instal·la el cups-config, perquè no és un paquet en si mateix. Però sembla que el controlador que t'has baixat i que volies configurar per compilar-lo i instalar-lo necessita aquest fitxer.

---

### Post by Funk'u on 2011-03-18
Hola, doncs resulta, que al netbook amb Ubuntu 10.04 també tinc els mateixos arxius i em va de perles:

[COLOR=DarkRed]marta@pitifu:~$ ls /usr/bin/cups*
/usr/bin/cups-calibrate  /usr/bin/cupsdoprint  /usr/bin/cupstestppd
/usr/bin/cupsdconf       /usr/bin/cupstestdsc
marta@pitifu:~$ [/COLOR]

De moment per poder imprimir arxius d'aquest, connecto els dos ordinadors amb sshfs des de l'altre ordinador, treballant des de l'altre.

Mirant la llista d'impressores per triar veig que hi surten molts més models d'Epson, entre ells tota la sèrie DX incloent-hi la meva.

Llavors per el Synaptic he vist que l'únic que no tinc instal·lat és el foomatic-db, i si li dic que me'l instal·li em diu que eliminarà l'ubuntu-desktop i el foomatic-dc-compressed (encara que elimini aquest prèviament m'elimina l'ubuntu-desktop), ossigui que no ho puc provar, tot i que hi tinc més coses instal·lades, referent a gutenprint, cups i foomatic.

Potser que els controladors d'aquesta nova versió hagin deixat de suportar tota una sèrie de models vells d'Epson?.




Salut!

---

### Post by Funk'u on 2011-03-21
Val, sembla que finalment me'n estic sortint; he deshabilitat la impressora, i amb el Synaptic, he reinstal·lat de nou tot el que tenia instal·lat referent a Gutenprint, CUPS, ink, inkjet i printer, (potser algún no fèia falta) llavors he fet al terminal "sudo killall cupsd" i seguidament "sudo cupsd".

Però no m'agrada no ser conscient del perquè del problema ni del perquè s'ha sol·lucionat.

He tornat a habilitar la impressora, i m'ha sortit l'esperada llista de models d'Epson, he pogut triar el meu, i hi han dues versions, una simplificada i una igual però que no diu simplificada (que no sé quina diferència hi ha), he agafat la que no diu simplificada i sembla que va perfecte, imprimir i escanejar, tot i que no em deixa netejar capçals o veure el nivell de tinta.

[COLOR=DarkRed]Error del servidor CUPS
S'ha produït un error durant l'operació del CUPS: «client-error-document-format-not-supported».[/COLOR]

Abans tampoc ho podia fer, ho feia amb escputil, que també funciona bé ara.




Salut!

---

### Post by wgarcia on 2011-03-22
Que bé que s'hagi solucionat, a vegades passa que algun paquet queda mal instal·lat i s'arregla amb "la solució de l'informàtic": apaga i torna a engegar (en aquest cas desinstal·la i torna a instal·lar). Ningú no sap perquè pero funciona :confused:

---

### Post by Funk'u on 2011-03-22
Ja m'estava superant, i m'he dit a prendre pel sac torne'm-hi!, aquesta era l'opció "A", la "B" era instal·lar la pròxima versió i la "C" dur-ho tot a cal metge.

[COLOR=Black]Em queden dues espines i no sé si tancar el fil i obrir-ne un de nou, o bé seguir amb aquest:
[/COLOR]
- Al Xsane (no cal dir que ho he tornat a reinstal·lar tot el referent a Xsane) em surt un error que al tancar-lo és torna a obrir tres vegades abans no s'obre el programa, quan s'obre s'enfosqueixen les finestres del programa mig segon, i només puc pre-visualitzar, al escanejar no surt cap imatge, abans no ho feia i m'anava molt bé, tot i que escaneja bé amb el Simple Scan.

[COLOR=DarkRed]S'ha produït un error en la conversió CMS: No s'ha pogut obrir Perfil ICM de l'escàner.
[/COLOR]
- El tema de que no pugui utilitzar les opcions que t'ofereix el configurador d'impressora i que em diu:

[COLOR=DarkRed]Error del servidor CUPS
S'ha produït un error durant l'operació del CUPS: «client-error-document-format-not-supported».[/COLOR]



Moltes gràcies, salut!

---

### Post by wgarcia on 2011-03-22
Millor obre un altre fil amb el títol apropiat, a veure si algú que sàpiga sobre el xsane pot donar una mà.

---

### Post by Funk'u on 2011-03-22
D'acord wgarcia, així ho faré doncs, dono aquest tema per tancat, moltes gràcies per l'ajuda!!

Salut! :lolflag:

---

