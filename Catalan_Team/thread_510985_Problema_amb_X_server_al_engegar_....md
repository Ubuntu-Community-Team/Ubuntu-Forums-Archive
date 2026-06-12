---
title: "Problema amb X server al engegar ..."
date: 2007-07-27
forum: Catalan Team
---

### Post by Polete on 2007-07-27
> **CarlesOriol said:**
> Si el que vols és instal·lar l'ubuntu. Baixa't la versió alternate. Un cop fet això pots modificar el xorg.conf per tal de canviar el refresc del monitor. -ja t'explicaria com fer-ho -

Si el que vols es veure el ubuntu des de CD per curiossejar, es pot arreglar però et portarà més maldecaps que satisfaccions.

Hola a tothom, aquest es el meu primer post i estic molt interessat en el món Linux i he triat Ubuntu per fer-ho.

Tinc un problema semblant a CarlesDB. Quan arrenco el live-cd (7.04) em surten els següents problemes:

[INDENT]"Failed to start the X server (your graphical interface)"
[INDENT]"VESA(0): nO MATCHING MODES"
"Screen(s)found, but none have a usable config."
"Fatal server error: no screens found"[/INDENT][/INDENT]

Tot això em succeeïx en un Portàtil (Fujitsu computers Siemens Amilo) amb un adaptador de pantalla ATI Mobility Radeon X1400. El monitor es el propi del portàtil i a mes tinc una pantalla LCD Samsung SyncMaster 710MP.

Provo a baixar-me la versió alternate? L'instalació tambe em recomana que verifiqui la versió d l'X server...

---

### Post by papapep on 2007-07-27
Polete, t'he mogut el post a un nou fil per a no barrejar coses. Per molt que es pugui assemblar a alguna altra consulta si no en barrejem  de diferents quedarà tot més clar ;-)

---

### Post by papapep on 2007-07-27
Respecte el teu problema, crec que podries provar el següent. En un terminal tecleja:

```
sudo dpkg-reconfigure xserver-xorg

```

Vas seguint els passos i configurant les opcions i a veure si et funciona.

---

### Post by CarlesOriol on 2007-07-27
**Cagada pastorets.**

Pots agrair als amics privatius d'ati que aquesta targeta no té suport lliure ni es compatible vesa.
Amb aquesta targeta de vídeo no tens cap so&#320;lució gaire bona per un nou vingut i probablement farà que la teva experiència en ubuntu (i en qualsevol linux) sigui un pel decepcionant ja que et complicarà moltissim la vida.

(Espero que ens veiem a la propera festa per poder ajudar en tot el que quedi pendent)

Però bé... anem per passos:

Cal fer la **insta&#320;lació en mode alternate** i un cop fet i reiniciat **NO t'engegarà.** Et mostrarà un error de configuració de l'xorg.

Llavors insta&#320;les els controladors privatius d'ati.

edites el sources.list
```
 sudo nano /etc/apt/sources.list 
```
i modifiques la linia on diu: 
```
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) feisty main 
```
*(pot ser que despres del main hi digui més coses)*
que quedi ben bonica:
```
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
```
*(ad.archive.ubuntu.com varia segons el servidor)*

surts del nano i fas
```
sudo apt-get update
``` 
*per actualitzar els repositoris*
...
```
sudo apt-get install xorg-driver-fglrx
```
*per insta&#320;lar els controladors privatius d'ati.*

i reconfigures les X amb el consell d'en papapep. 

```
sudo dpkg-reconfigure xserver-xorg
```

amb això t'ha e funcionar. *(Tinc un Aspire 5670 amb el mateix problema.)*

Un cop engegat el sistema gràfic (pots fer-ho amb ```
sudo /etc/init.d/gdm restart
``` ) començaras a patir per gentilesa d'ati.

Coses de les que et pots anar oblindant: beryl / compiz o compiz fusion amb aiglx. Si vols fer-lo anar et caldrà l'xgl i això trinxa bastant l'estabilitat del sistema.

:popcorn: Deixa un post quan hagis arribat (o no) en aquest punt i seguim.

---

