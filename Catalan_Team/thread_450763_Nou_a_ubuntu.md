---
title: "Nou a ubuntu"
date: 2007-05-21
forum: Catalan Team
---

### Post by kukat on 2007-05-21
Que passa!!
Salutacions a tots i totes!!
Escric des de Castalla (Pais Valencia), per fer algunes preguntes!! 
Fa uns mesos vaig comensar a introduir me al mon linux amb Sabayon, pero ara he instalast el Ubuntu 7.04 Studio. Esta molt be!!

Preguntes
1. He fet be, o era millor instalar el Feisty Fawn...
2. Com es fa per a utilitzar l-escriptori 3d
3. M-instala la tarjeta grafica (Club 3d Radeon x1650 professional) o tinc que instalar la, per que he tingut que tornar a instalar el Ubuntu per que al instalar la tarjeta no anava, es quedaba la pantalla en negre....ajuda!!!

I per ultim perd'o per la lletra, no funciona be el teclat!! Es que acabe d instalar/lo i crec que ho he configurat mal!!! Ara vaig a vorer si ho solucione!!:D

---

### Post by kukat on 2007-05-21
EL problema es que no hem surt l opcio d efectes d escripori a Sistema, Preferencies....no se el que que passa pero no hi es. Que passa!!!! 
gracies a tots per adelantat!!

---

### Post by orestesmas on 2007-05-21
Benvingut, company.

Si et dediques a temes multimèdia, ja has fet bé. T'estalviaràs configurar coses.

Per activar l'escriptori 3d primer has de tenir l'acceleració gràfica de la tarja ben configurada i funcionant. Obre un terminal i tecleja "glxinfo". Has de veure una línia que posi "Direct Rendering: Yes". Si és així vas bé i podem passar al segon pas, que és instal·lar el beryl i l'emerald. Confirma el pas 1 abans de prosseguir.

La teva tarja no la conec, no sé si l'acceleració estarà suportada pel driver lliure (radeon), per privatiu (fglrx) o per cap dels dos... Si el lliure funciona millor, el driver privatiu és força marrano i jo he tingut molts maldecaps amb ell.

---

### Post by MarkCat on 2007-05-21
vale! jo tb sóc nou i m'uneixo a aquests passos!

a mi sí que em surt el yes aquest... però tinc el feisty fawn... millor poso l'altre?

la meva tarja és la ati 9600...

---

### Post by orestesmas on 2007-05-21
No, la Feisty ja està bé.

Ara has d'instal·lar el beryl i l'emerald. Després has d'anar al menú i executar el beryl-manager. T'hauria de quedar un nou símbol vermell a la barra de tasques, i t'hauria de funcionar ja el Beryl. Mou les finestres. Es comporten com si fossin "de goma"?

---

### Post by kukat on 2007-05-22
Vaja lio!!! 
He baixat els drivers de ati.de/suport, i no consegueixc instalar-ho!! La meva tarjeta es una ATI club 3d Radeon x1650pro, i he baixat els drivers de Linux x86, Radeon, Radeon x1600 series... no ho he fet bé?? 

quin mal de cap!! ajuda!!

---

### Post by kukat on 2007-05-22
baixe els drivers, que deuen de ser els correctes (!!!), i a la consola pose ./nomdelarxiu, i comença a instalar-ho, però al final hem surt el seguent:

Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.b12812

---

### Post by orestesmas on 2007-05-22
A veure company, abans de començar a instal·lar controladors baixats directament del web de ati/nvidia etc. mira d'usar els controladors que ja venen empaquetats pel sistema que utilitzes. Això SEMPRE és preferible perquè si els tens integrats en el sistema de paquets i els vols eliminar només cal que facis "sudo aptitude remove <paquet>, mentre que els controladors baixats directament del fabricant són fàcils d'instal·lar, però la desinstal·lació l'has de fer generalment "a mà" i és fàcil deixar-se coses.

T'estàs fent un embolic. Asserena't i pensa fredament els passos que has de seguir, perquè altrament acabaràs amb un bon maldecap i pocs resultats. T'ho dic per experiència pròpia.

Tens una ATI. El primer que has de provar és si el controlador lliure (radeon) te la suporta. Mira, obre una consola i tecleja: "sudo dpkg-reconfigure xserver-xorg" i quan et pregunti el tipus de tarja tu escull "radeon". Per la resta d'opcions accepta els valors per omissió i quan hagis acabat reengega les X fent:

"sudo /etc/init.d/gdm restart" (o canviant gdm per kdm si uses KDE)

o pel mètode guarro d'apretar Ctrl+Alt+Backspace

