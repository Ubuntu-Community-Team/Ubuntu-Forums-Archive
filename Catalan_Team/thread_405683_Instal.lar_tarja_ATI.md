---
title: "Instal.lar tarja ATI"
date: 2007-04-10
forum: Catalan Team
---

### Post by Josep Maria on 2007-04-10
Hola.
El meu ordinador te una tarja gràfica ATI Radeon 600 Pro
He mirat d'instal·lar el Beryl al meu ordenador i no m'arrenca, per això he buscat el driver per a Linux de la tarja.
L'he trobat a la web de ATI, l'he baixat, però no sé com instal·lar-lo.
He provat d'obrir l'scrip clicant a sobre, pero em demana permis de superutilitzador.
Podeu ajudar-me ?

Josep Maria

---

### Post by droijals on 2007-04-10
Josep Maria, bon dia.

Mira, jo crec que és més fàcil fer-ho així:

- Obres *[I]Synaptic*[/I] i t'instal.les el fglrx (vés amb comte amb els linux-restricted-modules)


- Instal.la el driver lliure radeon:

*sudo apt-get install xserver-xorg-video-ati *(et demanarà contrassenya de superusuari)

- Editar el fitxer *xorg.conf* i posa a la secció *device* el driver &#8220;radeon&#8221;, fent:

*sudo gedit /etc/X11/xorg.conf*

Busca la secció *Device* i canvia el driver per &#8220;radeon&#8221;; el *Identifier* no el toquis, i el *BusID* tampoc. Finalment, afegeix les tres opcions en cursiva:

Section "Device"
Identifier  "ATI Technologies, Inc. model de targeta"
Driver "radeon"
BusID  "PCI:1:0:0"
[I]Option "UseFBDev" "true"
Option "EnablePageFlip"
Option "ColorTiling"[/I]
EndSection

- Reinicia. Si tens una targa wifi que depengui dels linux-restricted-modules potser et deixa de funcionar (els hauríes de desinstal.lar o deshabilitar el mòdul fglrx editant el fitxer corresponent)

I a més, si vols instal.lar el driver propietari d'ATI i tenir acceleració gràfica pots fer això:

1.- Activa els repositoris *universe* i *multiverse* i actualitza el teu apt-get (un moment! abans que em peguis :)  et deixo un enllaç on t'ho expliquen pas a pas i amb unes captures de pantalla ben aclaridores [AQUI]("http://dudas.wordpress.com/2006/10/21/repositoriosque-hacer/"))

2.- Una vegada ho tens, si t'en vas al Menú principal / "Aplicacions" / "Afegir i treure", sel.lecciones "System Tools" i tens un click d'instal.lar-ho el "ATI binary X.org driver"

[IMG]http://img228.imageshack.us/img228/2369/atifullri3.png[/IMG]

Salutacions

---

### Post by basdala on 2007-04-10
Cony! Algú sap si aquest sistema té suport per les X1300? La meva em dona problemes, i l'única manera ha sigut instal·lar l'oficial que, per alguna raó, no em dona acceleració completa -i per tant Beryl.

---

### Post by droijals on 2007-04-10
De tota manera, a part de tot aquest *rotllo patatero* que t'he fotut fa un moment :) 

... has sentit a parlar de l'**Automatix 2 Bleeder**? Perqué em sembla que t'aniria força bé, i sense complicacions ... perqué no fas un cop d'ull [AQUI]("http://www.hydorn.es/?p=50") i ens dius què tal?

---

### Post by Josep Maria on 2007-04-11
Hola Droijals :
He provat el que m'has dit.
He instal.lat l'automatix bleeder, però no em deixa instal.lar Beryl, perquè diu que la meva tarja gràfica no està,suportada.
Tinc instal.lat ara el driver ATI que ve amb aquest automatix.
La tarja gràfica funciona, però no tinc acceleració en 3D.
Bé, no és la fí del mon.
He mirat d'istal.lar el driver que vaig baixar de la web de ATI radeon, però no sé quins comandaments haig de posar.
Escolta, parlant de tot, on puv trobar una guia dels comandaments a utilitzar amb la terminal.
Em confón una mica aquesta doble via, de l'entorn gràfic i de la terminal.

Josep Maria

---

### Post by droijals on 2007-04-11
Josep Maria, bona tarda.

