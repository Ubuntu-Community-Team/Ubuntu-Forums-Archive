---
title: "[SOLVED] Eliminar dependencias de KDE"
date: 2008-02-15
forum: Argentina Team
---

### Post by Vero1 on 2008-02-15
Hola a todos,

Antes de volver a equivocarme, quisiera que alguien me diga exactamente qué tengo que hacer.

Hace un tiempo instalé KDE(tengo Gnome). No me gustó KDE y lo quise eliminar pero pasó que tambien me eliminó todo Gnome y tuve que pedirles socorro a Uds. para arreglar el problema.

O sea, actualmente parece que tengo los dos o por lo menos dependencias de KDE que quiero eliminar porque no lo uso y porque el otro día bajé como 35 actualizaciones(tengo configuradas las actualizaciones automáticas).

Cuáles serían los pasos a seguir entonces para eliminar todo lo que sea KDE y que no me toque Gnome?

Muchas gracias de antemano.

p.d.
He visto algunos comentarios en Google pero me parece mas seguro preguntar aquí.

saludos

---

### Post by Mataca on 2008-02-15
Vero  Antes que nada te cuento que si desinstalas las dependencias vas a dejar paquetes huerfanos, los que uses de KDE por ej. Yo uso gnome y si haria esto no podria usar amarok. Claro que una vez terminada la desinstalación, los instalas de nuevo y listo.

Dependiendo de como lo instalaste tenés, hasta donde yo se, dos formas. Te copio exactamente lo que usé yo en feisty alguna vez y lo saqué  del blog de Beuno,:

Desinstalar (si usaste aptitude para instalar):
```
sudo aptitude remove kubuntu-desktop
```

Desinstalar (si usaste apt-get o synaptic para instalar):
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools
```

Yo pasé por lo mismo vero, hace un tiempo y esto que te paso me sirvió de 10!!

fuente de los codigos:[http://www.kbglob.com/cat/gnulinux/ubuntu/]("http://www.kbglob.com/cat/gnulinux/ubuntu/")

---

### Post by Vero1 on 2008-02-15
Hola mataca,

Antes que nada gracias por contestar.

Realmente no recuerdo cómo lo instalé, pero qué pasa si pruebo primero sudo aptitude? 

Si no funciona siempre puedo probar el otro.

Qué opinás?

Gracias

---

### Post by Mataca on 2008-02-15
No creo que vallas a tener problemas, en un índice de 99% de confianza.
Yo lo instalé con sinaptic y lo quité con aptitude, si te sirve para mas datos. Creo que no vas a tener ningun problema.

Pd. No es necesario agradecer, me han ayudado tantas veces acá.. :)

---

### Post by Vero1 on 2008-02-15
Bueno voy a probar con aptitude.

En cuanto a agradecer, creo que sí es necesario porque nadie tiene la obligación de contestar y si lo hace merece mi agradecimiento :-)

saludos

---

### Post by Vero1 on 2008-02-15
Bueno, como no me dió resultado ya que el informe que tiró la consola fue que no encontró ningun paquete, fuí a Synaptic y manualmente desinstalé todo lo de KDE, pero esta vez no me eliminó nada de Gnome porque me fijé muy bien en lo que iba a borrar.

De todas formas gracias por haber querido ayudarme.

saludos:)

---

### Post by Mataca on 2008-02-15
De nada vero !!!

Si te quedaron librerias huerfanas podes instalar desde sinaptic GtkOrphan. Que es una herramienta grafica que utiliza deborphan muy linda y facil de usar.
Te muestra las librerias huerfanas que ya no usas. asi las podés eliminar.

Fijate si te sirve esto tambien.

---

### Post by Vero1 on 2008-02-16
Hola mataca,

Acabo de instalar gtkorphan pues no lo tenía instalado.
Lo corrí desde Consola y me encontró un montón de paquetes húerfanos que ya eliminé.

Gracias de nuevo :-)

saludos

---

### Post by Mataca on 2008-02-16
Un placer :)

---

### Post by Vero1 on 2008-02-16
:-d

:-D

---

### Post by Vero1 on 2008-02-16
Una pregunta:

Qué significa la taza blanca entre los beans?

gracias :-)

---

### Post by marianom on 2008-02-16
> **Vero1 said:**
> Una pregunta:

Qué significa la taza blanca entre los beans?

gracias :-)

Basicamente [nada]("http://ubuntuforums.org/showthread.php?t=239560").

---

### Post by Vero1 on 2008-02-17
ok, gracias.

---

### Post by ubuntu27 on 2008-02-20
Se que has resuelto el problema, pero por si acaso, pon el siguiente comando en el terminal (COPYA Y PEGA). Ese comando elinara todo los paqutes de KDE e qt e instalara paquetes que usa UBuntu (GNOME). 

Nota, que este comando es para la version Gutsy Gibbon.

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

---

### Post by Vero1 on 2008-02-20
Muchas gracias ubuntu27.

saludos

---