Ara prova el "glxinfo" en un terminal. Et surt el Direct Rendering: Yes ????

---

### Post by Ferri on 2007-05-22
El driver que t'has baixat no suporta la teva versió d'Xorg, la 7.2, que és la que ve a Feisty; la darrera que suporta és la 7.1.
Com t'ha dit, oblida't dels drivers d'ATI, que solen donar més problemes que no n'arreglen, especialment si vols efectes 3D a l'escriptori.

---

### Post by MarkCat on 2007-05-22
ja em funciona el beryl!!

però... què és això de l'emerald? és necessari?

---

### Post by kukat on 2007-05-22
AHHHHHHHHHHHHHHHHHHHHHHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Ja no hem funciona res!! he fet el que has dit, he posat "sudo dpkg-reconfigure xserver-xorg" a la consola, he escollit ATI (no surt RADEON, hi he pensat que seria ATI...) i ho he posat tot per defecte....Després, al posar el seguent que mas dit (lo de "restart") se m'ha quedat l'ordinador bloquejat. L'he reiniciat, però ara ja no s'inicia el Ubuntu, hem diu que no tinc configurada bé la X, i hem surt en mode consola......que faig!?Deu ser que la tarjeta es AGP en lloc de PCI-Express o aixó no te res a veure?? (es el primer que se m'ha ocurrit!!) 

Gràcies per adelantat, espere que m'ajudeu a solucionar el problema... ufffff, si fa falta el tornaré a instalar :sad:

---

### Post by MarkCat on 2007-05-22
això és just el que em va sortir a mi ahir!!! doncs tu, reinstal·la i et funcionarà xD

---

### Post by kukat on 2007-05-22
El reinstale i faig els mateixos pasos que abans, i hem sortirà tot bé??? 

Gràcies!!! Estic desitjant veure l'escriptori!!!

I Gràcies a tots, es un plaer no tindre que parlar en cristià!!! Visca la terra! (jejej);)

---

### Post by CarlesOriol on 2007-05-23
Markcat. Estas donant un consell a kukat que no és gens correcte. Els problemes no es soucionen reinsta&#320;lant, i com pots veure a més la gràfica de la que et parla no és la mateixa que la teva.

La serie X16xx d'ati no esta suportada pel controlador lliure. Per tant reinsta&#320;lant sols tindrà maldecaps i tornarà al mateix punt on es troba ara. ...i el controlador privatiu amb aixgl no funciona bé.

Una so&#320;lució pot ser canviar el xorg a XGL... però això encara pot complicar més la vida a qualsevol usuari novell.

Les gràfiques ati tenen molts problemes i cada una és un mon diferent. Cada una té un cert nivell de "compatibilitat" però degut a la falta d'informació que ha ofert el fabricant i la mala qualitat dels controladors privatius que per definició limiten tot bon ús que se'n pugui fer l'han auto-marginat en el mon del programari lliure.

AMD (que darrerament va comprar ATI) ens ha promés que properament lliurarà el codi font dels controladors. És una gran noticia... però fins que no ho facin pixarem sang.

Com t'he dit abans, no t'enfadis, però esborrar i insta&#320;lar no serveix de res i insta&#320;lar controladors de que no hagi preparat la comunitat d'ubuntu sense abans no comprendre llegint tota la documentació sobre els avantatges i inconvenients que cada un comporta sols pot desestabilitzar-te el sistema.

---

### Post by kukat on 2007-05-23
Per lo tant no puc fer res per a poder veure l-escriptori 3d? Tinc que esperar a que traguin els d-ati la solucio? QUina llastima!!

---

### Post by patrickfromspain on 2007-05-23
abans de tot: l'escriptori 3D no es ni beta... ES ALPHA. A no se que tinguis una intel o segons quina nvidia, es un mal de cap fer-lo funcionar. Vaja, no es massa recomendat per a novells. Si et passa aixo que et quedes amb una pantalla en negre i no saps per on tirar deixa-ho correr de moment.

Salut

---

### Post by Miquel Ubuntero on 2007-05-23
Hola a tots.
En MarkCat comenta que te una Radeon 9600. Jo tinc la mateixa i hem va perfecte amb Ubuntu 7.04
Tinc habilitat a Sistema -Administració - Gestor de controladors restringits, el controlador ATI.
Fàcil i funciona.
referent a Ubuntu o Ubuntu Studio, crec que son el mateix, la ùnica diferencia és que el studio te més aplicacions audio/video i connectors ja preinstal.lats; la qual cosa t'estalvia feina.
Salut companys!

---

