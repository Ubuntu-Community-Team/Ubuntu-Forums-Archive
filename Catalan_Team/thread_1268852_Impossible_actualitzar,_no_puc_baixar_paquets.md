---
title: "Impossible actualitzar, no puc baixar paquets"
date: 2009-09-17
forum: Catalan Team
---

### Post by xavix2005 on 2009-09-17
No aconsegueixo actualitzar, em surten missatges del tipus:

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb)
  No s'ha pogut connectar amb archive.ubuntu.com:80 (91.189.88.140), temps de connexió excedit [IP: 91.189.88.140 80]


W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb)
  No es pot connectar amb archive.ubuntu.com http: [IP: 91.189.88.140 80]




Agraïré qualsevol ajuda, sóc novell en això de l'Ubuntu i no me'n surto!

---

### Post by papapep on 2009-09-17
Això indica que per alguna raó no es pot connectar amb el servidor del dipòsit de programari al que intentes connectar.

Si la xarxa et funciona correctament per navegar i demés coses, hauries de provar a modificar la configuració de les fonts de programari a Sistema > Administració > Gestor de paquets Synaptic, i si vas a Paràmetres > Dipòsit tria un altre servidor on diu "Baixa de". Tria'n un qualsevol, mentre sigui diferent del que tens ara.
Després tornes a provar el que dius que abans no et funcionava.

Salut.

---

### Post by xavix2005 on 2009-09-17
Agraeixo la resposta, però ho intento i no me'n surto. Sembla ser algun problema de connexió, potser he de canviar algun paràmetre, pot tenir a veure amb la meva connexió no permeti els intercanvis P2P? L'error és ara: 

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty/Release.gpg](http://ftp.udc.es/ubuntu/dists/jaunty/Release.gpg)  No s'ha pogut connectar amb ftp.udc.es:80 (193.144.48.41), temps de connexió excedit

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty/main/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty/main/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty/restricted/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty/restricted/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty/universe/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty/universe/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty/multiverse/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty/multiverse/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-updates/Release.gpg](http://ftp.udc.es/ubuntu/dists/jaunty-updates/Release.gpg)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-updates/main/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-updates/main/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-updates/universe/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-updates/universe/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  No s'ha pogut connectar amb archive.canonical.com:80 (91.189.90.142), temps de connexió excedit

W: No s'ha pogut obtenir [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-ca.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-ca.bz2)  No es pot connectar amb archive.canonical.com http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-security/Release.gpg](http://ftp.udc.es/ubuntu/dists/jaunty-security/Release.gpg)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-security/main/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-security/main/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-security/restricted/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-security/restricted/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-security/universe/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-security/universe/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ftp.udc.es/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-ca.bz2](http://ftp.udc.es/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-ca.bz2)  No es pot connectar amb ftp.udc.es http:

W: No s'ha pogut obtenir [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/Release.gpg](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/Release.gpg)  No s'ha pogut connectar amb ppa.launchpad.net:80 (91.189.90.217), temps de connexió excedit

W: No s'ha pogut obtenir [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/main/i18n/Translation-ca.bz2](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/main/i18n/Translation-ca.bz2)  No es pot connectar amb ppa.launchpad.net http:

W: No es poden baixar alguns fitxers índex, s'han ignorat o en el seu lloc s'han emprat els antics.

---

### Post by papapep on 2009-09-17
Però amb aquest ordinador amb el qual tens problemes, pots navegar, pots enviar i rebre correu, funciona correctament la xarxa per la resta de coses? estàs darrera algun proxy o tallafocs? és una xarxa casolana, o és algun lloc empresarial o educatiu? Tens el tallafocs activat a l'Ubuntu? la connexió de xarxa és per cable, o inalàmbrica? anava bé abans? si és que sí, des de quan falla? recordes si has instal·lat/desinstal·lat o modificat alguna cosa que pugui afectar això?

Dóna alguna pista, si us plau...

---

### Post by papapep on 2009-09-20
xavix2005: he mogut els dos últims apunts a un nou fil.

Hauries de fer una bona ullada a les normes de funcionament bàsic del fòrum, a fi d'intentar operar tots d'una manera una mica homogènia: 

[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

Per què t'ho dic això?

1. Per que una de les normes d'or del fòrum és "un tema, un fil". Si canvia el tema, cal obrir-ne un de nou per a no barrejar coses dins un fil i facilitar que la teva experiència pugui servir a d'altres posteriorment, sense haver de repetir eternament totes les preguntes un i altre copl
2. Tornes a plantejar preguntes sense explicar-nos res de res del teu ordinador. I podem saber, o no, de Gnu/Linux, però el do de l'adivinació encara no ens ha arribat :D

Quina mida té el teu/s disc/s dur/s? quantes particions hi tens, i com estan definides?

Respon a [aquest fil]("http://ubuntuforums.org/showthread.php?t=1271091") , si us plau

---

