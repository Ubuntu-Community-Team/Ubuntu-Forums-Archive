---
title: "(DEBIAN) dpkg error code 1"
date: 2008-12-31
forum: Catalan Team
---

### Post by marteljorge on 2008-12-31
quan faig ```
sudo apt-get -f remove kdebluetooth
```, no entenc l'error que obtenc:
```
(Leyendo la base de datos ...
103886 ficheros y directorios instalados actualmente.)
Desinstalando kdebluetooth ...
dpkg-divert: diferencia al desviar
  cuando se eliminaba `diversion of /usr/bin/kdesktop_lock to /usr/bin/kdesktop_lock_nobt by kdebluetooth'
  se encontró `diversion of /usr/bin/kdesktop_lock to /usr/bin/kdesktop_lock.orig by kdelock-knoppix'
dpkg: error al procesar kdebluetooth (--remove):
 el subproceso post-removal script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 kdebluetooth
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by papapep on 2008-12-31
Fes un:

```
sudo dpkg --configure -a
```

a veure si t'ho arregla.

---

### Post by CarlesOriol on 2009-01-01
kdelock-**knoppix**

Tens algun repositori que s'està barallant amb els d'ubuntu?

---

### Post by marteljorge on 2009-01-01
> **papapep said:**
> Fes un:

```
sudo dpkg --configure -a
```

```
udo dpkg --configure -a
dpkg: problemas de dependencias impiden la configuración de firefox-3.0:
 firefox-3.0 depende de libnspr4-0d (>= 1.8.0.10); sin embargo:
  La versión de `libnspr4-0d' en el sistema es 1.8.0.8-1.
 firefox-3.0 depende de xulrunner-1.9 (>= 1.9.0.1); sin embargo:
  El paquete `xulrunner-1.9' no está instalado.
