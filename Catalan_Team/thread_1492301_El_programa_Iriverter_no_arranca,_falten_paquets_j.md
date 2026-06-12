---
title: "El programa Iriverter no arranca, falten paquets java...."
date: 2010-05-24
forum: Catalan Team
---

### Post by sianeu on 2010-05-24
He instalat Iriverter amb el Synaptic, però no funciona. Per cònmola dona aquest error:

> sianeu@unicorn:~$ iriverter
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/events/SelectionListener
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.events.SelectionListener
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
	... 12 more
Could not find the main class: org.thestaticvoid.iriverter.ConverterUI. Program will exit.
 

He buscat java per synaptic, però hi ha una quantitat de paquets que mareja, i no tinc idea del que em cal.

Si algù sap el que falta........

Salut

---

### Post by wgarcia on 2010-05-25
Tens libswt-gtk-3.5-java instal·lat?

sudo aptitude search libswt-gtk-3.5-java

---

### Post by sianeu on 2010-05-27
Perdò pel retar.
Sí tinc instal·lat el libswt-gtk-3.5-java. He insta·lat a mès el libswt-gtk-3.5-java-gcj, sense cap cambi en el problema ni en el missatge d'error.

Gracies per l'ajut.

Salut

---

### Post by wgarcia on 2010-05-27
Mira si el que s'explica en aquest enllaç t'ho arregla:

