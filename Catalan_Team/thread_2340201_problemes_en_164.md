---
title: "problemes en 16/4"
date: 2016-10-16
forum: Catalan Team
---

### Post by jesús sol on 2016-10-16
Vaig actualitzar Ubuntu 14/4 a 16/4LTS. Dona missatge " S'ha produït unproblema mentre s' instal·lava el programa. Paquet: Keyboard-configuration  1.108 ubuntu 15.2». Ara l'ordinador funciona amb irregularitats. De tant en tant diu "ubuntu ha experimentat un error intern". Les  actualitzacions. diuen que falla un paquet cada vegada. 
Potser reinstal·lar  16/4? Gràcies!

---

### Post by jmaspons on 2016-10-17
Aquest missatge te'l dona quan intentes actualitzar el sistema?

prova la següent comanda que intenta configurar els paquets que s'hagin quedat a mig instal·lar

```
sudo dpkg --configure -a
```

---

### Post by wgarcia on 2016-10-17
Una altra comanda per completar una instal·lació inacabada és:

```
sudo apt-get dist-upgrade
```

però compte, s'ha de llegir el que fa, perquè si hi ha problemes de dependències no satisfetes pot voler desinstal·lar components importants, si veus que proposa desinstal·lar coses aborta la comanda.

---

### Post by jesús sol on 2016-10-18
Gràcies per la rapidesa!
He executat la comanda -configure i m'ha sortit una tirallonga llarguíssima de dependències insatisfetes (que no goso copiar per l'extensió) entenc que no ha fet res ja que diu que es deixen sense configurar.
Després he executat sudo apt-get dist-upgrade i ha respost el següent:
jesus@jesus-Dell:~$ sudo apt-get dist-upgrade
S'està llegint la llista de paquets&#8230; Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
S'està calculant l'actualització&#8230; Fet
Els paquets següents s'han insta&#320;lat automàticament i ja no són necessaris:
  checkbox-ng cups-browsed cups-core-drivers cups-daemon
  cups-filters-core-drivers cups-server-common fonts-linuxlibertine
  gcc-4.9-base gstreamer1.0-clutter libamd2.3.1 libapt-inst1.5
  libarchive-extract-perl libass4 libavcodec54 libavformat54
  libbasicusageenvironment0 libbind9-90 libbit-vector-perl
  libboost-date-time1.54.0 libboost-system1.54.0 libcamd2.3.1 libcamel-1.2-45
  libcarp-clan-perl libccolamd2.8.0 libcdr-0.0-0 libcholmod2.1.2 libclamav6
  libcmis-0.4-4 libcolamd2.8.0 libcolorhug1 libdate-calc-perl
  libdate-calc-xs-perl libdirac-encoder0 libdns100 libdvbpsi8
  libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0
  libedata-book-1.2-20 libedataserver-1.2-18 libegl1-mesa-drivers libelfg0
  libenca0 libestools2.1 libexiv2-12 libfontembed1 libfriends0 libgegl-0.2-0
  libglamor0 libglew1.10 libglewmx1.10 libgnome-bluetooth11
  libgnome-desktop-3-7 libgphoto2-port10 libgroupsock1 libicu52 libilmbase6
  libimobiledevice4 libisc95 libisccc90 libisccfg90 libisl10
  libjavascriptcoregtk-1.0-0 liblinear1 liblivemedia23 libllvm3.4
  liblog-message-perl liblog-message-simple-perl liblouisutdml-bin
  liblouisutdml-data liblouisutdml6 liblwres90 libmagickcore5
  libmagickcore5-extra libmagickwand5 libmbim-glib0 libmodule-pluggable-perl
  libmodule-runtime-perl libmspub-0.0-0 libnetpbm10 libntdb1 libopenexr6
  libopenjpeg2 libopenvg1-mesa liborcus-0.6-0 libparams-classify-perl
  libpocketsphinx1 libpod-latex-perl libpoppler44 libprocps3 libprotobuf8
  libprotoc8 libqmi-glib0 libqpdf13 libqpdf17 libqt5qml-graphicaleffects
  libqt5sensors5 libqt5webkit5-qmlwebkitplugin libraw9 libreadline5
  librhythmbox-core8 libsphinxbase1 libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libtar0 libterm-ui-perl libtext-soundex-perl
  libthumbnailer0 libts-0.0-0 libumfpack5.6.2 libunityvoice1 libupstart1
  libusageenvironment1 libusbmuxd2 libvisio-0.0-0 libvpx1 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libx264-142 libxtables10 linux-generic
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-headers-3.13.0-45 linux-headers-3.13.0-45-generic
  linux-headers-3.13.0-61 linux-headers-3.13.0-61-generic
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-generic
  linux-image-3.13.0-39-generic linux-image-3.13.0-45-generic
  linux-image-3.13.0-61-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-extra-3.13.0-39-generic
  linux-image-extra-3.13.0-45-generic linux-image-extra-3.13.0-61-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-generic netpbm printer-driver-foo2zjs-common
  python-commandnotfound python-ntdb python3-checkbox python3-pexpect
  python3-pil python3-ptyprocess python3-renderpm python3-reportlab
  python3-reportlab-accel qml-module-qtquick-dialogs
  qml-module-qtquick-localstorage qml-module-qtquick-privatewidgets
  qml-module-ubuntu-ui-extras-browser qpdf qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-window-plugin sphinx-voxforge-hmm-en sphinx-voxforge-lm-en
  tcl thermald tk tsconf unity-lens-friends unity-scope-audacious
  unity-scope-clementine unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-musique unity-voice-service