### Post by orestesmas on 2007-05-23
Noi, sento que el consell no hagi funcionat. Certament, el nom del driver a escollir era ati, no radeon. Bé, si dius que no s'inicien les X el millor és veure perquè: a la consola tecleja la següent ordre:

grep "(EE)\|(WW)" /var/log/Xorg.0.log

i envia'ns la sortida. Això mira el fitxer de log de les X i busca les línies que continguin (EE) o (WW), és a dir, errors i warnings.

---

### Post by kukat on 2007-05-24
kukat@kukat:~$ grep "(EE)\|(WW)" /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom


Aixo es el que surt. 
Per cert tinc al menu per triar els S.O. uns quants UBUNTU. Quina diferencia hi ha entre el Low Latency i el normal???? Jo trie el normal... el low latency es per a quan hi ha algun error, com el recovery mode?

---

### Post by CarlesOriol on 2007-05-24
El lowlatency és un mode de funcionament del núcli bàsicament per al tractament d'audio en temps real multipistes i similars.

S'insta&#320;la predeterminadament en l'ubuntustudio però es pot posar a qualsevolr altre "*sabor*".

No afecta en res al funcionament dels controladors de video, ni als restringits ni als lliures.

---

### Post by kukat on 2007-05-26
Orestesmas, contestam alguna cosa!! mes que siga alguna tonteria, estic desitjant veure la resposta. Perdona si es que encara estaves cavilant la resposta... .jejejeje, de bon rollo. 
Per cert, algú de vosaltres utilitza el ubuntu studio per a gravar música??? Tinc una Ibanez amb una pedalera d'efectes amb conexió USB, Hi ha algún programa per a grabar la guitarra amb una pedalera ZOOM???? Seria meravellós!!

---

### Post by CarlesOriol on 2007-05-26
kukat. No mesclem temes als fils. Jo també tinc una pedalera zoom i l'ubuntustudio. Obre un altre fil i en parlem.

---

### Post by kukat on 2007-05-31
Orestesmas, senc tornar a insistir, però com hem vas dir que et donara la sortida, i encara no m'has dit res, te la torne a possar:

kukat@kukat:~$ grep "(EE)\|(WW)" /var/log/Xorg.0.log
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom


jejejeje, es que vull veure si puc de una vegada vorer l'escriptori 3d!!! que hem morc d'enveja (sana) cada vegada que el veig pel youtube!!!. ;)

Espere que no t'ho prengues a mal!!.

---

### Post by papapep on 2007-05-31
> Orestesmas, senc tornar a insistir, però com hem vas dir que et donara la sortida, i encara no m'has dit res, te la torne a possar:

Insistint, com a molt, conseguiràs que la gent s'enfadi i passi de contestar-te. Pensa que qui vol, i pot, contestar-te ja ho farà i qui no vol no ho farà i punt. No forcis les coses.

Salutacions.

---

