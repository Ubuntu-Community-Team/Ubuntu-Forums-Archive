---
title: "Puc treballar mentre es fa l'actualització a la 9.10 Karmik Koala?"
date: 2009-10-31
forum: Catalan Team
---

### Post by jinglada on 2009-10-31
Puc treballar mentre es fa l'actualització?
------------------------------
He començat l'actualització i em diu:
S'han desactivat les fonts de tercers
S'han desactivat algunes entrades de tercers. Les podeu reactivar després de l'actualització des de l'eina «software-properties» en el vostre gestor de paquets.
------------------------------
S'ha deixat de donar suport a algunes aplicacions
Canonical Ltd. ja no mantindrà aquests paquets de manera oficial. Tot i això, com sempre, obtindreu l'ajuda de la comunitat.
Si no teniu activat el dipòsit «universe» se us suggerirà que els desinstal·leu en finalitzar l'actualització (em dona una llista d'unes 50 o 60 línies).
------------------------------
La baixada de fitxers serà de 3h54'. La baixada i actualització poden durar algunes hores i no es pot cancel·lar.
Voleu iniciar l'actualització?
-------------------------------
Li dic que si i segueixo treballant?

---

### Post by jinglada on 2009-10-31
Què és millor:

a) fer l'actualització des del Gestor d'actualitzacions?

o

b) descarregar la imatge .iso i instal·lar-la des de CD?

---

### Post by orestesmas on 2009-10-31
> **jinglada said:**
> Què és millor:


Una actualització et conserva totes les teves dades i programes instal·lats, mentre que una instal·lació de zero no et conservarà els programes instal·lats (et deixarà la tria per defecte), i hauràs d'anar amb molt de compte per tal d'evitar que t'esborri les teves dades personals.

A partir d'aquí, tu esculls.

---

### Post by orestesmas on 2009-10-31
> **jinglada said:**
> Puc treballar mentre es fa l'actualització?
-------------------------------
Li dic que si i segueixo treballant?

Si que es pot seguir treballant, tot i que has d'estar preparat perquè un programa peti. És normal quan en un programa li actualitzaen les llibreries en què es basa mentre s'està executant...

---

### Post by jinglada on 2009-11-01
> **orestesmas said:**
> Una actualització et conserva totes les teves dades i programes instal·lats, mentre que una instal·lació de zero no et conservarà els programes instal·lats (et deixarà la tria per defecte), i hauràs d'anar amb molt de compte per tal d'evitar que t'esborri les teves dades personals.

Gràcies, Orestes. Faré **l'actualització**. De tota manera, quan diu: 

"S'ha deixat de donar suport a algunes aplicacions 
Canonical Ltd. ja no mantindrà aquests paquets de manera oficial. Tot i això, com sempre, obtindreu l'ajuda de la comunitat.
Si no teniu activat el dipòsit «universe» se us suggerirà que els desinstal·leu en finalitzar l'actualització
acl
binutils-static
bluez-gnome
contact-lookup-applet
cpp-4.3
cupsddk
epiphany-browser
epiphany-browser-data
epiphany-extensions
epiphany-gecko
g++-4.3
gcc-4.3
gcc-4.3-base
gcj-4.3-base
gnome-mount
gnome-user-guide-ca
gnome-user-guide-en
gnome-user-guide-eo
gnome-user-guide-es
gstreamer0.10-gnomevfs
hotkey-setup
human-icon-theme
indi
klogd
libgcj9-0
libgcj9-jar
libglew1.5
libgnome-speech7
libgnomevfs2-bin
libmono-data1.0-cil
libmono-data2.0-cil
libmono-getoptions1.0-cil
libmono-posix1.0-cil
libmysqlclient15off
libpolkit-gnome0
libsmbios2
libstdc++6-4.3-dev
nvidia-180-modaliases
phonon
phonon-backend-gstreamer
pidgin-otr
policykit-gnome
python-gdata
python-launchpad-bugs
python-usb
qt4-qtconfig
rss-glx
sysklogd
tangerine-icon-theme
ttf-kochi-gothic
ttf-sazanami-gothic
ubuntu-gdm-themes
w3c-dtd-xhtml
xulrunner-1.9
xulrunner-1.9-gnome-support"

què vol dir? què el dipòsit «**universe**»?

Jo faig servir l'epiphany, de tant en tant el python, però sobretot em preocupa això que diu de la **nvidia**-180-modaliases, pel que he llegit d'alguns problemes.

Què he de fer?

---

### Post by orestesmas on 2009-11-01
Podem classificar els programes continguts a l'ubuntu de dues maneres: Segons si són o no programari lliure i segons si els suporta o no Canonical de manera oficial.

Això ens dóna 4 combinacions possibles, i Canonical col·loca cadascuna d'aquestes categories en un magatzem apart. Aquests magatzems tenen el nom de "main", "restricted", "universe" i "multiverse" (aquest darrer nom té el seu orígen en la mecànica quàntica, però no hi té res a veure, clar).

```

           |  lliure               privatiu
-----------|--------------------------------
oficial    |   MAIN               RESTRICTED
           |
no oficial | UNIVERSE             MULTIVERSE

```

Per tant el repositori universe conté els programes que provenen directament de Debian (la distribució "mare" d'Ubuntu), però dels quals l'empresa Canonical no es responsabilitza de mantenir (es refien de Debian).

En general com a usuaris d'entorns d'escriptori voldrem tenir activat el repositori universe, perquè ens dóna accés a milers de programes que funcionen perfectament sota ubuntu, encara que canonical no els consideri essencials per al funcionament del sistema. Aquí hi poden haver jocs, utilitats diverses, etc.

L'única cosa que et diu aquest missatge és que canonical ha decidit deixar de donar suport a alguns programes lliures (desapareixen de main), i que passa a refiar-se del suport de Debian (els traspassa a universe). Per tant és normal que els desinstal·li si tu no tens activat el repositori universe.

Els diferents repositoris s'activen i es desactiven des del synaptic.

---

### Post by jinglada on 2009-11-01
> **orestesmas said:**
> Per tant és normal que els desinstal·li si tu no tens activat el repositori universe.

Els diferents repositoris s'activen i es desactiven des del synaptic.

Gràcies novament. He anat al synaptic. He clicat a 'origen' i he vist que tots els esmentats són al 'ad.archive.ubuntu.com/main'. 

En el mateix 'menú' també hi ha 'ad.archive.ubuntu.com/universe', 'ad.archive.ubuntu.com/multiverse', 'ad.archive.ubuntu.com/restricted', 'Local/main', 'Local/multiverse', 'ppa.launchpad.net/main' i 'ppa.launchpad.net/universe'

Això vol dir que tinc el repositori universe activat?

---