Empreu «sudo apt autoremove» per a suprimir-los.
S'actualitzaran els paquets següents:
  gnome-software gnome-software-common libpam-systemd libsystemd0 libudev1
  python3-update-manager systemd systemd-sysv ubuntu-software udev
  update-manager update-manager-core xserver-common xserver-xorg-core
  xserver-xorg-legacy
15 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
36 no insta&#320;lats o suprimits completament.
S'ha d'obtenir 9704 kB d'arxius.
Després d'aquesta operació s'empraran 78,8 kB d'espai en disc addicional.
Voleu continuar? [S/n] 

I ara no sé què respondre...
Agraït

---

### Post by wgarcia on 2016-10-18
Pots dir que sí, si revises la llista de coses que farà, veus que no vol desinstal·lar res. Un cop que acabi per acabar l'actualització, fes

```
sudo apt-get autoremove
```

Això eliminarà tots els paquets antics que han quedat obsolets amb l'actualització.

Després faria 

```
sudo apt-get update
```

i a countinuació 
```
sudo apt-get upgrade
```

Si et diu que no hi ha res a instal·lar, sembla que s'haurà completat l'actualització a la nova versió.

---

### Post by jesús sol on 2016-10-18
He fet tot el que m'heu dit. En l'autoremove, ha desinstal·lat la tira de coses. Al final de tot ha quedat aquest missatge:    	 	 	 	   E: Sub-process /usr/bin/dpkg returned an error code (1)
He reiniciat i sembla que va bé. Ja us diré si és així amb el temps. 
Mil gràcies wgarcia i jmaspons. Encantat de ser part de la comunitat ubuntaire.

---

### Post by wgarcia on 2016-10-19
Jo ara tornaria a fer aquestes ordres:

```

sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get upgrade

```

a veure si ha quedat alguna cosa per configurar/instal·lar.

---

### Post by jesús sol on 2016-10-19
La cosa no xuta, Walter. La màquina no acaba d'anar bé. He tornat a fer aquestes ordres i segueix donant errors.
Enganxo un tros de la resposta del terminal:
  	 	 	 	   jesus@jesus-Dell:~$ sudo dpkg --configure -a
 S'està configurant keyboard-configuration (1.108ubuntu15.2)&#8230;
 Error loading new keyboard description
 /usr/bin/ckbcomp: Can not find file "symbols/ad" in any known directory
 dpkg: s'ha produït un error en processar el paquet keyboard-configuration (--configure):
  el subprocés s'ha instal·lat el script post-installation retornà el codi d'eixida d'error 1
 dpkg: problemes de dependències impedeixen la configuració de xserver-xorg-core:
  xserver-xorg-core depèn de keyboard-configuration; tot i així:
   El paquet keyboard-configuration encara no està configurat.
 
 
 dpkg: s'ha produït un error en processar el paquet xserver-xorg-core (--configure):
  problemes de dependències - es deixa sense configurar
 dpkg: problemes de dependències impedeixen la configuració de xserver-xorg-video-radeon:
  xserver-xorg-video-radeon depèn de xorg-video-abi-20; tot i així:
   El paquet xorg-video-abi-20 no està instal·lat.
   El paquet xserver-xorg-core que proveeix xorg-video-abi-20 no està configurat.
  xserver-xorg-video-radeon depèn de xserver-xorg-core (>= 2:1.17.99.902); tot i així:
   El paquet xserver-xorg-core encara no està configurat.
 
 
 dpkg: s'ha produït un error en processar el paquet xserver-xorg-video-radeon (--configure):
  problemes de dependències - es deixa sense configurar
 dpkg: problemes de dependències impedeixen la configuració de xserver-xorg:
  xserver-xorg depèn de xserver-xorg-core (>= 2:1.17.2-2); tot i així:
   El paquet xserver-xorg-core encara no està configurat.