### Post by kukat on 2007-05-31
No!!!! No pretenia aixó. Però pensava que igual havía oblidat aquest post, només aixó. Son moltes preguntes que contestar a moltes persones,  i se li pot oblidar de contestar-me. No pretenia enfadar a ningú!!! :(

---

### Post by AlexMuntada on 2007-05-31
> **kukat said:**
> (EE) AIGLX: Screen 0 is not DRI capable

Si no ho tinc entès malament, això significa que no tens suport per al Beryl,
si més no amb el controlador que hagis triat.

Com ja t'han comentat altres companys, pensa que el Beryl és una cosa
que encara està un pèl verda i, tot i que funciona bé en alguns casos,
dóna força maldecaps quan no funciona bé (per exemple, quan les
finestres no es mostren correctament).

---

### Post by orestesmas on 2007-06-01
Ho sento!! Entre tants mails, posts, llistes, coses de la feina (sí, també treballo) i altres se m'havia passat aquest fil.

com diu n'Àlex, el controlador que uses no suporta l'acceleració gràfica (DRI, direct rendering infrastructure), i per tant AIGLX no es pot carregar i el beryl no funcionarà.

Recapitulant: tens un ATI Club 3d Radeon x1650 professional, i deies que si escollies el driver lliure "ati" no s'iniciaven les X (tot negre). Per tant, assumeixo que uses el driver privatiu (fglrx). Amb aquest driver has de saber que NO suporta AIGLX segur, per tant no podràs executar Beryl. [Aquesta pàgina del wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") diu clarament:

> In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. To disable Composite you must edit the /etc/X11/xorg.conf file, so add these lines at the end of xorg.conf: .

Per mi, només tens una esperança: és molt estrany que el driver lliure no funcioni *gens*. S'hauria de veure alguna cosa, ni que sigui en mode de compatibilitat amb VESA. Per tant, intueixo que no el vas instal·lar correctament. Segueix provant amb el driver lliure i intenta descobrir perquè no et funciona. Quan aconsegueixis fer-lo anar, potser el beryl et córre. Et pot ajudar mirar el fitxer /var/log/Xorg.0.log a veure quins missatges dónen les X en arrencar.

Això és tot el que puc dir per ara.

---

### Post by CarlesOriol on 2007-06-01
Orestes el controlador lliure d'ati és molt millor que el privatiu però t'adjunto la compatibilitat:

Full 3D Support

    * 7000 / rv100 based cards.
    * 7200 / R100 based cards.
    * 7500 / rv200 based cards.
    * 8X00 / R200 based cards.
    * 9000 / rv250 based cards.
    * 9100 / R200 based cards.
    * 9200 / rv280 based cards.

 
Experimental 3D Acceleration

    * 9500 / R300 based cards.
    * 9600 / rv350 or rv360 based cards.
    * 9700 / R300 based cards.
    * 9800 / R350 or R360 based cards.
    * X300 / rv370 based cards.
    * X600 / rv380 based cards.
    * X700 / rv410 based cards.
    * X800 / R420 or R423 or R430 or R480 based cards.
    * X850 / R480 or R481 based cards.

 
2D Acceleration Only

    * Xpress 200M Northbridge integrated GPUs

 
Unsupported

    * X1300 / R515 based cards.
    * X1600 / R530 based cards.
    * X1800 / R520 based cards.
    * X1900 / R580 based cards.

La x1650 (x1600) no funciona.

He trobat aquest problema en algunes targetes i sols pots fer una insta&#320;lació alternate i un cop dins (en consola) inta&#320;lar el fglrx. 


Això d'ati ja comença a ser una mica angoixant. Espero que facin alguna cosa.

---

### Post by orestesmas on 2007-06-02
Ok. Tens raó, Carles, hauria d'haver mirat la llista prèviament. Kukat, sento haver-te guiat erròniament. Amb aquesta ATI no tens massa esperances de fer córrer el beryl, sembla.

---

### Post by patrickfromspain on 2007-06-02
be, tampoc es tan dificil fer correr el beryl amb aquesta tarja :) Si el driver FGLRX et funciona, hi ha moltes esperances de que puguis fer anar beryl amb XGL:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

encara que aixo pot portar altres problemes associats, pro ja es una altre tema i no m'el conec massa... En el portatil de la meva novia (x1100) va funcionar perfectament i de moment no s'ha queixat.

salut!

---

