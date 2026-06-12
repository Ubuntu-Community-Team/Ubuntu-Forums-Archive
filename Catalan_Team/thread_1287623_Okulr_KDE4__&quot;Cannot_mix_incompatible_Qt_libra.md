---
title: "Okulr KDE4 / &quot;Cannot mix incompatible Qt libraries&quot;"
date: 2009-10-10
forum: Catalan Team
---

### Post by Pablitus on 2009-10-10
Hola,

Fins fa no gaire utilitzava Okular com a lector de pdfs, però des de fa unes setmanes no puc.

El missatge d'error que dona l'interpret de comandes és el que hi ha al títol del post:> Cannot mix incompatible Qt libraries Faig servir Ubuntu 8.04 amb gnome i hi tinc instal·lades altres aplicacions de KDE (Amarok, Ktorrent, K3b, KPDF, Ktechlab, etc...). Crec que totes per a KDE3, mentre que Okular és per a KDE4.

He provat desinstal·lant i reinstal·lant alguns programes, la veritat és que una mica al tuntun, i també ho he preguntat a google, però no n'he sabut treure res clar.

M'he d'oblidar d'okular si no vull actualitzar les altres aplicacions a la versió per a KDE4, o algú se li acut una solució que pugui provar?

Gràcies!

---

### Post by RafaelCarreras on 2009-10-10
Si no vaig errat, per al KDE3, el lector de pdf és el KPDF i l'Okular és el del KDE4. I tenir el KDE3 i 4 alhora és complicat, com pots veure, perquè les Qt3 i les Qt4 són massa diferents.

---

### Post by Pablitus on 2009-10-10
Hola!

> Si no vaig errat, per al KDE3, el lector de pdf és el KPDF i l'Okular és el del KDE4Exacte.

> I tenir el KDE3 i 4 alhora és complicat, com pots veure, perquè les Qt3 i les Qt4 són massa diferents. Ja m'ho suposo, però fins fa alguns dies els tenia tots dos i els podia fer anar sense problemes. No és gens greu, però okular m'anava molt bé.

Fins ara!
Pau

---

### Post by RafaelCarreras on 2009-10-10
Vaja, doncs a veure si hi ha algú que sàpiga de conflictes de biblioteques.
Es va passar després d'alguna actualització, o després d'instal·lar algun programa del KDE?

---

### Post by Pablitus on 2009-10-11
Hola RafaelCarreras,

Va ser després d'una actualització. Així que potser amb una altra futura actualització tornarà a funcionar....

Fins ara,
Pau

---

### Post by orestesmas on 2009-10-12
Anem a veure: obre un terminal i mostra'ns la resposta a les següents ordres:

```

ldd `which okular` | grep Qt
dpkg -l | grep qt

```

En el primer cas, la cometa és un accent greu. Per obtenir-la pitja la tecla de l'accent greu seguida de l'espai.
Respecta les majúscules

---

### Post by Pablitus on 2009-10-14
Hola, 

Ahí va, per una banda:

```
pau@pau-desktop:~$ ldd `which /usr/lib/kde4/bin/okular` | grep Qt
	libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0xb7ce6000)
	libQtGui.so.4 => /usr/lib/libQtGui.so.4 (0xb6cd6000)
	libQtNetwork.so.4 => /usr/lib/libQtNetwork.so.4 (0xb686c000)
	libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0xb681c000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0xb67c4000)
	libQtSvg.so.4 => /usr/lib/libQtSvg.so.4 (0xb676d000)
```

I de l'altra:

```
pau@pau-desktop:~$ dpkg -l | grep qt
ii  libavahi-qt3-1                             0.6.22-2ubuntu4.1                                          Avahi Qt 3 integration library
ii  libdbus-qt-1-1c2                           0.62.git.20060814-2build1                                  simple interprocess messaging system (Qt-based shared li
ii  libpoppler-qt4-2                           0.6.4-1ubuntu3.2                                           PDF rendering library (Qt 4 based shared library)
ii  libqt3-mt                                  3:3.3.8-b-0ubuntu3                                         Qt GUI Library (Threaded runtime version), Version 3
ii  libqt4-core                                4.3.4-0ubuntu3.1                                           Qt 4 core non-GUI functionality runtime library
ii  libqt4-gui                                 4.3.4-0ubuntu3.1                                           Qt 4 core GUI functionality runtime library
ii  libqt4-network                             4.4.0-1ubuntu5~hardy1                                      Qt 4 network module
ii  libqt4-qt3support                          4.3.4-0ubuntu3.1                                           Qt 3 compatibility library for Qt 4
ii  libqt4-sql                                 4.3.4-0ubuntu3.1                                           Qt 4 SQL database module
ii  libqtcore4                                 4.4.0-1ubuntu5~hardy1                                      Qt 4 core module
ii  libqtgui4                                  4.4.0-1ubuntu5~hardy1                                      Qt 4 GUI module
ii  libqthreads-12                             1.6.8-6ubuntu1                                             QuickThreads library for Guile
ii  libstrigiqtdbusclient0                     0.5.7-2                                                    library for writing D-Bus clients for Strigi Desktop Sea
ii  python-qt4                                 4.3.3-2ubuntu4.1                                           Python bindings for Qt4
ii  python-qt4-common                          4.3.3-2ubuntu4.1                                           Shared files for PyQt4

```

Gràcies!
Fins aviat.

---