Ah! la màquina és DELL Vostro 3560

---

### Post by wgarcia on 2016-10-20
Sembla que el paquet keyboard-configuration no està ben instal·lat. Primer es pot provar de reinstal·lar-lo:

```
sudo apt-get install --reinstall keyboard-configuration
```

---

### Post by jesús sol on 2016-10-20
Poso l'ordre de reinstal.lar i el terminal diu això:
jesus@jesus-Dell:~$ sudo apt-get install --reinstall keyboard-configuration
[sudo] contrasenya per a jesus: 
S'està llegint la llista de paquets&#8230; Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
0 actualitzats, 0 nous a insta&#320;lar, 1 reinsta&#320;lats, 0 a suprimir i 0 no actualitzats.
36 no insta&#320;lats o suprimits completament.
Després d'aquesta operació s'empraran 0 B d'espai en disc addicional.
E: Internal Error, No file name for keyboard-configuration:i386
jesus@jesus-Dell:~$ 

M'he  adonat que hi ha instal·lat Ubuntu 16.04.1 LTS 32-bit. Crec recordar  que en instal·lar el 14.04 LTS, vam posar el de 32 bit, tot i que el  processador és un Intel I5, crec que perquè no anava bé la tarja  gràfica.
Pot ser que haguem de posar el 16.04 de 64 bits?
D'altra  banda, dir-vos que em sap greu atabalar-vos tant amb el meu problema. Si  tinc salut, el proper 5 de novembre vull pujar a Ripoll a la festa del  16.10. Potser fora prudent esperar a veuren's i a més de tenir el plaer  de saludar-vos em podeu donar un copet de mà, sense més molèsties...

---

### Post by wgarcia on 2016-10-21
Podem continuar per aquí, i si encara no ens hem sortit, a Ripoll ho podem rematar. Per veure exactament si tens 32 o 64 bits, l'ordre és:

```
uname -a
```

Si es veu "i386" és 32 bits, si es veu "x86_64" és 64 bits.

---

### Post by jesús sol on 2016-10-24
Ooops! no havia vist que continuava a una altra pàgina...
amb uname -a diu:
jesus@jesus-Dell:~$ uname -a
Linux jesus-Dell 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:50:36 UTC 2016 i686 i686 i686 GNU/Linux
jesus@jesus-Dell:~$ 
??
Però a Parametres / Detalls diu: Sistema base: Ubuntu 16.04.1 LTS 32-bit

---

### Post by wgarcia on 2016-10-25
Bé, està clar que tens instal·lat el sistema de 32 bits.

A veure si reinstallant el paquest keyboard configuration s'arregla:

```

sudo apt-get remove keyboard-configuration
sudo apt-get install keyboard-configuration
sudo apt-get update && sudo apt-get upgrade

```

i a creuar els dits...

---

### Post by jesús sol on 2016-10-25
No sembla tenir massa bona pinta...
Diu:
  	 	 	 	   S'està desempaquetant keyboard-configuration (1.108ubuntu15.2)&#8230;
 S'estan processant els activadors per a systemd (229-4ubuntu11)&#8230;
 S'estan processant els activadors per a ureadahead (0.100.0-19)&#8230;
 ureadahead will be reprofiled on next reboot
 S'estan processant els activadors per a man-db (2.7.5-1)&#8230;
 S'està configurant keyboard-configuration (1.108ubuntu15.2)&#8230;
 Error loading new keyboard description
 update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
 update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
 update-initramfs: deferring update (trigger activated)
 S'estan processant els activadors per a initramfs-tools (0.122ubuntu8.5)&#8230;
 update-initramfs: Generating /boot/initrd.img-4.4.0-43-generic
 jesus@jesus-Dell:~$  
