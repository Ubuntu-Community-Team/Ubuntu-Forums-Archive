---
title: "Jaunty Jackalope no detecta l'ATI 9550"
date: 2009-04-24
forum: Catalan Team
---

### Post by kukat on 2009-04-24
He obert altre fil per a veure que ha passat amb la targeta ATI. El problema és el següent: Ara mateix tinc els efectes activats en "Normal" (!!!) però quan vaig a "Sistema", "Administració", "Controladors de Maquinari", em diu: "Aquest sistema no utilitza controladors de propietat", i no em surt res (completament en blanc), per activar l'ATI 9550. 

He fet una comprovació del sistema en "Sistema", "Administració", i em posava açò: "RV350 AS [Radeon 9550] (Secondary)" (entre altres coses).

Jordilin m'ha dit que faça un lspci en la línia d'ordres. Em posa el següent: 

[I]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
[/I]

Per cert, l'ATI funciona sobre AGP, no sobre PCI!!! (per si pot tindre alguna cosa a veure)

Ah! i vaig baixar els controladors de la web d'AMD i em surt el següent missatge a l'instal·lar-ho:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro


Gràcies!

---

### Post by kukat on 2009-04-24
Per el que veig, el que passa es que la Jaunty està gastant la gràfica que té la placa base integrada! El problema es com activar l'ATI.

Per cert, funciona tot de meravella, a pesar de no tindre l'ATI (!!!!) :)

---

### Post by papapep on 2009-04-24
> el que passa es que la Jaunty està gastant la gràfica que té la placa base integrada

...mmm....mmmm...en tot cas, l'Ubuntu farà servir la gràfica on tinguis endollada la pantalla, no????....difícilment en farà servir una, mentre tens la pantalla endollada a una altra... 8-[

---

### Post by kukat on 2009-04-24
Ja.....el problema es que està endollada a l'ATI...però pareix que estiga utilitzant altra cosa! A no ser que ATI haja fet lliures els controladors i per això em diu que no està gastant-ne de propietaris! :)

---

### Post by joseap on 2009-04-24
Una proposta, prova d'instalar l'ultim paquet de ati per linux. El trobaras directament a la pagina de ati.

Potser ajuda, t'instala y configura tot amb el ati control center.

Salut!

---

### Post by PatrickVogeli on 2009-04-24
jo encara no hi veig el problema... que es el que no et funciona? Si tot et va bé, no hi ha cap problema no?

---

### Post by kukat on 2009-04-24
mmm....Hi ha alguna forma de saber si l'ATI està funcionant correctament? bé, de moment tampoc he tingut temps de comprovar-ho tot, però em pareix estrany que no detecte que hi puc insta&#320;lar els controladors restringits.
Ja provaré amb el Open Arena i comente. De totes formes, seria convenient saber com puc instalar el Catalyst Control Center, ja que em tira l'error que he comentat abans.

De totes formes, si està funcionant l'ATI sense haver insta&#320;lat cap controlador propietari, es un gran pas per al programari lliure...jejeje

Salut!

---

### Post by Daerun on 2009-04-24
Fa poc ATI va alliberar unes quantes targetes, però si no recordo malament eren de la serie 4000-escaig, no de la 9000 :P

---