dpkg: error al procesar firefox-3.0 (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 firefox-3.0
```

---

### Post by papapep on 2009-01-01
Enganxa el contingut de /etc/apt/sources.list.

---

### Post by marteljorge on 2009-01-01
> **CarlesOriol said:**
> kdelock-**knoppix**

Tens algun repositori que s'està barallant amb els d'ubuntu?

Potser [http://ftp.de.debian.org?](http://ftp.de.debian.org?)

---

### Post by marteljorge on 2009-01-01
# Security updates for "stable"
deb [http://security.debian.org/](http://security.debian.org/) stable/updates main contrib non-free  
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib non-free 

# Stable
deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) stable main contrib non-free  

# the non-US branch doesn't exist anymore since sarge. -KK
# deb [http://ftp.es.debian.org/pub/debian-non-US/](http://ftp.es.debian.org/pub/debian-non-US/) stable/non-US main contrib non-free   

# Stable Sources
deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) stable main contrib non-free  

# Testing
deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) testing main contrib non-free  
deb [http://ftp.de.debian.org/pub/debian](http://ftp.de.debian.org/pub/debian) testing contrib non-free   

# Testing Sources
deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) testing main contrib non-free   
deb-src [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) testing main contrib non-free  

# Unstable
deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) unstable main contrib non-free 
# deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) unstable main contrib non-free 

# Unstable Sources
deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) unstable main contrib non-free 
# deb-src [http://ftp.de.debian.org/debian-non-US/](http://ftp.de.debian.org/debian-non-US/) unstable/non-US main contrib non-free 

# Experimental
deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) experimental main contrib non-free 

# Experimental Sources
# deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) ../project/experimental main contrib non-free 

# ndiswrapper source (disappeared, only source.tar available)
# deb [http://ndiswrapper.sourceforge.net/debian/](http://ndiswrapper.sourceforge.net/debian/) ./ 

# KDE 3.5 (not in sarge)
# deb [http://pkg-kde.alioth.debian.org/kde-3.5.0/](http://pkg-kde.alioth.debian.org/kde-3.5.0/) ./ 
# deb-src [http://pkg-kde.alioth.debian.org/kde-3.5.0/](http://pkg-kde.alioth.debian.org/kde-3.5.0/) ./ 
# deb [http://pkg-kde.alioth.debian.org/kde-3.4.1/](http://pkg-kde.alioth.debian.org/kde-3.4.1/) ./ 
# deb-src [http://pkg-kde.alioth.debian.org/kde-3.4.1/](http://pkg-kde.alioth.debian.org/kde-3.4.1/) ./ 

# Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
# deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 

# Unichrome graphics driver
# deb [http://www.physik.fu-berlin.de/~glaweh/debian/](http://www.physik.fu-berlin.de/~glaweh/debian/) unichrome/ 
# deb-src [http://www.physik.fu-berlin.de/~glaweh/debian/](http://www.physik.fu-berlin.de/~glaweh/debian/) unichrome/ 

# NX stuff
# deb [http://www.kalyxo.org/debian/](http://www.kalyxo.org/debian/) experimental main 
# deb [http://www.kalyxo.org/debian/](http://www.kalyxo.org/debian/) unstable main 

# ndiswrapper
# deb [http://rigtorp.se/debian/](http://rigtorp.se/debian/) unstable/ 
# deb-src [http://rigtorp.se/debian/](http://rigtorp.se/debian/) unstable/ 

# Blades Repository (pppoeconf & co)
# deb [http://people.debian.org/~blade/testing/](http://people.debian.org/~blade/testing/) ./ 
# deb-src [http://people.debian.org/~blade/testing/](http://people.debian.org/~blade/testing/) ./ 

# deb cdrom:[Debian GNU/Linux 2.2 r3 _Potato_ - Official i386 Binary-1 (20010427)]/ unstable contrib main non-US/contrib non-US/main 

# Knoppix special packages resource at LinuxTag HQ
# deb [http://developer.linuxtag.net/knoppix/](http://developer.linuxtag.net/knoppix/) ./ 
# deb-src [http://developer.linuxtag.net/knoppix/](http://developer.linuxtag.net/knoppix/) ./ 

# deb [http://snapshot.debian.net/archive/](http://snapshot.debian.net/archive/) pool gcc 
# deb-src [http://snapshot.debian.net/archive/](http://snapshot.debian.net/archive/) pool gcc 

# From the Kanotix archives
# deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./ 
# deb-src [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./ 

# NX Server
# deb [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) sid nx 
# deb-src [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) sid nx 

# NX Client (binary-only, non-free)
# deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) sid main contrib non-free 

# Packages from ubuntu. CAUTION, they don't mix well with Debian
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hoary main universe multiverse 
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hoary main universe multiverse 

# Unofficial packages, like JAVA
# deb [ftp://ftp.debian-unofficial.org/debian/](ftp://ftp.debian-unofficial.org/debian/) stable main contrib non-free restricted 
# deb-src [ftp://ftp.debian-unofficial.org/debian/](ftp://ftp.debian-unofficial.org/debian/) stable main contrib non-free restricted 
# deb [ftp://ftp.debian-unofficial.org/debian/](ftp://ftp.debian-unofficial.org/debian/) testing main contrib non-free restricted 
# deb-src [ftp://ftp.debian-unofficial.org/debian/](ftp://ftp.debian-unofficial.org/debian/) testing main contrib non-free restricted 
# deb [ftp://ftp.debian-unofficial.org/debian/](ftp://ftp.debian-unofficial.org/debian/) unstable main contrib non-free restricted 
# deb-src [ftp://ftp.debian-unofficial.org/debian/](ftp://ftp.debian-unofficial.org/debian/) unstable main contrib non-free restricted 

# Open-Xchange and JavaMail packages
# deb [http://ox.cs.bme.hu/ox-stable/](http://ox.cs.bme.hu/ox-stable/) sarge contrib 

# Open-Xchange development version (currently 0.8.1.2-1) and JavaMail packages
# deb [http://ox.cs.bme.hu/ox-devel/](http://ox.cs.bme.hu/ox-devel/) sarge contrib 

# Various Projects

# Thunderbird
#deb [http://people.debian.org/~asac/experimental/](http://people.debian.org/~asac/experimental/) ./ 
#deb-src [http://people.debian.org/~asac/experimental/](http://people.debian.org/~asac/experimental/) ./ 

# Beryl/Compiz from Ubuntu
# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main 
# deb-src [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main 

# imu's Beryl-SVN Debian-unstable Repository
# GPG key: 81836EBF
deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) debian-unstable beryl-svn 
deb-src [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) debian-unstable beryl-svn 

# NX
#deb [http://sidux.com/debian/](http://sidux.com/debian/) sid nx 
#deb-src [http://sidux.com/debian/](http://sidux.com/debian/) sid nx 

# whereto - automatic detection of country/language
# [http://www.iki.fi/karvinen/wheretero.html](http://www.iki.fi/karvinen/wheretero.html)
# [http://myy.helia.fi/~a0600207/terodeb](http://myy.helia.fi/~a0600207/terodeb)

# Local FTP-KL
#deb [http://ftp.uni-kl.de/debian-local/](http://ftp.uni-kl.de/debian-local/) sid main

---

### Post by papapep on 2009-01-01
Bufffffffff......quin merder.

A veure, en síntesi: a banda del fet de que Debian no és exactament igual a Ubuntu en certes coses, tens un poti poti de repositoris en el qual tens fins i tot els de unstable i experimental, amb el qual els paquets que pots instal·lar et poden fer de tot.
Si no fas neteja i deixes els de l'estable (la versió estable, no la l'estable dels cavalls :-D) no crec que sigui massa viable deixar el sistema estable. 

I per a Debian hauries de buscar un fòrum o recurs especialitzat en ella (jo tinc moltes màquines amb Debian, no tinc pas res en contra (només faltaria), però aquí no és el lloc).

---

### Post by marteljorge on 2009-01-01
> **papapep said:**
> Bufffffffff......quin merder.

A veure, en síntesi: a banda del fet de que Debian no és exactament igual a Ubuntu en certes coses, tens un poti poti de repositoris en el qual tens fins i tot els de unstable i experimental, amb el qual els paquets que pots instal·lar et poden fer de tot.
Si no fas neteja i deixes els de l'estable (la versió estable, no la l'estable dels cavalls :-D) no crec que sigui massa viable deixar el sistema estable. 

I per a Debian hauries de buscar un fòrum o recurs especialitzat en ella (jo tinc moltes màquines amb Debian, no tinc pas res en contra (només faltaria), però aquí no és el lloc).

Doncs, deuria preguntar en esdebian.org?:confused:

---

### Post by papapep on 2009-01-01
El primer que faria jo és decidir si vull una instal·lació estable, testing o inestable  (A banda de preguntar al lloc correcte). Hi ha una llista de correu d'usuaris de Debian en català. 
T'hi pots subscriure a: 

[http://lists.debian.org/debian-user-catalan/](http://lists.debian.org/debian-user-catalan/)

---

### Post by marteljorge on 2009-01-02
com em puc suscriure?

---

### Post by papapep on 2009-01-02
Crec que no has llegit com cal el meu anterior post.

---