i després:
jesus@jesus-Dell:~$ sudo apt-get update && sudo apt-get upgrade
Obj:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Obj:2 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial InRelease              
Obj:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease              
Bai:4 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95,7 kB]
Obj:5 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-backports InRelease
S'ha baixat 95,7 kB en 0s (112 kB/s)                            
S'està llegint la llista de paquets&#8230; Fet
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
S'està calculant l'actualització&#8230; Fet
Els paquets següents s'han insta&#320;lat automàticament i ja no són necessaris:
  libxatracker2 xserver-xorg-legacy
Empreu «sudo apt autoremove» per a suprimir-los.
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.

Mil gràcies per tot.

---

### Post by wgarcia on 2016-10-25
Ara 

```
sudo apt-get autoremove
```

i després un altre cop 

```
sudo apt-get update && sudo apt-get upgrade
```

però ja es veu força bé a les ordres anteriors.

---

### Post by jesús sol on 2016-10-25
:( Ja ho he fet tot. Semblava que tot havia anat bé. Ha dit al final:
  	 	 	 	   S'està configurant multiarch-support (2.23-0ubuntu4)&#8230;
 S'està configurant libc-dev-bin (2.23-0ubuntu4)&#8230;
 S'està configurant libc6-dev:i386 (2.23-0ubuntu4)&#8230;
 S'està configurant libc6-dbg:i386 (2.23-0ubuntu4)&#8230;
 S'està configurant locales (2.23-0ubuntu4)&#8230;
 Generating locales (this might take a while)...
   ca_AD.UTF-8... done
   ca_ES.UTF-8... done
   ca_ES.UTF-8@valencia... done
   ca_FR.UTF-8... done
   ca_IT.UTF-8... done
   en_AG.UTF-8... done
   en_AU.UTF-8... done
   en_BW.UTF-8... done
   en_CA.UTF-8... done
   en_DK.UTF-8... done
   en_GB.UTF-8... done
   en_HK.UTF-8... done
   en_IE.UTF-8... done
   en_IN.UTF-8... done
   en_NG.UTF-8... done
   en_NZ.UTF-8... done
   en_PH.UTF-8... done
   en_SG.UTF-8... done
   en_US.UTF-8... done
   en_ZA.UTF-8... done
   en_ZM.UTF-8... done
   en_ZW.UTF-8... done
 Generation complete.
Després ha dit que calia reiniciar. Ho he fet. I ara no s'engega. Surt la pantalla on s'escull com engega i es queda aturat.
He engegat amb un Ubuntu 12.04 que hi havia al final de la llista i amb ell us escric.:cry:

---

### Post by wgarcia on 2016-10-26
A la pantalla d'engegar (grub) tens l'opció "Opcions avançades" o quelcom així? Mira si tens aquí altres nuclis per provar d'engegar. En cas que no tinguis, segurament tindràs una opció d'iniciar en mode de recuperació, prova també si pots engegar amb aquest mode.

---

### Post by jesús sol on 2016-10-26
:confused: He provat d'engegar amb 'opcions avançades' En mode recuperació s'arriba a una pantalla on es pot triar diverses accions. Però en cap s'engega. Al final acaben en una pantalla on hi ha tot de coses que ha fet i on destaca en vermell un parell que diuen: Failed To start set console keymap, i Failed to start set console font and keymap.
I d'aquí no passa.

---

### Post by wgarcia on 2016-10-27
Vaja, sembla que la configuració del teclat continua donant problemes. A veure si tornant-la a configurar almenys et deixa entrar. Des d'aquesta pantalla que dius en mode recuperació prova:

```
sudo dpkg-reconfigure keyboard-configuration
```

---

### Post by jesús sol on 2016-11-10
Solventat a Ripoll. Substituït tot per Ubuntu 16.04 64 bit. Perfecte.
Moltes gràcies, wgarcia.

---

