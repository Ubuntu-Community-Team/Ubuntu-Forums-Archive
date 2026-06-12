---
title: "[RESOLT] com instal·lar StarOffice 8"
date: 2007-05-23
forum: Catalan Team
---

### Post by prostata on 2007-05-23
He baixat de Sun StarOffice 8 amb una llicencia per a estudiant, aixì és gratis, el paquet es en format .sh i no en tinc ni idea de com instal-lar-lo, ¿em podrieu dir com es fa per instal-lar aquest format d'arxius?

gràcies

---

### Post by CarlesOriol on 2007-05-23
És un arxiu executable. Marcal com a tal i executa'l

---

### Post by PellRoja on 2007-05-23
l' starOffice és l' openoffice per MAC no?

---

### Post by prostata on 2007-05-23
> **CarlesOriol said:**
> És un arxiu executable. Marcal com a tal i executa'l

he fet el seguent:

veure les propietats de l'arxiu, en permissos he marcat, permitir execuatr com un programa
he anat a var|tmp|unpack_staroffice i he executat en una terminal el fitxer setup... però un cop ha fet el extarctin, la terminal s'ah tancat.... i ara què :D perquè no veig res de res per exemple en aplicacions, estic segur o que no ho fet bé o que em falta quelcom, segur... pots dir-me quina és la questió??
gràcies

---

### Post by papapep on 2007-05-23
Apart dels permisos d'execució, ja has mirat que l'usuari sigui el correcte? Em refereixo que si intentes executar el setup com a usuari normal, que tant a l'executable com per la resta de fitxers d'instal·lació aquest usuari hi tingui permisos totals.

---

### Post by prostata on 2007-05-23
> **papapep said:**
> Apart dels permisos d'execució, ja has mirat que l'usuari sigui el correcte? Em refereixo que si intentes executar el setup com a usuari normal, que tant a l'executable com per la resta de fitxers d'instal·lació aquest usuari hi tingui permisos totals.

Tinc tots els permisos, al menys en l'apartat que ho diu, dins de propietats, consta com a lectura i escriptura, en tots....

---

### Post by prostata on 2007-05-23
> **CarlesOriol said:**
> És un arxiu executable. Marcal com a tal i executa'l

Carles, t'adjnto el que he fet per terminal per si et dona més pistes, gràcies:

josep@josep-desktop:~$ cd var
bash: cd: var: No existe el fichero ó directorio
josep@josep-desktop:~$ cd /var
josep@josep-desktop:/var$ cd tmp
josep@josep-desktop:/var/tmp$ cd unpack_staroffice
josep@josep-desktop:/var/tmp/unpack_staroffice$ ./setup
Unpacking...
Checksumming...
Extracting...
Done.
Running installer
InvocationTargetException in ArchiveReader constructornull
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)
Caused by: java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        ... 7 more
Target Exception Trace:
java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)
josep@josep-desktop:/var/tmp/unpack_staroffice$

---

### Post by papapep on 2007-05-23
Aquí: 
> Caused by: java.lang.RuntimeException: the /var/opt/sun/install directory does not exist

crec que tens una possible pista d'el problema. No hi ha cap document ni directori amb documentació que parli de com instal·lar-ho?

Has provat a fer-ho com a root, amb sudo??

Per cert, a quina arquitectura ho estàs instal·lant?? i386, AMD, PPC??

---

### Post by papapep on 2007-05-23
Abans d'ocupar més temps amb el tema, he estat mirant a [packages.ubuntu.com]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=openoffice&searchon=names&subword=1&version=feisty&release=all"), i veig que hi ha paquets d'OpenOffice per a les tres arquitectures, inclòs Powerpc. Hi ha alguna raó de pes que t'obligui a instal·lar l'StarOffice en detriment d'un simple "aptitude install openoffice.org"?

---

### Post by prostata on 2007-05-23
> **papapep said:**
> Abans d'ocupar més temps amb el tema, he estat mirant a [packages.ubuntu.com]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=openoffice&searchon=names&subword=1&version=feisty&release=all"), i veig que hi ha paquets d'OpenOffice per a les tres arquitectures, inclòs Powerpc. Hi ha alguna raó de pes que t'obligui a instal·lar l'StarOffice en detriment d'un simple "aptitude install openoffice.org"?

no hi ha cap raó de pes, excepte que amb la versió openoffice que incorpora Ubuntu, no puc crear una base de dades nova però, sense partir de cap asistent, és dir la taula si la puc crear pero quan vull fer un formulari amb aquesta taula i desprès de seguir tots el procediments de l'ajuda, el programa es queda "incpacitat" per fer el formulari. insisteixo, partin d'una creació sense cap mena de plantilla o asistent. la taula la fa, però el formulari peta, i amb staroffice en entorn windows si que anava.

---

