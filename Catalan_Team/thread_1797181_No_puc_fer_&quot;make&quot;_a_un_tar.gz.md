---
title: "No puc fer &quot;make&quot; a un tar.gz"
date: 2011-07-04
forum: Catalan Team
---

### Post by xanxu on 2011-07-04
Bones a tothom,

Tinc un problema a l'hora d'instal·lar un .tar.gz
Anoto el que em diu la terminal i després especifico.

guillem@guillem-Aspire-5810T ~ $ cd Descargas
guillem@guillem-Aspire-5810T ~/Descargas $ cd covergloobus-1.6
guillem@guillem-Aspire-5810T ~/Descargas/covergloobus-1.6 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
configure: error: cannot run /bin/bash ./config.sub
guillem@guillem-Aspire-5810T ~/Descargas/covergloobus-1.6 $ make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
guillem@guillem-Aspire-5810T ~/Descargas/covergloobus-1.6 $

l'arxiu descargat és un tar-gz que ja he descomprimit prèviament a través de la terminal. faig cd a la carpeta creada i segueixo els passos ./configure, make, make install però després de ./configure no em deixa seguir. Hi ha un arxiu INSTALL que em diu que ho haig de fer així. Quin pot ser el problema?

L'arxiu és d'aquesta pàgina: [http://launchpad.net/covergloobus/1.6/1.6stable/+download/covergloobus_1.6.tar.gz](http://launchpad.net/covergloobus/1.6/1.6stable/+download/covergloobus_1.6.tar.gz)

Gràcies!

---

### Post by xanxu on 2011-07-04
He seguit les instruccions de [http://ubuntulife.wordpress.com/2010/02/26/covergloobus-caratula-y-letras-de-tus-canciones-en-el-escritorio/](http://ubuntulife.wordpress.com/2010/02/26/covergloobus-caratula-y-letras-de-tus-canciones-en-el-escritorio/) descargant-me l'arxiu que te alla en un link i sembla que funciona, amb el pas previ de ./autogen.sh
De totes maneres, què és això de autogen? no sempre s'ha de fer veritat?

---

### Post by wgarcia on 2011-07-05
"autogen.sh", "configure.sh" i altres són "scripts" inicials que configuren el paquet per a la plataforma especifica on s'estigui compilant el paquet. Aquests són paquets multiplataforma i en aquests "scripts" els desenvolupadors posen instruccions perquè el paquet es configure per a la plataforma específica on s'estigui compilant.

---

### Post by xanxu on 2011-07-05
Així quan descomprimeixo un tar.gx, si veig qualsevol d'aquests arxius els hauré de correr a la terminal abans que el ./configure?

Per altra banda, i sento si marxo del tema, és molt difícil construir paquets .deb a partir de paquets .tar.gz? Si fos fàcil m'animaria a crear una plataforma o quelcom semblant on tots aquests arxius que necessiten corres per terminal es poguessin obrir amb un doble click, com els .exe. Ho dic ja que conec moltíssima gent que no s'anima al canvi per culpa d'aquests paquets, i si tot fos tant fàcil com un doble click...

---

### Post by wgarcia on 2011-07-05
Normalment hi ha un fitxer tipus README o INSTALL que explica com configurar i compilar un paquet. 

Muntar un deb no és tasca impossible però sí una mica complicada. S'han de respectar molts requisits perquè el paquet pugui ser inclòs en els dipòsits Debian i els seus derivats (Ubuntu, etc.). Normalment tots els paquets més habituals tenen un "mantenidor/a" que munta el paquet debian corresponent. Si vols iniciar un paquet hauries de buscar "tutorials" que t'expliquin com muntar un paquet debian.

---

