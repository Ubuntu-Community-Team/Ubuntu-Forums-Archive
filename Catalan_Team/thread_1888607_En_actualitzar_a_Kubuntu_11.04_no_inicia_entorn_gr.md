---
title: "En actualitzar a Kubuntu 11.04 no inicia entorn gràfic"
date: 2011-11-29
forum: Catalan Team
---

### Post by nichope on 2011-11-29
Hola ubuntaires.
Em sap greu que el meu primer post no sigui de presentació, però tinc un problema una miqueta urgent de solucionar, i actualment massa poc temps lliure :S.

Començo explicant el problema principal: fins fa 2 o 3 setmanes, havia mantingut el Kubuntu (extret del CD oficial que vaig rebre per correu) en la versió 10.10, i vaig voler actualitzar-lo. Després de baixar tots els fitxers, aplicar l'actualització i esborrar els fitxers innecessaris amb el gestor de paquets, vaig reiniciar l'ordinador. El problema és que en iniciar Kubuntu 11.04 (no sé si és el que fa normalment, però em va actualitzar només a la versió immediatament superior i no a 11.10), no va carregar l'escriptori, i no ho ha fet des d'aleshores. Em demanava nom d'usuari i posteriorment contrassenya, però tot en línia de codi.
Us adjunto el link a un video de l'inici de l'ordinador i el seu comportament que vaig filmar i he pujat, per si pot ajudar:
[http://www.megavideo.com/?d=YGTH7EK0](http://www.megavideo.com/?d=YGTH7EK0)
si no funciona el vídeo, el podeu baixar: [http://www.megaupload.com/?d=YGTH7EK0](http://www.megaupload.com/?d=YGTH7EK0)

Sembla que l'error podria ser greu, perquè li vaig posar un live CD (de l'ArtistX), i no va poder iniciar des del CD, quan anteriorment havia pogut. El que si que em deixa és iniciar desde Windows 7. Per cert, quan intento iniciar "des de versions anteriors de linux" em passa el mateix, però també diu que sóc en una sessió amb Ubuntu 11.04 :S

Un possible antecedent de l'error és que el mateix dia que el vaig intentar actualitzar, havia intentat obrir programes de models químics de molècules en 3D com l'Avogadro i el GBall viewer (em sembla que es deia així) i em donava un error que vaig buscar i que sembla que també es dóna en videojocs, i que em sembla que estava relacionat amb els drivers de la targeta gràfica (tot i que em va estranyar, perquè anteriorment tots dos programes de molècules els havia pogut obrir i manipular perfectament). No recordo el nom de l'error, i com que era a l'historial del navegador al Kubuntu, no ho puc mirar.

He intentat restablir l'escriptori amb les comandes startx i startKDE, però no han funcionat. El que si que em deixa fer perfectament és navegar entre els arxius, tot i que li vaig inserir un pendrive per guardar i recuperar els arxius de la carpeta personal, i a la carpeta "media" no el vaig trobar...

Les especificacions de l'ordinador són:
Model: HP Pavilion dv6 Notebook PC
Processador: AMD Turion II Dual-Core Mobile M500 2.20 GHz
RAM: 4 GB
Targeta gràfica: ATI Mobility Radeon HD 4650 Series
El windows 7 és de 64 bits, i em sembla que el Kubuntu també ho era, tot i que no hi posaria la ma al foc.


Bé, ja no se m'acut gaire més per dir. Vaig estar buscant pels fòrums d'Ubuntu i per Google a veure si trobaba ajuda, però la majoria de gent que tenia aquest problema era en nova instal·lació i per problemes amb la gràfica (però a mi ja m'havia funcionat el Kubuntu 10.10 perfectament durant mig any amb aquella gràfica), o tenia problemes diferents del meu. Em va fer gràcia tenir el navegador tan ple de pestanyes de fòrums i li vaig fer una captura, així que si voleu comprovar que realment vaig buscar ajuda abans de crear el fil, us enllaço la imatge XDD
Si hi ha alguna cosa extra que volgueu saber, digueu-m'ho i ho miraré i/o us ho diré tan aviat com pugui.

Moltes gràcies per avançat,

Nico

---

### Post by orestesmas on 2011-11-29
Bé, realment sembla un problema de drivers. Probablement el driver del nucli i el de les X no són el mateix (han quedat "desincronitzats").

Són problemes empipadors d'arreglar si no et trobes al davant de la màquina, però ho podem provar.

D'entrada caldria veure la sortida de les X en provar d'arrencar. Hauries de provar de fer un "startx" o un "sudo /etc/init.d/kdm restart", i posteriorment enviar el fitxer /var/log/Xorg.0.log. Sense això no podem aventurar gran cosa ara per ara.

Finalment, tot i que sigui potser una bestiesa, en el vídeo veig que has posat a la màquina un "hostname" anormalment llarg. Crec recordar que havia llegit que es recomana que sigui com a molt de 24 caràcters. Pots provar d'editar el fitxer /etc/hostname i canviar-lo per un de més curtet. No fos cas que un hostname massa llarg confongués les X...

---

### Post by nichope on 2011-12-11
Moltes gràcies per la resposta :).
He canviat el hostname per nicolas-pc (he editat l'arxiu amb el Nano), però no s'ha solucionat el problema.
Ni "startx" ni "sudo /etc/init.d/kdm restart" han servit, tot i que en introduir el segon em recomanava que introduís una altra comanda diferent (ara no recordo quina). El fitxer Xorg.0.log sí que l'he pogut trobar i obrir (Nano), tot i que, en introduir tant un CD com un pendrive, no els trobo a la carpeta "media", de manera que no els puc copiar per poder-vos'els enviar des del Windows 7 o qualsevol altre ordinador que em deixi obrir un navegador d'internet per arribar a aquest fòrum.
Com a molt, el que podria fer en un cas extrem seria reescriure el que diu el log (tot i que m'hi estaria una bona estona), o enregistrar en vídeo la pantalla mentre tinc obert el log amb el Nano, i anar baixant en l'arxiu de manera que tirant endavant i enrere en el vídeo es pogués anar llegint el que hi ha més amunt o avall de l'arxiu.

>>Editat:
Tenint en compte que en la interfície gràfica les unitats externes (CDs i USBs) es munten automàticament (segons vaig llegir), vaig pensar que probablement el motiu per no trobar-les a la carpeta "media" era que sense la interfície gràfica no es muntaven automàticament, així que li vaig demanar a un conegut de la universitat amb més experiència en S.O. basats en GNU/Linux i m'ho va confirmar. El problema és que entre ell i jo vam estar mirant el manual de l'ordre "mount", i no hi vam saber trobar l'emplaçament on es troben (en aquest cas) les unitats USB. Algun consell per continuar endavant i poder copiar el log per enviar-lo?

---

### Post by nichope on 2012-01-08
Al final, amb ajuda d'un altre amic, he muntat l'USB i hi he copiat el Xorg.0.log. El penjo en una carpeta .zip perquè el format .log no està entre els admesos. Sento haver trigat tant, però entre festes i estudis no he pogut fer-ho fins ara :S

---

### Post by kimet on 2012-01-11
Sembla un problema del driver privatiu fglrx.
Pots pots provar el driver lliure radeon o radeonhd, per a mi funcionen bé.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by nichope on 2012-01-21
Si ho he entès bé, el que he de fer és treure el fglrx amb 
dpkg -l '*fglrx*' 
I després instal.lar el driver radeonhd, que pel que he vist suposo que ho hauré de fer així:
(sudo) apt-get install xserver-xorg-video-radeonhd
En principi és correcte? O m'he perdut alguna cosa?
Per altra banda, canviar els drivers de la tarjeta gràfica no pot provocar problemes després en iniciar windows (recordem que al portàtil hi faig servir els 2)? O els drivers que toquem només són dintre del Kubuntu (vull dir, si el que canviem no afectarà a la tarjeta gràfica en ella  mateixa ni als altres SO que poguem fer servir)?
Gràcies per l'ajut,

Nico

---

### Post by wgarcia on 2012-01-22
En primer lloc no hi ha cap problema de remoure/instal·lar els controladors gràfics de Linux amb qualsevol altra sistema operatiu, cada sistema operatiu utilitza els seus propis controladors/mòduls. 

En segon lloc la instrucció per remoure el "fglrx" seria:

```
sudo apt-get remove fglrx
```

La instrucció per instal·lar l'altre paquet la veig correcte, tot i que convindria que algú que faci servir targetes ATI confirmi si aquests són els paquets a remoure/instal·lar (jo no he fet servir mai targetes ATI).

En tercer lloc, abans de fer res, des de la línia de comandes jo donaria totes les instruccions següent:

```

sudo apt-get clean 
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

```

a vegades a les actualitzacions queden paquets mal instal·lats que aquestes instruccions arreglen.

---

### Post by nichope on 2012-02-08
Gràcies, wgarcia i kimet :)
Wgarcia, he provat les ordres per netejar i actualitzar les llistes de paquests, i després de reiniciar m'ha dit que hi havia 150 actualitzacions pendents, de les quals unes 120 eren de seguretat. He tornat a executar les ordres, per si actuarien diferentment amb la llista de paquets actualitzada, però m'ha seguit dient el mateix. Suposo que per actualitzar-ho hauria de fer servir
> sudo apt-get upgrade
amb alguna opció específica. He mirat a l'ajuda, però  no hi surt cap opció per actualitzar tots els paquets de la llista, i actualitzar els  150 paquets un per un no em sembla que sigui l'opció :P . Per altra banda, tampoc sé si seria recomanable actualitzar els paquets, o si només em recomanaves fer això per netejar les llistes.

Fet això he executat > apt-get remove fglrx, he comfirmat i s'han eliminat "fglrx" i "fglrx-amdcccle", alliberant 77'8 MB. Us adjunto una foto del que ha dit, per si ha passat alguna cosa anormal, que he vist un parell d'operacions que m'han semblat importants (l'inici del procés és a partir de la cinquena línia que es veu a la foto):

[http://img138.imageshack.us/img138/4808/20120208001.jpg](http://img138.imageshack.us/img138/4808/20120208001.jpg)

Com també podreu veure, he intentat instal·lar el driver radeonhd, però sembla que no l'ha trobat. He reiniciat per veure què passava (com que els drivers de la targeta gràfica no són necessaris par carregar la línia de codi...) i, bé, l'únic canvi era que les lletres sortien una mica més petites xD. He provat apt-get autoremove i em deia que hi havia 5 paquets que es podien esborrar que ocupaven 83'4 MB en total (a part dels 150 no actualitzats). Li he dit que no i he reinstal·lat fglrx (sempre el puc tornar a treure), que s'ha instal·lat junt amb fglrx-amdcccle. També us adjunto la imatge de la info. donada durant la instal·lació. Això és tot. Què us sembla?

[http://img33.imageshack.us/img33/3585/20120208002.jpg](http://img33.imageshack.us/img33/3585/20120208002.jpg)

---

### Post by wgarcia on 2012-02-08
Per actualitzar els 150 paquets, has de fer 
```
sudo apt-get update
sudo apt-get upgrade
```

I després mira les ordres posades aquí:

[http://ubuntuforums.org/showpost.php?p=11643430&postcount=8](http://ubuntuforums.org/showpost.php?p=11643430&postcount=8)

a veure si et milloren la qüestió gràfica.

---

### Post by nichope on 2012-05-05
Fa unes setmanes (o mesos :P) vaig actualitzar els paquets (em sembla que n'hi va haver alguns que no es van poder actualitzar) i vaig intentar provar els diferents drivers que suggeria el post (tot i que no vaig entendre gaire bé algunes coses), però no vaig aconseguir solucionar-ho. També en vaig fer fotos. Per desgràcia, des d'aleshores no he tingut gens de temps liure per posar-me a narrar què vaig fer en cada imatge i explicar-ho bé, així que he decidit que el més eficaç serà esperar a la setmana que ve, que aniré a la festa de llançament del Pangolin, i allà segurament esborraré aquesta versió i faré instal.lació des de 0. Tot i així, abans de desinstal.lar-lo m'agradaria saber què és el que li ha passat al kubuntu del meu ordinador, així que el que proposo és que si algú dels que en sabeu més que jo té curiositat per descobrir-ho o simplement em vol ajudar, podria mirar-s'ho amb mi una estona el dia de la festa i, si descobrim què passava i com solucionar-ho, ho penjo/pengem en aquest post per si pot ajudar algú :)

Algun voluntari? (com que dir "si que vindré i m'interessaria fer-li una ullada. Com quedem?" no crec que aporti gaire ajuda a per resoldre el problema a ningú que visiti aquest fil, m'imagino que serà millor que m'ho dieu per privat)

---

### Post by wgarcia on 2012-05-05
Lamentablement no soc expert en KDE ni puc anar-hi a la festa, però tot i que no trobis cap confirmació estic segur que trobaràs més d'un que t'ajudarà a esbrinar el que ha passat i deixar la instal·lació com cal.

---