He estat mirant una mica aquest tema (donat que la meva resposta és fruit del poc que jo sé i del que he llegit, perqué jo no en faig servir de Tarjeta ATI) i tinc notícies ... no gaire bones :( 

A la Base de Coneixement de la gent de ATI deixen "clar" que els drivers de la ATI no suporten Beryl. 

En anglés ho pots trobar (=llegir) [AQUI]("http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907")

I en castellà, un dels llocs web que se'n fa ressó es l'argentí VivaLinux! (pots llegir-ho [AQUI]("http://www.vivalinux.com.ar/desktop/ati-drivers-vs-3d-desktop.html"))

-----------------

Apart: llista de comandes ... *marchando* ... [AQUI]("http://dunetna.yi.org/docs/comandes-ca.html") en tens una per començar!

Salutacions.

---

### Post by Josep Maria on 2007-04-11
Gràcies :
Bé , potser hi ha alguna manera, pero en tot cas l'accleració 3D no la faig servir gaire.
El que em portava de cap és no poder fer-ho.
Bé quina tarja gràfica va millor per l'Ubuntu?

Josep Maria

---

### Post by sianeu on 2007-04-12
No fa gaire hi havia una pàgina o blog (fred.cpp y sis cosas) que em va ajudar molt a donar les primeres passes pel terminal i ubuntu. Per desgracia ja no hi es, però queden algunes restes dels seus tutorials, per exemple [[COLOR="DarkOrchid"]AQUI[/COLOR]]("http://sigt.net/etiquetas/fred.cpp")

No es el que vaig fer servir per a una ATI 9200SE per que jo vaig instalar Compiz, en aquell moment, pero podries provar......

Es diu que les Nvidia tenen millor soport que ATI, en Linux. I segur que deu ser veritat, però a mi la nova Asus 7600GS m'ha donat molts més maldecaps que la antiga 9200 (i sol·lucionant-los he aprés moltissim....)

Que tinguis sort

---

### Post by MeneK on 2007-04-12
El driver propietari d'ATI (fglrx) el que no suporta és AIGLX, que és la manera directa i elegant de fer servir beryl/compiz. El que es pot fer (i el que jo faig amb una X700) és córrer compiz a sobre de Xgl. 

Aquí teniu un howto detallat: [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

El driver lliure (radeon) suporta amb algunes targes de manera experimental AIGLX. En el meu cas les finestres es quedaven a mig dibuixar, tant amb beryl com amb compiz.

Si esteu fet servir feisty compte: compiz funciona perfecte sobre Xgl, però la versió de beryl que hi ha als repositoris oficials d'Ubuntu no inclou beryl-xgl. Aquí teniu el bug:

beryl-xgl missing from beryl and beryl-core (feisty)
[https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/95394](https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/95394)


Conclusió: ATI mai més!

---

### Post by Josep Maria on 2007-04-13
Gràcies Menek :
Beryl no acaba d'anar bé, s'encalla 
El que em preocupa no és el Beryl, és que vaig instal.lar Feisty i no hi havia manera de fer funcionar la tarja, ni a 2D: no podia passar de 640x 480 i el vaig acabar per desinstal.lar, i tornar a Edgy.
Ara no sé si quan arribi la versió definitiva de Feistt aquest problema continuará passant o no.
Jo he treballat fins fa poc amb Mac, però el G5 últim va sortir un rave i encara és al servei técnic.
No m'agrada Windows i per això he probat l'ubuntu.
Trobo en manca unes quantes coses per poder treballar-hi del tot :
- El Gimp no treballa en CMYK, no el puc fer servir per treballs que surten a impremta.
- No sé com instal.lar les fonts Open Type amb les que fem la revista.
Apart d'això amb l'automatix, l'Edgy funciona prou bé.

De fet aquesta tarja ATI, per linux sembla que és un pot. 
Vaig poder canviar la ressolució de pantalla al intentar instal.lar Beryl per ATI el primer dia que provava l'Ubuntu.
Beryl no va acabar d'anar però no sé perqué el problema de la ressolució de pantalla es va corregir.
D'aquí el meu interés.


Josep Maria

---

### Post by MeneK on 2007-04-13
És possible que no tinguis totes les resolucions configurades a /etc/X11/xorg.conf (jo crec que vaig haver d'afegir la més alta a ma).

Has de buscar la secció "Screen" dins de /etc/X11/xorg.conf . La meva té aquesta pinta:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"

        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

Per a fer una còpia de seguretat i modificar el fitxer, des del terminal:
```

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
$ gksu gedit /etc/X11/xorg.conf
```

---

