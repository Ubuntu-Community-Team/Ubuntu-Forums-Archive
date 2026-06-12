---
title: "Problemes per  instal·lar DRopbox"
date: 2012-06-24
forum: Catalan Team
---

### Post by joaquimrubio on 2012-06-24
Ubuntu 12.04 actualitzat. 

Dropbox:
A l'instal·lar el programa Dropbox des del Gestor de Paquets Synaptic, es queda penjat, ocupa el 100% de la CPU  i no deixa instal·lar res més, nomès ho puc resoldre matant el procés via Terminal i després desinstal·lant també via Terminal. 
No m'he atrevit a fer la instal·lació via Terminal per por de provocar un desgavell. Algú ha tingut aquest problema i ho ha resolt així? Ho d'una altra manera?

---

### Post by albert-I on 2012-06-25
que hi tens moltes coses? en el Dropbox? jo quant faig canvis de molta envergadura, també li passa. El deixo que carregi tot i desprès funciona be.
Pel que fa a la instal·lació, jo ho he fet a traves del instal·lador i cap problema.

---

### Post by wgarcia on 2012-06-26
Te pinta de ser un problema de connexió de xarxa amb el Dropbox, potser s'hagi de connectar amb els servidors Dropbox durant la instal·lació i no ho pot fer. No em sembla mala idea provar d'instal·lar des d'una terminal, si saps com fer-ho, pot donar més missatges d'error si no completa que ajudin a identificar el problema.

---

### Post by joaquimrubio on 2012-06-26
Albert I: Sí que hi tinc moltes coses, i a mes comparteixo fotos i altres docs amb altres usuaris de dropbox. Però no se m'arriba a instal·lar, em queda penjat a un 85% o així. No sap quin usuari sóc ni quants fitxers hi ha. 

wgarcia: via consola primer he netejat possibles restes d'instal·lacions fallides anteriors i després he provat d'instal·lar-ho via terminal. Em diu que no troba el paquet.
Escrivint dropbox amb minúscula respon el mateix.
Em sorprén que no el trobi quan sí apareix tant al Centre de Programari com al Synaptic. 
A la terminal apareix això:

joaquim@joaquim-G31M-ES2L:~$ sudo apt-get remove Dropbox
[sudo] password for joaquim: 
S'està llegint la llista de paquets… Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet%
E: No s'ha trobat el paquet Dropbox
joaquim@joaquim-G31M-ES2L:~$ sudo apt-get install Dropbox
S'està llegint la llista de paquets… Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet%
E: No s'ha trobat el paquet Dropbox

---

### Post by wgarcia on 2012-06-27
Em sembla que el paquet no es diu "dropbox". He fet el següent des d'una terminal:

```
sudo apt-cache search dropbox
```

això mira a la base de dades de paquets i mostra tots els paquets que tenen la cadena "dropbox". Fet això surt:

```
nautilus-dropbox - Dropbox integration for Nautilus
dvcs-autosync - Automatically synchronize distributed version control repositories
libnet-dropbox-api-perl - Perl module providing a dropbox API interface
python-django-social-auth - Django social authentication made simple
sparkleshare - distributed collaboration and sharing tool
dropbox-share - Dropbox Share
unity-dropbox-share - Unity Dropbox Share
dropbox-index - Dropbox Index
```

Em sembla que el paquet que vols és "nautilus-dropbox", per tant des d'una terminal:

```
sudo apt-get install nautilus-dropbox
```

t'ho hauria d'instal·lar.

---

### Post by joaquimrubio on 2012-06-27
He instalat el dropbox via terminal tal com m'indica wgarcia i a la consola no dona cap missatge d'error, sinó que indica que s'ha instal·lat correctament.

La icona de Dropbox apareix a:  Tauler d'inici - teclejo Dropbox a la pestanya de cerca - apareix la icona Dropbox. Aleshores clico damunt la icona i apareix aquest missatge: 
"Dropbox is running from an unsupported location. Please visit [http://www.dropbox.com/install](http://www.dropbox.com/install) to download and install the latest version.

Don't ask me again                                                   Install Dropbox correctly.

Aleshores, clico sobre install Dropbox correctly i de forma automàtica vaig al lloc web [http://www.dropbox.com/install](http://www.dropbox.com/install), escullo la opció Ubuntu 64 bits, clico allí i se m'engega també automàticament el Centre de Programari Ubuntu amb el següent missatge:

Dropbox.
Trenca el paquet existent "nautilus - dropbox" per conficte amb "nautilus -dropbox". Però "/tmp/dropbox-1.4.0-amd64.deb" el proporciona a través e "nautilus-dropbox"

Error:
Nautilus Dropbox is an extension that integrates the Dropbox web service with your GNOME desktop.


Aleshores he recordat que, abans de demanar ajut al fòrum, quan consultava al web per intentar resoldre el problema per instal·lar el Dropbox,  en algún lloc vaig llegir que, després d'instal·lar el dropbox,  sortia el missatge que m'ha sortit a mi i que calia clicar a la icona "Don't ask me again", encara que sigui contrari a la intuició.
Així ho he fet i problema resolt, s'ha instal·lat el Dropx correctament.

Moltes gràcies a totes les persones de fòrum que heu esmerçat temps i esforç en ajudar-me, sense els vostres guiatges no n'hauria sortit.

---

### Post by joaquimrubio on 2012-06-27
Resumint per si algú es troba amb el mateix problema:

1.- Per instal·lar el Dropbox:

A la terminal, teclejar la següent comanda:

sudo apt-get install nautilus - dropbox

Un cop s'ha instal·lat correctament, quan fem doble clic sobre la icona, pot passar que surti el següent missatge:

"Dropbox is running from an unsupported location. Please visit [http://www.dropbox.com/install](http://www.dropbox.com/install) to download and install the latest version.

Don't ask me again                                                   Install Dropbox correctly.

Cal clicar sobre Don't ask me again, encara que sembli contra el sentit comú, i ja s'instal·la el Dropbox.

---