### Post by mininomutante on 2007-08-04
Hola!
Doncs jo tinc un problema semblant al company Polete. Se m'ha acodit la genial idea d'activar la targeta gràfica (ATI Radeon 9000 Excalibur 256 M) per provar algun joc (l'ET XD). I he degut fer alguna cosa malament (he seguit un manual d'internet) ja que al reiniciar l'ordinador ja no sortia la interfície de les finestres sino un missatge avisant-me que xserver no es podia iniciar  i que probablement la "interfície gràfica" no estava ben configurada, desprès de provar diverses coses, he utlitzat el command que ha posat papapep més amunt:
dpkg -reconfigure xserver-xorg
Gràcies a això he aconseguit canviar a VESA (no sé on he llegit que era genèrica) i ara puc veure les finestres bé i passejar-me per l'ubuntu com abans però les barres superior em surten amb colors "desconfigurats".
Puc seguir les intruccions de CarlesOriol per activar l'interfície per la meva ATI?
Moltes gràcies.

Edito: Estic comprovant que alguna cosa no va bé, apart del tema de la barra superior, quan minimitzo l'amule en lloc de que quedi al costat del rellotge queda l'icona en blanc a l'escriptori (?), tampoc puc executar el TVTime (sembla que l'obri però en 1 segon es tanca sol). He intentat desintal·lar i tornar a instal·lar els drivers amb ENVY (tan automàtica com manualment) i em surt el següent error:
"There was an error in the installation process. You can see the log file /var/log/envy-installer.log"
No sé si existeix la possibilitat de eliminar tot driver que s'hagi instal·lat amb antel·lació i tornar-ho a provar.
Per si pot ajudar alguna cosa:
[http://img368.imageshack.us/img368/9841/capturajt8.png](http://img368.imageshack.us/img368/9841/capturajt8.png)

---

### Post by papapep on 2007-08-05
Com arreglar-te el merder no se m'acudeix, però per evitar propers problemes d'aquesta mena, abans de tocar coses que funcionen no t'estiguis de fer una còpia de seguretat de l'xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.datadelacòpia
```

Així, amb una simple còpia a l'inversa, tornaràs a ser al punt anterior i si fas un dpkg -reconfigure xserver-xorg podràs revertir les destrosses :-D

---

### Post by mininomutante on 2007-08-05
> Com arreglar-te el merder no se m'acudeix
Ja tens raó papapep, tinc unes mans que semblen peus :).
A la próxima còpia de seguretat :).
Provaré de fer:
dpkg -reconfigure xserver-xorg ... :confused:

A veure si me'n surto.
Gràcies :)

---

### Post by mininomutante on 2007-08-12
Hola,
Un afegit, he donat un cop d'ull als repositoris i veig que tinc instal·lat el:
xorg -driver -fglrx i en les característiques sembla que NO suporti la ATI 9000, pot venir da'quí l'error?
Gràcies

---

### Post by CarlesOriol on 2007-08-13
El controlador privatiu SI que la suporta. Però aquesta targeta et funcionaria MOLT MILLOR amb el controlador lliure.


Aquest fil és un pel enganyós ja que estem parlant de dos problemes diferents. L'inicial d'una radeon X1400 no suportada pels controladors LLIURES i la de mininomutante que és un problema de configuració.

No mescleu temes als posts.

---

### Post by Polete on 2007-08-22
:lolflag: Moltes gracies Carles Oriol, pero tot aixo em ve molt gran ](*,)... de moment;). Em sembla q seguiré amb windows :-# fins q adquireixi un nou equip. Fins aleshores us agraïria recomanacions de hardware.):P

---

### Post by CarlesOriol on 2007-08-23
Com vulguis.

Espero que vinguis a la propera festa que fem (la de la presentació del Gutsy) a mitjans d'octubre i et portis l'ordinador ja veuras com posar-lo en solfa serà un moment. Ens divertirem.

---

### Post by ricoris on 2007-10-13
CarlesOriol, jo tinc el mateix problema que Polete. Encara que sigui complicat, si que vull probar a instal·lar-ho. M'ho pots explicar més a poc a poc tenint en compte que sé molt poc de Linux? 
1. Què és una instal·lació en mode alternate?
2. D'on trec els controladors privatius d' ATI?
3. Per fer tot aquest procés haig d'estar connectada a internet perquè funcioni (ho dic perquè a casa no tinc WiFi)?
Imagino que tu ja estaràs més acostumat a Linux i que segurament les meves preguntes et semblen obvietats però...que hi farem. Tot això em ve de nou.

---

### Post by Ferri on 2007-10-13
> **CarlesOriol said:**
> El controlador privatiu SI que la suporta. Però aquesta targeta et funcionaria MOLT MILLOR amb el controlador lliure.

Compte!!
Almenys la meva ATI 9200SE (suposo que amb una 9000 deu passar el mateix) NO funciona amb els controladors privatius, almenys des de Feisty. Les darreres versions dels controladors privatius d'ATI no suporten les targes antigues con les nostres i les versions més antigues del controlador privatiu no són compatibles amb les darreres versions de xorg.
El controlador lliure sí que va perfectament i em permet, fins i tot, funcionar amb Beryl sense problemes (tot i que no ho faig perquè encara no he descobert de què em serveix).

---

### Post by Ferri on 2007-10-13
> **ricoris said:**
> 
1. Què és una instal·lació en mode alternate?
Fes la instal·lació fent servir la imatge ISO que porta la paraula "alternate", per exemple: [Ubuntu Feisty Alternate]("http://releases.ubuntu.com/releases/7.04/ubuntu-7.04-alternate-i386.iso")
> **ricoris said:**
> 2. D'on trec els controladors privatius d' ATI?
Has d'afegir les fonts de programari "restricted", com ha explicat el CarlesOriol abans.
> **ricoris said:**
> 3. Per fer tot aquest procés haig d'estar connectada a internet perquè funcioni (ho dic perquè a casa no tinc WiFi)?
Si vols fer servir (o bé els necessites) els controladors privatius, sí que necessites connexió a internet, però assegura't abans que els necessites, ja que amb algunes targes gràfiques et poden donar més problemes que no solucions, com ja poso al meu post anterior.

---

### Post by CarlesOriol on 2007-10-13
> **ricoris said:**
> CarlesOriol, jo tinc el mateix problema que Polete. 

Puf... de moment cada ati és un mont. Com pots veure amb el que comenta en Ferri en canvis de nombres de versions molt petits pot canviar molt la cosa.

Posa primer tota la informació de la targeta (model) de l'ubuntu que estem muntant i seguim. 

Sobre tot: NO DESCARREGUIS EL CONTROLADOR DEL WEB D'ATI!!  No cal per res  i després serà complicadissim de treure.

I si pots venir el proper dissabte a Olot segur que tot serà molt més fàcil!

---

### Post by Ferri on 2007-10-13
Per ser més precís, he fet una petita recerca:

- La darrera versió compatible dels controladors privatius amb ATI 9250 o anterior és la 8.28.8
- Aquesta versió funciona amb versions d'xorg fins a la 7.1
- La versió d'xorg a Ubuntu, des de Feisty, és la 7.2

En el seu moment vaig estar intentant diversos mètodes per fer funcionar els drivers privatius a Feisty amb xorg 7.2, però no hi va haver manera. Afortunadament vaig descobrir que els lliures anaven millor que els privatius (tot i que en versions més antigues d'Ubuntu no hauria pogut dir el mateix).

Abans d'instal·lar els drivers privatius d'ATI val la pena anar a la web [drivers ATI]("http://ati.amd.com/support/driver.html") i assegurar-se que la tarja que tenim és compatible amb els controladors que volem instal·lar i amb la versió d'xorg que fem servir. Un cop fet això, com diu el Carles, NO descarregueu el controlador d'allà. Us serà molt més fàcil arreglar els problemes que puguin aparèixer si instal·leu la versió de les fonts "restricted", que sol ser la mateixa o molt poc endarrere de la que hi ha a la web d'AMD/ATI.

---

### Post by CarlesOriol on 2007-10-13
Tampoc està de més un cop d'ull a: [http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon).

Personalment els ordinadors que tinc amb ati 

una mobility radeon 9600 : gutsy 64 bits > El controlador lliure va fantàstic amb efectes d'escriptori a "tot-i-ple" i el privatiu no va.

una x1300 ; gutsy 32 > El lliure no va, no va ni tan sols el controlador vesa!!. Sols funciona el privatiu. Els efectes d'escriptori funcionen amb xgl.... brgghhh

Això de les atis sembla que esta canviant... però encara li falta un parell de voltes.

---