[http://ubuntuforums.org/showpost.php?p=2855567&postcount=5](http://ubuntuforums.org/showpost.php?p=2855567&postcount=5)

---

### Post by sianeu on 2010-05-28
Aquì suggereixen instal·lar el paquet libswt3.2-gtk-jni. Per desgracia aquest paquet ja no hi es en el Lucid, diu que el paquet eclipse-rcp el reemplaça. He instal·lat aquest, pero això per si sol no arregla el problema.

Consola:> ianeu@unicorn:~$ sudo apt-get install libswt3.2-gtk-jni
[sudo] password for sianeu: 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
El paquet libswt3.2-gtk-jni no té versió disponible, però un altre paquet
en fa referència. Això normalment vol dir que el paquet falta,
s'ha tornat obsolet o només és disponible des d'una altra font.

Tot i que els següents paquets el reemplacen:
  eclipse-rcp
E: El paquet libswt3.2-gtk-jni no té candidat d'instal·lació
sianeu@unicorn:~$ sudo apt-get install eclipse-rcp
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Els paquets següents s'instal·laren automàticament i ja no són necessaris:
  vcdimager libiso9660-7 libvcdinfo0
Empreu «apt-get autoremove» per a suprimir-los.
S'instal·laran els següents paquets extres:
  libequinox-osgi-java libicu4j-java
Paquets suggerits:
  eclipse
S'instal·laran els paquets NOUS següents:
  eclipse-rcp libequinox-osgi-java libicu4j-java
0 actualitzats, 3 nous a instal·lar, 0 a suprimir i 10 no actualitzats.
Es necessita obtenir 23,3MB d'arxius.
Després d'aquesta operació s'empraran 28,0MB d'espai en disc addicional.
Voleu continuar [S/n]? s
Bai:1 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/universe libequinox-osgi-java 3.5.2-2ubuntu4.1 [2136kB]
Bai:2 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/universe libicu4j-java 4.0.1.1-1 [5243kB]
Bai:3 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/universe eclipse-rcp 3.5.2-2ubuntu4.1 [15,9MB]
23,3MB baixats en 1min 43s (226kB/s)                                           
S'està seleccionant el paquet libequinox-osgi-java prèviament no seleccionat.
(S'està llegint la base de dades ... hi ha 176719 fitxers i directoris instal·lats actualment.)
S'està desempaquetant libequinox-osgi-java (de .../libequinox-osgi-java_3.5.2-2ubuntu4.1_all.deb) ...
S'està seleccionant el paquet libicu4j-java prèviament no seleccionat.
S'està desempaquetant libicu4j-java (de .../libicu4j-java_4.0.1.1-1_all.deb) ...
S'està seleccionant el paquet eclipse-rcp prèviament no seleccionat.
S'està desempaquetant eclipse-rcp (de .../eclipse-rcp_3.5.2-2ubuntu4.1_amd64.deb) ...
S'està configurant libequinox-osgi-java (3.5.2-2ubuntu4.1) ...
S'està configurant libicu4j-java (4.0.1.1-1) ...
S'està configurant eclipse-rcp (3.5.2-2ubuntu4.1) ...


El segon pas era modificar amb gedit l'arxiu /usr/bin/iriverter:

> then add the following so that it becomes the second line in the file

Code:

LD_LIBRARY_PATH="/usr/lib/jni"

the finished file should now look like this:

Code:

#!/bin/sh
LD_LIBRARY_PATH="/usr/lib/jni"
prefix=/usr
exec_prefix=${prefix}
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.thestaticvoid.iriverter.ConverterUI $*



Però suposo que això ferìa referencia al paquet que no he pogut instaD·lar i que deurìa fer-ho a /usr/lib/jni. He mirat la descripciò que fa el synaptic dels altres dos paquets que s'han instal·lat (libequinox-osgi-java libicu4j-java) però no veig que tinguin res a veure. 

El meu arxiu /usr/bin/iriverter obert amb gedit diu:

> #!/bin/sh
prefix=/usr
exec_prefix=${prefix}
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib:${exec_prefix}/lib/jni -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt-gtk-3.5.jar org.thestaticvoid.iriverter.ConverterUI $*

En fí, gràcies per l'ajut. No se si podràs treure'n res de tot això.

Salut

PD: Per synaptic he vist que tinc insta.lats, entre altres els paquets libswt-gtk-3.5-java libswt-gtk-3.5-java-gcj libswt-gtk-3.5-jni libswt-gnome-gtk-3.5-jni

Vist això he provat a modificar l'arxiu /usr/bin/iriverter tal com indica el segon pas de la pàgina. Ha quedat aixì:

> #!/bin/sh
LD_LIBRARY_PATH="/usr/lib/jni"
prefix=/usr
exec_prefix=${prefix}
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib:${exec_prefix}/lib/jni -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt-gtk-3.5.jar org.thestaticvoid.iriverter.ConverterUI $* 

Tampoc ha funcionat. El missatge d'error es el mateix.

---

### Post by wgarcia on 2010-05-28
Suposo que en algun moment actualitzaran iriverter per fer servir les noves llibreries. De moment pots potser provar de baixar-te la la llibreria que et falta directament i instal·lar-la. Encara hi és als dipòsits de "debian". La pots baixar d'aquí:

[http://packages.debian.org/lenny/libswt3.2-gtk-jni](http://packages.debian.org/lenny/libswt3.2-gtk-jni)

Mira a sota de tot de baixar-la per a la teva instal·lació (suposo que tens ubuntu normal, per tant has de baixar la que posa "i386"). Per instal·lar-la, simplement baixa't l'arxiu "deb" a algun lloc on el puguis trobar i clica sobre ell per instal·lar, o a la carpeta on te l'hagis baixat des d'una terminal de comandes fes:

sudo dpkg -i libswt3.2-gtk-jni_3.2.2-6.1_i386.deb

Si no et funciona i no vols mantenir aquest paquet, per desinstal·lar-lo fes simplement

sudo apt-get remove libswt3.2-gtk-jni

No sé si funcionarà però es pot provar.

---

### Post by sianeu on 2010-05-28
Tinc el Lucid 64bits i he instal·lat el corresponent, però sense èxit. Tot segueix igual. Què hi farem...!

Salut

---

### Post by wgarcia on 2010-05-28
Has mirat amb 

sudo apt-cache search iriverter

que et mostra les dependències, si et falta alguna cosa més?

---

### Post by sianeu on 2010-05-28
Mmm...... Em surt aixó:

> sianeu@unicorn:~$ sudo apt-cache search iriverter
[sudo] password for sianeu: 
iriverter - converts video for use on various multimedia players
     

:confused:

Salut

---

### Post by wgarcia on 2010-05-29
Perdona, no és "search" sino "show":

sudo apt-cache show iriverter

---

### Post by sianeu on 2010-05-29
> sianeu@unicorn:~$ sudo apt-cache show iriverter
[sudo] password for sianeu: 
Package: iriverter
Priority: optional
Section: multiverse/graphics
Installed-Size: 504
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Richard Bailey <rmjb@mail.com>
Architecture: all
Version: 0.16-0ubuntu4
Depends: java-gcj-compat | java-gcj-compat-dev, libswt-gtk-3.5-java, mplayer-nogui | mplayer, mencoder, ffmpeg
Filename: pool/multiverse/i/iriverter/iriverter_0.16-0ubuntu4_all.deb
Size: 250670
MD5sum: d7c445b9e05d85a5523069feae836b45
SHA1: 4648577216468be5a7413dd0cc6b509dfd57e618
SHA256: e1c4ac2b030860236b64954dbaa00aed6381493e6954e1f8eed85f92fff626d8
Description: converts video for use on various multimedia players
 iriverter is a cross-platform frontend to mencoder designed to facilitate the
 conversion of almost any video format to one that is playable on various
 multimedia players.
Homepage: [http://iriverter.sourceforge.net/index.shtml](http://iriverter.sourceforge.net/index.shtml)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu


Està instal·lat: libswt-gtk-3.5-java, mplayer, mencoder, ffmpeg. El mplayer-nogui no hi es, no se si cal (que vol dir la "|" entre mplayer i mplayer-nogui).
 El paquet java-gcj-compat torna a ser un cas "especial":
> sianeu@unicorn:~$ sudo aptitude search java-gcj-compat
v   java-gcj-compat                 -                                           
v   java-gcj-compat-dev             -                                           
v   java-gcj-compat-headless        
sianeu@unicorn:~$ sudo apt-get install java-gcj-compat
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Nota: s'està seleccionant gcj-jre en comptes de java-gcj-compat
gcj-jre ja es troba en la versió més recent.
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 10 no actualitzats.

 
Semblaria que tot està correcte, però no funciona

Salut

---

### Post by wgarcia on 2010-05-29
El "|" és el "o" lògic, és a dir que depèn d'un paquet o d'un altre. Un últim intent pot ser intentar instal·lar el paquet de debian:

[http://ftp.de.debian.org/debian/pool/main/j/java-gcj-compat/java-gcj-compat_1.0.78-2_amd64.deb](http://ftp.de.debian.org/debian/pool/main/j/java-gcj-compat/java-gcj-compat_1.0.78-2_amd64.deb)

Ara bé, no faig servir iriverter, però sembla que tota la seva funcionalitat la pots tenir usant "mencoder" o "ffmpeg" des de la línia de comandes. Per convertir vídeo d'un format a un altre pot ser el mètode preferit. I si vols una eina gràfica "Pitivi" que ve per defecte amb Lucid sembla una eina força fàcil d'usar.

---

### Post by sianeu on 2010-05-29
No hi ha res a fer. Al intentar instal·lar aquest paquet ha donaat error per que en faltaba un altre (java-gcj-compat-headless). L'he descarregat de la mateixa pàgina que m'has donat avans (devian), però al intentar intalar-lo dona incompatibilitat:

> Error: Trenca el paquet existent «gcj-jre-headless» per conflicte amb java-gcj-compat-headless (< 1.0.80-6)

Volia provar el Iriverter com a programa gràfic de mencoder, que té un manual (man mencoder), que tira d'esquena. De moment seguiré amb el avidemux.

Moltes gràcies pel teu ajut. S'ha intentat.

Salut

---

### Post by quitus on 2010-05-30
També existeix winff que es un eina gràfica per ffmpeg.

salut

---

### Post by menjabits on 2010-10-29
No sé si al final algú va aconseguir fer-lo anar.. per si de cas, amb Ubuntu 10.10 he tingut que fer el següent:

1) Obrim el terminal
2) Introduïm la seguent comanda:
sudo gedit /usr/bin/iriverter

3) S'obre un fitxer i veurem entre mig que diu:
lib/java/swt-gtk-3.5.jar

S'ha d'introduïr

lib/java/swt-gtk-3.5**.1**.jar

I així m'ha funcionat.

---