### Post by papapep on 2007-05-23
Sembla ser que això que et passa és un problema ja detectat i creat a la base de dades d'errades d'openoffice.org : [http://qa.openoffice.org/issues/show_bug.cgi?id=77206](http://qa.openoffice.org/issues/show_bug.cgi?id=77206)

Respecte el que et passa amb l'Staroffice, has mirat al paquet que has descomprimit a veure si hi ha algun document explicant com fer-ho, m'hi jugaria un pèsol (Joaquim Mª Puyal(tm)) que ha d'haver-hi alguna pista.

---

### Post by prostata on 2007-05-23
> **papapep said:**
> Sembla ser que això que et passa és un problema ja detectat i creat a la base de dades d'errades d'openoffice.org : [http://qa.openoffice.org/issues/show_bug.cgi?id=77206](http://qa.openoffice.org/issues/show_bug.cgi?id=77206)

Respecte el que et passa amb l'Staroffice, has mirat al paquet que has descomprimit a veure si hi ha algun document explicant com fer-ho, m'hi jugaria un pèsol (Joaquim Mª Puyal(tm)) que ha d'haver-hi alguna pista.

Doncs aquesta errada és la que em crea la necessitat de canvi... sobre la resta t'adjunto tot el que he trobat, que és el que he fet però ni aixì:

Las versiones UNIX de StarOffice no se pueden instalar en una partición (V)FAT porque los sistemas de archivos FAT no admiten la creación de vínculos simbólicos. La ruta del directorio de instalación de StarOffice no debe contener un espacio.!

   1. Acceda al directorio que contiene los paquetes rpm de StarOffice.
   2. Escriba el comando siguiente: sudo alien -i -k *.i586.rpm

Nota: Este proceso puede tardar varios minutos en efectuarse.

Instalar StarOffice 8 en un servidor de archivos Linux

Si instala StarOffice en un servidor de archivos Linux, para instalar en el cliente el paquete de integración de StarOffice se deben efectuar estos pasos.

Nota: Para instalar este paquete se necesita RedHat Package Manager (RPM).

   1. En el cliente, abra un terminal y conviértase en usuario raíz.
   2. Escriba "rpm -ivh staroffice-Linux_distribution_name-menus-8.0.0-xx.noarch.rpm". El paquete de integración de menús para la distribución de Linux se encuentra en la carpeta rpm del directorio de instalación de StarOffice.
   3. En el directorio /etc, modifique el vínculo simbólico de staroffice8 para que el vínculo haga referencia a la instalación de StarOffice en el servidor de archivos. Por ejemplo, si monta el servidor de archivos como /mnt/nfs, escriba "ln -sf/mnt/nfs/staroffice8 staroffice8".

---

### Post by prostata on 2007-05-23
la sequencia per instalar definitiva i correctament la suite satroffice 8 es fácil i senzitlla, només calen dues sentencies per terminal a saber:

1ª) des de le directori on estiguin els paquets RPMS;  sudo alien -d -v -c *.rpm
trigará força tot aquest process però tingueu paciencia

2ª) un cop tot això fet: sudo dpkg -i *.deb

aquesta instal-lació deu ser completa per tal de poder veure la suite de la seguenta manera: 
 
amb l'editor de menus busqueu els executables que és troben en /opt/staroffice/programs son tots els que comencen amb s per exemple swriter, sdraw, scalc, etc

espero que sigui útil per a tothom que tingui un problema semblant...

---

### Post by papapep on 2007-05-23
Quan es resolgui el problema pel qual heu creat el fil de la consulta no creeu nous fils, ja que aleshores qui tingui el mateix problema té números de trobar una conversa i no l'altra.

Hauries d'afegir la teva resposta (per cert si comentes d'on treus els rpm's ajudaràs a entendre el tema als més inexperts) al fil inicial.

---

### Post by prostata on 2007-05-24
> **papapep said:**
> Quan es resolgui el problema pel qual heu creat el fil de la consulta no creeu nous fils, ja que aleshores qui tingui el mateix problema té números de trobar una conversa i no l'altra.

Hauries d'afegir la teva resposta (per cert si comentes d'on treus els rpm's ajudaràs a entendre el tema als més inexperts) al fil inicial.


OK, tens raó, vols que la torni a possar dins el fil inicial??? o la pot posar l'administrador mateix??

---

### Post by prostata on 2007-05-24
la sequencia per instalar definitiva i correctament la suite satroffice 8 es fácil i senzitlla, només calen dues sentencies per terminal a saber:

1ª) des de le directori on estiguin els paquets RPMS;
 sudo alien -d -v -c *.rpm
trigará força tot aquest process però tingueu paciencia

2ª) un cop tot això fet: 
sudo dpkg -i *.deb

aquesta instal-lació deu ser completa per tal de poder veure la suite de la seguenta manera:

amb l'editor de menus busqueu els executables que és troben en /opt/staroffice/programs son tots els que comencen amb s per exemple swriter, sdraw, scalc, etc

espero que sigui útil per a tothom que tingui un problema semblant...

NOTA, la carpeta que conté els RPMS, al menys en el meu cas eren a var/tmp/unpack_satroffice. Quan vaig descarregar el programa NO el vaig guardar a disc sino que el vaig tractar, si no  recordo malament, amb "¿gedebian"?, no me'n recordo, pero crec que és una especie d'instalador per defecte en Ubuntu, que instala el paquet sencer en aquest directori i és a partir d'ell que se executen les sentencies, les quals el que fan es tot el proces de descompresió-instalació del soft, ja que una cosa es l'instalació del paquet en si, i un altre la de la suite propiament parlant.

---

### Post by orestesmas on 2007-05-25
Fet :-)

---

