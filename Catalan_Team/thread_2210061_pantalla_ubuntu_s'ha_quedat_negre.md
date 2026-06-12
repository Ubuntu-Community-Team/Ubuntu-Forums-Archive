---
title: "pantalla ubuntu s'ha quedat negre"
date: 2014-03-08
forum: Catalan Team
---

### Post by pserra on 2014-03-08
Hola,
fa un parell de setmanes vaig passar-me a la 13.10, sembla més estable que la 12.10.
Però tinc un problema generat per mí:
l'altre dia afegint programes  vaig voler actualitzar controladors nvidia.
I des de llavors em fa un acosa enstranya... quan em carrega la pàgina principal on entro la contrasenya es veu bé... però un cop entro al meu perfil em queda la pantalla negre...
He provat d'actualitzar controladors amb el programa: intel-linux grafics-instaler
Però la pantalla un cop entro com asuari no em va.. QUE POT SER?
GRÀCIES

---

### Post by wgarcia on 2014-03-09
Convindria saber quina targeta NVIDIA tens exactament, cosa que es pot saber fent:

```
lspci | grep -i vga
```

des d'una terminal, i quin controlador estàs fent servint, si és controlador propietari et sortirà a Paràmetres de sistema -> Programari i actualitzacions -> Controladors addicionals

---

### Post by pserra on 2014-03-09
Hola wgarcia
el que em mostra és:
pere@pere-PC:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
el controlador que faig servir no te'l puc mostrar, ja que no tinc access a paràmetres de sistema... ja que només puc obrir terminal amb les tecles: Ctrl+alt+t i si vull obrir navegador el tinc que obrir des de el terminal....
el meu portàtil és in Compaq Presario CQ71 de 5 anys..

però si entro:
pere@pere-PC:~$ lspci -vmmnn
Slot:	00:00.0
Class:	Host bridge [0600]
Vendor:	Intel Corporation [8086]
Device:	Mobile 4 Series Chipset Memory Controller Hub [2a40]
SVendor:	Hewlett-Packard Company [103c]
SDevice:	Device [306b]
Rev:	07

Slot:	00:02.0
Class:	VGA compatible controller [0300]
Vendor:	Intel Corporation [8086]
Device:	Mobile 4 Series Chipset Integrated Graphics Controller [2a42]
SVendor:	Hewlett-Packard Company [103c]
SDevice:	Device [306b]
Rev:	07
... no sé si aquesta informació pot ser d'ajuda...

---

### Post by wgarcia on 2014-03-09
Bé, aquest tipus de targeta gràfica no té controlador propietari, els d'Intel han deixat el codi obert i per tant les seves targetes estan plenament suportades. Per tant no entenc el que dius que actualitzant els controladores NVIDIA s'ha espatllat el sistema gràfic, perquè no veig per enlloc que s'hagin de fer servir en aquest sistema (segons el que mostres no tens targeta gràfica NVIDIA). 

Abans de continuar, una cosa fàcil a provar és el següent: Si tens l'usuari "Invitat", prova d'entrar a aquest usuari a veure si aquí també té problemes el sistema.

---

### Post by pserra on 2014-03-09
Hola wgarcia.... 
si va ser error meu... creia que tenia nvidia i vaig cometre l'error d'actualitzar el que no tenia...
he provat d'entrar com a usuari convidad (guest) i se'm queda negre igualment..
però el que m'estranya que si a través del terminal obro navegador puc connectar-me... sense veure l'entorn ubuntu(botons, barres, menús..)
Hi ha alguna manera 'simple' de solucionar el problema?
Gràcies.

---

### Post by wgarcia on 2014-03-09
Mira a veure si no s'ha desinstal·lat el programari de l'escriptori. Prova de fer

```
sudo apt-get install ubuntu-desktop
```

a veure què et diu.

---

### Post by pserra on 2014-03-09
Hola wgarcia....
aqui tens:> pere@pere-PC:~$ sudo apt-get install ubuntu-desktop
[sudo] password for pere: 
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
ubuntu-desktop ja es troba en la versió més recent.
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
pere@pere-PC:~$ 

la pantalla s'ha quedat igual...

---