### Post by orestesmas on 2009-10-15
En principi veig que l'okular està enllaçat a les llibreries Qt4 (les del KDE4), i que aquestes estan correctament instal·lades. Fins aquí res d'estrany.

Ara bé, observo que tens una barreja de versions de llibreries Qt4: tens algunes parts a la versió 4.3.3, altres a la 4.3.4 i fins i tot un parell o tres a la 4.4.0.

Ignoro si això pot ser la causa dels teus maldecaps, però en qualsevol cas no em sembla massa bo. Com ha pogut passar? Potser en fer una actualització hi havia alguns paquets que encara no havien entrat al repositori, i d'aquí la barreja de versions. Si fos així, s'hauria d'arreglar en una propera actualització.

També pot ser que tinguis activats repositoris no oficials, que hagin pogut provocar aquesta barreja de versions. En aquest cas prova de desactivar-los i d'esborrar i reinstal·lar els programes afectats, a veure què tal.

Més enllà d'això se'm fa difícil de dir, perquè jo ja no tinc la 8.04 a cap ordinador. Va ser la versió on Ubuntu va introduir el salt al KDE4 com a cosa opcional i era una mica una barreja precària. T'aconsello una actualització de versió de sistema com més aviat millor.

---

### Post by Pablitus on 2009-10-15
Hola Orestesmas,

A partir del que m'has dit he desinstal·lat des de Synaptic les llibreries Qt4 que esmentes que podrien ser problemàtiques, vigilant que en fer-ho no desinstal·lés cap aplicació que vulgués mantenir. He desinstal·lat també okular.

He desactivat algun repositori no oficial que tenia, he tornat a instal·lar okular et voilà, torna a ser aquí.

Ara la sortida de les ordres que em vas passar són:```
pau@pau-desktop:~$ ldd `which /usr/lib/kde4/bin/okular` | grep Qt
	libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0xb7df2000)
	libQtGui.so.4 => /usr/lib/libQtGui.so.4 (0xb7008000)
	libQtNetwork.so.4 => /usr/lib/libQtNetwork.so.4 (0xb6be9000)
	libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0xb6b99000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0xb6b40000)
	libQtSvg.so.4 => /usr/lib/libQtSvg.so.4 (0xb6aea000)

```i```
pau@pau-desktop:~$ dpkg -l | grep qt
ii  libavahi-qt3-1                             0.6.22-2ubuntu4.1                                          Avahi Qt 3 integration library
ii  libdbus-qt-1-1c2                           0.62.git.20060814-2build1                                  simple interprocess messaging system (Qt-based shared li
ii  libpoppler-qt4-2                           0.6.4-1ubuntu3.2                                           PDF rendering library (Qt 4 based shared library)
ii  libqt3-mt                                  3:3.3.8-b-0ubuntu3                                         Qt GUI Library (Threaded runtime version), Version 3
ii  libqt4-core                                4.3.4-0ubuntu3.1                                           Qt 4 core non-GUI functionality runtime library
ii  libqt4-gui                                 4.3.4-0ubuntu3.1                                           Qt 4 core GUI functionality runtime library
rc  libqt4-network                             4.4.0-1ubuntu5~hardy1                                      Qt 4 network module
ii  libqt4-qt3support                          4.3.4-0ubuntu3.1                                           Qt 3 compatibility library for Qt 4
ii  libqt4-sql                                 4.3.4-0ubuntu3.1                                           Qt 4 SQL database module
rc  libqtgui4                                  4.4.0-1ubuntu5~hardy1                                      Qt 4 GUI module
ii  libqthreads-12                             1.6.8-6ubuntu1                                             QuickThreads library for Guile
ii  libstrigiqtdbusclient0                     0.5.7-2                                                    library for writing D-Bus clients for Strigi Desktop Sea
ii  python-qt4-common                          4.3.3-2ubuntu4.1
```

Segueix havent-hi una mica de tot, no? Bé, la qüestió és que torna a funcionar. Ara ja seria la repera tenir-lo traduït.

> T'aconsello una actualització de versió de sistema com més aviat millor. 

De moment em funciona molt bé i tinc totes les aplicacions que necessito amb la 8.04. Tinc un cd amb el koala kàrmic que instal·laré en unes partició que tinc per fer proves i potinejar, però d'entrada no pensava canviar. Potser si volgués fer servir KDE4 o "lo último de lo último" d'alguns programes si que seria necessari.

Moltes gràcies i fins aviat!!

Pau

---

### Post by orestesmas on 2009-10-16
> **Pablitus said:**
> Hola Orestesmas,
Segueix havent-hi una mica de tot, no? Bé, la qüestió és que torna a funcionar. Ara ja seria la repera tenir-lo traduït.


Si, hi ha una mica de tot, però sense una Hardy "neta" al davant no et puc dir si això és normal o no. Però si ara et funciona ja està bé.

La traducció de l'okular (almenys a la Karmic) és al paquet language-pack-kde-base. Si no el tens instal·lat, instal·la'l.

---

### Post by Pablitus on 2009-10-16
Bones,

```
La traducció de l'okular (almenys a la Karmic) és al paquet language-pack-kde-base. Si no el tens instal·lat, instal·la'l. 
```

Si que el tinc instal·lat, i de fet tinc totes les altres aplicacions de KDE en català. De totes maneres no és cap problema tenir-lo en anglès.

Faig servir okular per la possibilitat d'afegir anotacions als pdf i pels punts o bookmarks.

Gràcies per tot,

Pau

---