### Post by Jpedros2 on 2009-04-25
Hola Kukat, mira, jo he instal·lat Jaunty en dos portàtils amb tarja ATI, el més modern (des d'on estic escrivint) té una "ATI Mobility Radeon HD 3450", i va perfectament amb els drivers lliures, sempre i quan no li demanes efectes d'escriptori o acceleració gràfica. He instal·lat els controladors propietaris que mostra ubuntu a l'apartat "controladors de maquinari".
Pel que fa a l'altre portàtil és un clònic amb tarja ATI Radeon de fa 5-6 anys, i em funciona perfectament, amb efectes d'escriptori, amb els drivers lliures que per defecte li coloca Ubuntu. No l'he provat amb jocs com l'Arena.

--
Jesús
 
Edite perquè he escrit una informació incorrecta, disculpeu.

---

### Post by kukat on 2009-04-25
Doncs a part de que l'ordinador va de meravella (molt ràpid! ) l'acceleració de la targeta gràfica es inexistent. L'OpenArena no funciona correctament, i em diu alguna cosa de MESA DRIVER. 

¿¿¿¿?¿?¿¿?

---

### Post by kukat on 2009-04-25
Buscant al Synaptic he vist que tinc insta&#320;lat açò:

X.Org X server -- ATI Radeon display driver

Ara em faltaria el fglrx per l'acceleració gràfica, si no m'equivoque! 

[I]"Note that this is not the same as the ATI-provided, binary-only, 'fglrx'
driver, which provides additional 3D functionality for some newer Radeon
cards, but is not supported."[/I]


EDITO: Si insta&#320;lo el paquet "xorg-driver-fglrx", serà com si instalés el driver que em proporciona ATI??? no vull espatllar l'entorn gràfic!

---

### Post by Jpedros2 on 2009-04-25
Hola kukat... 
Hi ha dos tipus de persones:
Les que ja han espatllat alguna vegada l'entorn gràfic
i les que l'espatllaran en algun moment en el futur...

per altre costat, abans t'he donat una informació incorrecta: en el portàtil més nou SI tinc els drivers propietaris instal·lats, en el més antic no. En ambdòs casos tinc una tarja gràfica ATI, com tu, però la més antiga me proporciona efectes d'escriptori sense haver de fer res.
Sort.
--
Jesús

---

### Post by kukat on 2009-04-25
Tens raó, jo també tinc els efectes en mode "normal" sense haver fet res....bé, provaré a veure si puc fer-me amb l'acceleració gràfica! 
Faré una còpia de Xorg....i a provar! jejej
Salut!

---

### Post by kukat on 2009-04-25
Doncs no
No funciona instal·lant el driver aquest.....S'havia espatllat l'entorn gràfic

he tingut que entrar a la consola de recuperació, i després de provar d'arreglar l'entorn  gràfic, solament s'ha arreglat amb açò:

aptitude purge xorg-driver-fglrx

Salut!

Continuarem lluitant a veure que passa......

---

### Post by kimet on 2009-04-25
Si tens instal.lat el paquet "mesa-utils" pots fer:

```
 $ glxinfo | grep direct

```

Pot ser que no tinguesis bé el xorg.conf....
Despres d'instal.lar "fglrx" a hon diu section device:

```
Section "Device"
Identifier  "Configured Video Device"
Driver      "fglrx"
EndSection
```

salut.

---

### Post by kukat on 2009-04-25
El primer em diu açò

kukat@kukatmaulet:~$ glxinfo | grep direct
direct rendering: Yes

Lo del fglrx........es que s'espatlla tot....no se....

---

### Post by kimet on 2009-04-25
Si et diu que "yes" es que tens la acceleració activada.

Fes:```
$ glxgears
``` 
 
A veure si es veuen els engranatges.

Salut.

---

### Post by kimet on 2009-04-25
Potser també et falten aquests paquets:     
    
"libgl1-mesa-dri" i "libgl1-mesa-glx"

Pots instalar-los amb synaptic.

A veure si tens sort.

---

### Post by kukat on 2009-04-26
Si, surten les els engranatges, però els paquets que comentes els tinc insta&#320;lats....
Pot ser falte algún altre?
libgl1-mesa-swx11 ????

:confused:

---

### Post by Jpedros2 on 2009-04-26
Benvolgut Kukat
m'has salvat la vida!
Parlant de carregar-se l'entorn gràfic, mentre intentava instal·lar la darrera versió dels drivers d'ATI, naturalment i com era d'esperar, m'he carregat les X.
El **dpkg-reconfigure xserver-org**, que altres vegades m'havia permés recuperar-lo, es mostrava inútil, igual que la utilitat d'autorecuperació que incorpora Jaunty.
Total que de presa i corrents he engegat el portàtil vell i he començat a descarregar una nova imatge de Jaunty amb la idea d'instal·lar-la de nou abans que la meva dona arribés a casa i necessités l'ordinador.
(Sempre em renya perquè quan les coses van, jo continue trastejant fins carregar-me l'entorn gràfic).

Total, que he vist que tu ho havies arreglat amb

**aptitude purge xorg-driver-fglrx**

i, efectivament,aquesta línia m'ha lliurat d'una bronca domèstica.
... et convidaria a un café.

Moltes gràcies.
--
Jesús

---

### Post by kukat on 2009-04-26
He trobat una possible solució!!!!!

[http://www.tuxapuntes.com/drupal/?q=node/1326](http://www.tuxapuntes.com/drupal/?q=node/1326)


Ara en reiniciar, si no explota res, ho donaré per cert!! De moment ho penje ací, ja que a pesar de que a mi no em funcione, igual a algú li pot resultar útil!

Vaig a veure.....


EDITO: NO FUNCIONA!  per al qui vullga provar-ho, fa exactament el mateix que quan he instal·lat el fglrx des del synaptic. L'entorn gràfic es trenca, i soles es pot llevar amb el comandament:
**aptitude purge xorg-driver-fglrx**

---

### Post by kimet on 2009-04-26
Kukat, si et diu direct rendering: yes, és que tens acceleració gràfica. 
El que passa és que pot ser que el driver lliure no funciona tant bé com el privatiu amb determinades aplicacions
Si no pots fer funcionar determinats jocs que t'interessen hauràs d'instal.lar el fglrx. 

Possiblement, la causa de que és trenqui (que no és carregui) és que has de modificar el paràmetres a /etc/X11/xorg.conf ja que sembla que el jaunty no ho fa automàticament. Hi has de posat a la secció "device" el que t'he dit al post anterior. Si no t'arrenqués sempre el pots tornar a editar amb "nano" desde la consola: ```
nano /etc/X11/xorg.conf
``` i tornar a l'estat anterior.

Però també podria ser un bug:(

---

### Post by kukat on 2009-04-26
ara mateix, el meu xorg.conf està així (per si serveix d'alguna cosa)


S[I]ection "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection[/I]

Pareix que hi haja poca cosa......la veritat....
Em recomana algú el Envy per al Jaunty?? 
Salut!

---