### Post by orestesmas on 2007-06-02
Ep, una mica després he anat a [aquesta pàgina d'ATI]("http://ati.amd.com/support/driver.html") (Linux X86 -> Radeon -> X1600) segons la qual la X1600 està suportada per la versió 8.37.6 del driver.

Això és un cacau.

---

### Post by orestesmas on 2007-06-02
Tens raó, més val que en qüestió de targes ATI em quedi calladet en el futur. Segons l'enllaç que poses XGL funciona (però no el recomanen).

El més curiós és que, si el Beryl és el mateix amb XGL que amb AIGLX, per què coll*** funciona amb l'un i amb l'altre no? Quines ganes de tocar la pera!

---

### Post by jmaspons on 2007-06-04
Vaig obrir un post amb un [problema semblant]("http://ubuntuforums.org/showthread.php?t=432683"). Jo també vaig tenir problemes instal·lant ubuntu al portatil de la meva companya que té una targeta gràfica ATI Mobility Radeon X1300 que també surt a la llista de targetes no suportades. Segueix la [documentació]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") a veure si et funciona.

A mi em va funcionar amb el compiz, no ho he provat amb el beryl.

Sort!

---

### Post by kukat on 2007-06-06
Bona Tarda a tots!!!

No he contestat des de feia uns dies, i es que avui he tingut un examen de Linux!!! jejeje (de comandaments i shellscripting, pero molt senzillet...) I tenia por de tocar alguna cosa i estropejar-ho i no poder estudiar!!

Ara ja me l'he carregat!! (el Linux) :D   . Però aquesta vegada ha sigut diferent, no se m'ha quedat la finestra bloquejada, no ha passat res. I al reiniciar l'ordinador: NO ES PODEN INICIAR ELS X (o com siga) I he agafat els errors:

(WW) RADEON: No matching Device section for instance (BUS ID PCI:1:0:1) found  ( o not found, no se, no es veia be)
(EE) No devices detected.

Fatal server error; no screens found

I també (però aço deu ser algun error de tipus de lletra): (WW) The directory "/usr/share/fonts/x11/cyrillic" does not exist...jejeje.

Bé, jo crec que l'error es que la tarjeta funciona amb el bus AGP, i al configurar-ho crec que ho he fet amb PCI: Quan es demana a l'instalació del bus de la targeta de video jo ho deixe per defecte: PCI:1:0:0

que tinc que fer???? Si hi ha que posar que es un bus AGP com ho pose? 
I altra cosa: Ara no funciona Ubuntu, es queda en mode de text, hi ha alguna forma de fer que torni com estava abans????

Gràcies a tots!!!

---

### Post by Ferri on 2007-06-06
Aquest error crec que és el mateix que vaig veure jo quan vaig intentar instal·lar els dirvers propietaris a Feisty. Però, teòricament, el meu problema s'explicava perquè la darrera versió dels drivers d'ATI ja no suporta la meva tarja (9200SE) i les versions antigues no són compatibles amb la versió d'xorg que vé amb Feisty. Jo hi vaig arreglar passant-me al controlador lliure.
En el teu cas, però, teòricament sí que està suportada la teva tarja i, en canvi, no tens l'alternativa del controlador lliure. Depenent de la versió que hagis agafat, pots intentar-ho amb una altra (la que et pots descarregar d'ATI o la que hi ha alts repositoris restringits d'Ubuntu). Però potser millor que primer intentem tornar a X (però a Linux tot es pot fer des de la líniia de comandaments).

Teòricament diu que no et troba la tarja on hauria de ser. posa:
```
lspci | grep VGA
```
T'hauria de dir quelcom així:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
```
Si els primers són com els meus, assegura't que a xorg.conf t'hi diu això a la secció "Device":
```
BusID		"PCI:1:0:0"
```
Mira també que la manera com tens identificada la tarja a la secció "Device" i el monitor a "Monitor", coincideix amb el que et posa després a Screen. És a dir, en el meu cas (he esborrat línies d'enmig per treure palla):
```
Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
EndSection

Section "Monitor"
	Identifier	"L1710M"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Monitor		"L1710M"
EndSection
```
Per editar xorg.conf des de fora d'X:
```
sudo nano /etc/X11/xorg.conf
```
Per desar ctrl-o i per sortir ctrl-x.

Per tornar a la teva situació prèvia:
```
cd /etc/X11
dir xorg*
```
Sortirà una llista amb les còpies que tens de versions prèvies d'xorg.conf. Dues bones opcions a intentar són xorg.conf~ (~ es fa amb alt-126) i xorg.conf.2007###### (un número que depèn del dia i hora que es va fer la còpia).
```
sudo cp xorg.conf xorg.conf.backup   <- posa-hi un nom que no et surti al llistat d'abans
sudo cp [la còpia d'xorg que hagis triat] xorg.conf
```
I torna a intentar iniciar X.
Si no et funciona, pots anar-ho intentant fins que en trobis un que funcioni.

Ja ens diràs com va...

---

### Post by kukat on 2007-06-06
iEP!!!
Primerament, gràcies per ajudar-me, i per escriure tot aixó!!jeje.

Primerament he escrit lspci | grep VGA, i m'ha sortit el mateix que a tu, però amb la meva targeta. 
Després he posat sudo nano /etc/x11/xorg.conf, però no hem surt res!! Solament una pantalla en negre que a dalt posa " GNU nano 2.0.2   File: /etc/x11/xorg.conf" i baix " ^G ^O...etc" 

Per cert, no se si et referies a posar : bus ID , però hem surt uns DEBUG, ERROR: USAGE, ERROR: bus [-d ....] 

Soc un poc novato (no un novato extrem, però si que hem queden moltíssimes coses per apendre!!)  ho senc

I es un mareig el teclat, les tecles no estàn iguals!! Sempre hem passa aixó quan entro.

---

### Post by papapep on 2007-06-06
Atenció a les majúscules i minúscules. NO és indiferent. El fitxer està a:

sudo nano /etc/X11/xorg.conf (fixa't en la X majúscula).

La pantalla negra que dius que posa NANO a dalt i demés, és que estàs a l'editor de text NANO. (per sortir fes Ctrl+x)

La comanda que executes significa:

sudo ---> demanes per executar com a superusuari (root) una comanda en concret, tot i estar com a usuari normal.

nano ---> crides l'editor de text, la comanda que has demanat d'executar com a root

/etc/X11/xorg.conf ---> el paràmetre que li passes a la comanda, o sigui, el fitxer que edites amb el Nano.

---