### Post by wgarcia on 2014-03-10
Quin escriptori estaves usant, l'escriptori estàndard de l'Ubuntu (Unity)?

---

### Post by pserra on 2014-03-10
Hola,
és el standar Unity...
he estat fent proves i ara quan em carrega la pagina negra em surt una finestra que em diu: System program problem detected..
             do you want to report the problem now?

---

### Post by wgarcia on 2014-03-11
Prova a veure si reinstal·lant l'escriptori es vol arreglar:

```
sudo apt-get install --reinstall ubuntu-desktop
```

Si et torna a sortir el missatge d'error intenta acceptar la demanda d'informar de l'error, a veure si es pot esbrinar quin error és i si està relacionat amb el problema de la gràfica. 

Mira també la sortida de l'ordre:

```
ls /var/crash
```

Aquí hi ha els informes de fallada per pujar al sistema d'errors i potser algun també està relacionat amb aquest problema.

---

### Post by pserra on 2014-03-11
Hola Wgarcia,
gràcies per el teu interès....
el que m'està passant és molt "misteriós"....no ho acabo d'entendre... el que m'està passant....
gairabé em venen ganes de tornar a instal·lar el 13.10 altre cop.... a veure va millor i començo de 0-
he fet el que m'has dit i:
code:
> 
pere@pere-PC:~$ sudo apt-get install --reinstall ubuntu-desktop
[sudo] password for pere: 
S'estÃ* llegint la llista de paquetsâ&#8364;¦ Fet 
S'estÃ* construint l'arbre de dependÃ¨ncies       
S'estÃ* llegint la informaciÃ³ de l'estatâ&#8364;¦ Fet
0 actualitzats, 0 nous a instaÅ&#8364;lar, 1 reinstaÅ&#8364;lats, 0 a suprimir i 17 no actualitzats.
S'ha d'obtenir 4270 B d'arxius.
DesprÃ©s d'aquesta operaciÃ³ s'empraran 0 B d'espai en disc addicional.
Bai:1 [http://ftp.caliu.cat/pub/distribucions/ubuntu/archive/](http://ftp.caliu.cat/pub/distribucions/ubuntu/archive/) saucy/main ubuntu-desktop i386 1.307 [4270 B]
S'ha baixat 4270 B en 0s (14,6 kB/s)
(S'estÃ* llegint la base de dadesâ&#8364;¦ hi ha 708119 fitxers i directoris instaÅ&#8364;lats actualment.)
S'estÃ* preparant per a reemplaÃ§ar ubuntu-desktop 1.307 (emprant â&#8364;¦/ubuntu-desktop_1.307_i386.deb)â&#8364;¦
S'estÃ* desempaquetant el reemplaÃ§ament de ubuntu-desktopâ&#8364;¦
S'estÃ* configurant ubuntu-desktop (1.307)â&#8364;¦



en la segona part no hi tinc rés:
code:> pere@pere-PC:~$ ls /var/crash
pere@pere-PC:~$ cd /var/
pere@pere-PC:/var/crash$ ls -l
total 0

---

### Post by wgarcia on 2014-03-12
Sí, es estrany, perquè que jo sàpiga la targeta gràfica que tens està suportada pel sistema gràfic d'Ubuntu i no hi hauria d'haver-hi problema. Pots provar la següent ordre a veure quina sortida et dóna?:

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by pserra on 2014-03-12
Hola wgarcia,
el que em retorna es aixo:
> pere@pere-PC:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system
pere@pere-PC:~$ 

que estrany...

---

### Post by wgarcia on 2014-03-13
És possible que quan vas instal·lar els controladors de NVIDIA t'ha configurat el sistema gràfic per usar aquests controladors, i com la teva targeta gràfica és Intel i no NVIDIA ara la gràfica no funciona. 

Doncs pots provar si desinstal·lant els controladors NVIDIA tornem a la normalitat, si no és així s'haurà de mirar si tens els controladors d'Intel isntal·lats, no sigui que la instal·lació dels NVIDIA els hagi remogut. Per tant prova

```
sudo apt-get remove --purge nvidia-current
```

a veure si hi ha sort.

---

### Post by wgarcia on 2014-03-13
Millor encara:

```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
```

---

### Post by pserra on 2014-03-13
Hola wgarcia
ara sembla que comencem a "resucitar" el Ubuntu
després de les comandes anteriors veig el fons de pantalla, però no veig cap barra ni lateral ni de dalt (no puc fer rés) apart de obrir terminal (Crlt+alt+t)
Hi ha un detall que no acaba d'anar: és el arxiu   libxatracker1
Perquè si faig un upgrade les darreres línias son:
> S'està preparant per a reemplaçar libxatracker1:i386 9.2.1-1ubuntu3 (emprant &#8230;/libxatracker1_10.1~git1402021930.81144c+curaga~gd~s_i386.deb)&#8230;
S'està desempaquetant el reemplaçament de libxatracker1:i386&#8230;
dpkg: s'ha produït un error en processar /var/cache/apt/archives/libxatracker1_10.1~git1402021930.81144c+curaga~gd~s_i386.deb (--unpack):
 s'està intentant sobreescriure «/usr/lib/i386-linux-gnu/libxatracker.so.2», que també està en el paquet libxatracker2:i386 10.2.0~git20140313.551d459a-0ubuntu0sarvatt~saucy
No s'ha escrit cap informe perquè ja s'ha superat MaxReports
                                                            S'han trobat errors en processar:
 /var/cache/apt/archives/libxatracker1_10.1~git1402021930.81144c+curaga~gd~s_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i si faig el que em vas dir el primer dia ( ls /var/crash),tenim:
> pere@pere-PC:~$ ls /var/crash
libxatracker1.0.crash  libxatracker1.0.upload  libxatracker1.0.uploaded

I si miro que em retorna el (/usr/lib/nux/unity_support_test -p)  ara retorna:
> pere@pere-PC:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 10.2.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Sembla que anem bé... l'unic  que no sé que carai em passa amb aquest pàquet:   libxatracker1

Gràcies

---

### Post by wgarcia on 2014-03-14
Prova a veure si traiem libxatracker1 si funciona, per tant ara les comandes serien:

```
sudo apt-get remove libxatracker1
sudo apt-get install --reinstall libxatracker2
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by pserra on 2014-03-14
Hola wgarcia...
ara quan faig els updates i upgrades..  ja no em surt cap error estrany..
he entrat com un altre usuari i l'escritori és el de sempre (amb les barres..)
Però des de el meu perfil veig el fons de pantalla... però no tinc cap mena de barra... si vull fer alguna cosa ha de ser a través terminal..
he provat de tornar a instal·lar el ubuntu desktop  i en principi no em surt cap error però no em canvia rés..
Potser hi ha alguna cosa a veure  que quan vaig passar-me al 14.10 no tenia accés a la /home... vaig arreglar-ho a través del nautilus..
Gracies

---

### Post by wgarcia on 2014-03-15
Entenc doncs que ara et funciona ja a l'usuari invitat però no al teu usuari normal. Això es pot arreglar segurament esborrant alguna carpeta de les que crea el sistema cada cop a la teva carpeta d'usuari, però abans de fer això el més fàcil és provar:

```
unity --reset
```

des del teu usuari.

---

### Post by pserra on 2014-03-15
hola wgarcia,
la comanda que m'has posat abans sembla que no acaba d'anar:
> pere@pere-PC:~$ unity --reset
ERROR: the reset option is now deprecated
pere@pere-PC:~$ sudo unity --reset
[sudo] password for pere: 
ERROR: the reset option is now deprecated

Si  executo nautilus ja veig totes les particions... però si vaig a home veig les carpetes dels usuaris + boot, +linux   però semblen les 2 buides...
Gràcies per l'ajud

---

### Post by wgarcia on 2014-03-16
Sí, perdona, en les últimes versions aquesta ordre ha canviat. Ara es fa amb una eina que es diu dconf-tools, així que primer s'ha de mirar si està instal·lada:

```
sudo apt-get install dconf-tools
```

Un cop verificat que està instal·lada s'ha de fer:

```
dconf reset -f /org/compiz/
setsid unity
unity --reset-icons
```

---

### Post by pserra on 2014-03-16
Hola wgarcia,
ja està solucionat.
Merci.

---

