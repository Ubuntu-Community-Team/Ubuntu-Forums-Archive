---
title: "problema con python 2.5 en upgrade a gutsy"
date: 2007-11-26
forum: Argentina Team
---

### Post by nenesio on 2007-11-26
hola, estaba haciendo el upgrade a gutsy desde el update manager
pero a mitad de la atcualizacion se cerro el update manager y ahora
al pedir de nuevo el upgrade dice esto :

usuario@ubuntu:~$ sudo apt-get dist-upgrade
Password:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
  alacarte: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  aptitude: Depende: libapt-pkg-libc6.3-6-3.11 pero no es instalable
  bicyclerepair: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  bittornado: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  deskbar-applet: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  dpkg: Rompe: aptitude (< 0.4.6.1-1ubuntu2) pero 0.4.0-5ubuntu3 está instalado
  gdebi: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  gimp-python: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  gnome-menus: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  hplip: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  kde-guidance: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  libmetacity0: Depende: metacity-common (>= 1:2.20) pero no está instalado
                Depende: metacity-common (< 1:2.21) pero no está instalado
  pykdeextensions: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-adns: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-cddb: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-clientcookie: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-crypto: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-egenix-mxproxy: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-egenix-mxstack: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-egenix-mxtexttools: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-egenix-mxtools: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-epydoc: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-eunuchs: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-examples: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-gadfly: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-gd: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-genetic: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-geoip: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-gmenu: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-htmlgen: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-htmltmpl: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-id3lib: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-imaging: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-imaging-sane: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-jabber: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-kjbuckets: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-ldap: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-libxml2: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-mysqldb: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-netcdf: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-newt: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pam: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-parted: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pexpect: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pgsql: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pisock: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pqueue: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pyao: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pylibacl: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pyogg: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pyopenssl: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pyvorbis: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-pyxattr: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-reportlab: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-simpletal: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-soappy: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-sqlite: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-stats: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-syck: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-unit: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-xml: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  python-xmpp: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  rdiff-backup: Depende: python (< 2.5) pero 2.5.1-1ubuntu2 está instalado
  serpentine: Depende: python-xml (>= 0.8.4-5) pero 0.8.4-1ubuntu3 está instalado
  ubiquity: Depende: libdebian-installer4 (>= 0.52ubuntu1) pero 0.37 está instalado
            Depende: libparted1.7-1 (>= 1.7.1-1) pero no está instalado
  ubiquity-frontend-mythbuntu: Depende: restricted-manager pero no está instalado
                               Depende: mythtv-common pero no está instalado
                               Depende: expect
                               Depende: guidance-backends pero no está instalado
                               Depende: vnc4-common pero no está instalado
                               Depende: lirc (>= 0.8.2-0ubuntu3) pero no está instalado
E: Dependencias incumplidas. Pruebe de nuevo usando -f.
 
pero cunado ejecuto sudo apt-get -f install aparece esto :

dpkg: error al procesar /var/cache/apt/archives/metacity-common_1%3a2.20.0-0ubuntu3_all.deb (--unpack):
 intentando sobreescribir `/usr/share/man/man1/metacity-theme-viewer.1.gz', que está también en el paquete metacity
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 /var/cache/apt/archives/metacity-common_1%3a2.20.0-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

alguien sabe alguna solucion ?

---

### Post by Hei Ku on 2007-11-26
estas complicado. A mi me paso algo similar y tuve que terminar la instalación a mano, buscando los paquetes con problemas.

Primero que todo, cuanta experiencia tenes en resolver problemas de dependencias? Es recuperable lo que te paso, pero vas a tener que arremangarte.

Segundo, postea tu archivo /etc/apt/sources.list para ver como quedo.

---

### Post by nenesio on 2007-11-26
en linux no soy nuevo antes era susero y me vine a ubuntu para cambiar hace como un mes, recopilar instalacion de paquetes deb ya se me se arrreglar, ya instale varios manual pero algunos igual me sale que depende de otro, lo quehago es instalar algunos paquetes debian separandolo con ; pero los deja sin configurar, 

lo que me desconcierta algo es metacity, bueno instalare todo la libreria python a mano a ver que pasa ahora el sistema esta roto si apago la pc oops adios sistema, bueno luego aviso a ver que tal

editando se me olvido dar el sources, lo que hice fue ir a la pagina o-matic y pedi los repositorios 7.10

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb-src [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

deb-src [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

---

### Post by Hei Ku on 2007-11-26
Te quedo el sources para instalar gutsy. O sea que ahora estas en el baile.

Yo tuve un caso similar al tuyo, con un archivo que compartian varios archivos de compiz y no queria desinstalarlo.
Proba a desinstalar el python, a ver que dice. Si dice que comparte el archivo con el metacity, podes probar con el comando dpkg.

ADVERTENCIA! Esto es peligroso para el sistema, y solo para estos casos.

dpkg -r --force-conflicts <paquete>

Eso te va a permitir desinstalar un paquete aunque tengas conflictos. Lo ideal en esos casos es desinstalar los dos, y enseguida reinstalar uno, para resolver el tema rapido.
Y despues de eso seguir con:

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

Probablemente hasta que aparezca el siguiente error, y ahi lavar, enjuagar y repetir. :)

---

### Post by nenesio on 2007-11-26
aparece esto 

usuario@ubuntu:~$ sudo dpkg -r --force-conflicts python
Password:
dpkg: problemas de dependencias impiden la desinstalación de python:
 python-pyogg depende de python (<< 2.5).
 python-pyogg depende de python (>= 2.4).
 python-pyogg depende de python (<< 2.5).
 python-pyogg depende de python (>= 2.4).
 python2.4-soappy depende de python (>= 2.4).
 python2.4-soappy depende de python (<< 3).
 python2.4-soappy depende de python (>= 2.4).
 python2.4-soappy depende de python (<< 3).
 kdebluetooth depende de python; sin embargo:
  El paquete `python' va a ser desinstalado.
 bicyclerepair depende de python (<< 2.5).
 bicyclerepair depende de python (>= 2.4).
 bicyclerepair depende de python (<< 2.5).
 bicyclerepair depende de python (>= 2.4).
 python-egenix-mxstack depende de python (<< 2.5).
 python-egenix-mxstack depende de python (>= 2.4).
 python-egenix-mxstack depende de python (<< 2.5).
 python-egenix-mxstack depende de python (>= 2.4).
 python-examples depende de python (>= 2.4).
 python-examples depende de python (<< 2.5).
 python-examples depende de python (>= 2.4).
 python-examples depende de python (<< 2.5).
 hplip depende de python (<< 2.5).
 hplip depende de python (>= 2.4).
 hplip depende de python (<< 2.5).
 hplip depende de python (>= 2.4).
 python-id3lib depende de python (>= 2.4).
 python-id3lib depende de python (<< 2.5).
 python-id3lib depende de python (>= 2.4).
 python-id3lib depende de python (<< 2.5).
 ubuntu-minimal depende de python; sin embargo:
  El paquete `python' va a ser desinstalado.
 python-xmpp depende de python (>= 2.4).
 python-xmpp depende de python (<< 2.5).
 python-xmpp depende de python (>= 2.4).
 python-xmpp depende de python (<< 2.5).
 python-egenix-mxtexttools depende de python (<< 2.5).
 python-egenix-mxtexttools depende de python (>= 2.4).
 python-egenix-mxtexttools depende de python (<< 2.5).
 python-egenix-mxtexttools depende de python (>= 2.4).
 python-libxml2 depende de python (<< 2.5).
 python-libxml2 depende de python (>= 2.4).
 python-libxml2 depende de python (<< 2.5).
 python-libxml2 depende de python (>= 2.4).
 python-cddb depende de python (<< 2.5).
 python-cddb depende de python (>= 2.4).
 python-cddb depende de python (<< 2.5).
 python-cddb depende de python (>= 2.4).
 python-htmlgen depende de python (>= 2.4).
 python-htmlgen depende de python (<< 2.5).
 python-htmlgen depende de python (>= 2.4).
 python-htmlgen depende de python (<< 2.5).
 rdiff-backup depende de python (<< 2.5).
 rdiff-backup depende de python (>= 2.4).
 rdiff-backup depende de python (<< 2.5).
 rdiff-backup depende de python (>= 2.4).
 gconf2 depende de python.
 python-imaging depende de python (<< 2.5).
 python-imaging depende de python (>= 2.4).
 python-imaging depende de python (<< 2.5).
 python-imaging depende de python (>= 2.4).
 gimp-python depende de python (<< 2.5); sin embargo:
  El paquete `python' va a ser desinstalado.
 gimp-python depende de python (>= 2.4); sin embargo:
  El paquete `python' va a ser desinstalado.
 gimp-python depende de python (<< 2.5); sin embargo:
  El paquete `python' va a ser desinstalado.
 gimp-python depende de python (>= 2.4); sin embargo:
  El paquete `python' va a ser desinstalado.
 python-parted depende de python (>= 2.4).
 python-parted depende de python (<< 2.5).
 python-parted depende de python (>= 2.4).
 python-parted depende de python (<< 2.5).
 python-crypto depende de python (<< 2.5).
 python-crypto depende de python (>= 2.4).
 python-crypto depende de python (<< 2.5).
 python-crypto depende de python (>= 2.4).
 alsa-utils depende de python.
 gdebi depende de python (<< 2.5).
 gdebi depende de python (>= 2.4).
 gdebi depende de python (<< 2.5).
 gdebi depende de python (>= 2.4).
 python-pam depende de python (<< 2.5).
 python-pam depende de python (>= 2.4).
 python-pam depende de python (<< 2.5).
 python-pam depende de python (>= 2.4).
 python-pyopenssl depende de python (<< 2.5).
 python-pyopenssl depende de python (>= 2.4).
 python-pyopenssl depende de python (<< 2.5).
 python-pyopenssl depende de python (>= 2.4).
 python2.4-imaging-sane depende de python (>= 2.4).
 python2.4-imaging-sane depende de python (<< 3).
 python2.4-imaging-sane depende de python (>= 2.4).
 python2.4-imaging-sane depende de python (<< 3).
 python-htmltmpl depende de python (>= 2.4).
 python-htmltmpl depende de python (<< 2.5).
 python-htmltmpl depende de python (>= 2.4).
 python-htmltmpl depende de python (<< 2.5).
 python-central depende de python (>= 2.4.3-10).
 python-gadfly depende de python (<< 2.5).
 python-gadfly depende de python (>= 2.4).
 python-gadfly depende de python (<< 2.5).
 python-gadfly depende de python (>= 2.4).
 python-jabber depende de python (>= 2.4).
 python-jabber depende de python (<< 2.5).
 python-jabber depende de python (>= 2.4).
 python-jabber depende de python (<< 2.5).
 python-xml depende de python (>= 2.4).
 python-xml depende de python (<< 2.5).
 python-xml depende de python (>= 2.4).
 python-xml depende de python (<< 2.5).
 python-ldap depende de python (>= 2.4).
 python-ldap depende de python (<< 2.5).
 python-ldap depende de python (>= 2.4).
 python-ldap depende de python (<< 2.5).
 python-genetic depende de python (<< 2.5).
 python-genetic depende de python (>= 2.4).
 python-genetic depende de python (<< 2.5).
 python-genetic depende de python (>= 2.4).
 deskbar-applet depende de python (<< 2.5).
 deskbar-applet depende de python (>= 2.4).
 deskbar-applet depende de python (<< 2.5).
 deskbar-applet depende de python (>= 2.4).
 unattended-upgrades depende de python.
 python-unit depende de python (<< 2.5).
 python-unit depende de python (>= 2.4).
 python-unit depende de python (<< 2.5).
 python-unit depende de python (>= 2.4).
 python-syck depende de python (<< 2.5).
 python-syck depende de python (>= 2.4).
 python-syck depende de python (<< 2.5).
 python-syck depende de python (>= 2.4).
 konq-plugins depende de python; sin embargo:
  El paquete `python' va a ser desinstalado.
 kde-guidance depende de python (<< 2.5); sin embargo:
  El paquete `python' va a ser desinstalado.
 kde-guidance depende de python (>= 2.4); sin embargo:
  El paquete `python' va a ser desinstalado.
 kde-guidance depende de python (<< 2.5); sin embargo:
  El paquete `python' va a ser desinstalado.
 kde-guidance depende de python (>= 2.4); sin embargo:
  El paquete `python' va a ser desinstalado.
 python-pyao depende de python (<< 2.5).
 python-pyao depende de python (>= 2.4).
 python-pyao depende de python (<< 2.5).
 python-pyao depende de python (>= 2.4).
 python-pyxattr depende de python (<< 2.5).
 python-pyxattr depende de python (>= 2.4).
 python-pyxattr depende de python (<< 2.5).
 python-pyxattr depende de python (>= 2.4).
 python-pyvorbis depende de python (<< 2.5).
 python-pyvorbis depende de python (>= 2.4).
 python-pyvorbis depende de python (<< 2.5).
 python-pyvorbis depende de python (>= 2.4).
 python-sqlite depende de python (<< 2.5).
 python-sqlite depende de python (>= 2.4).
 python-sqlite depende de python (<< 2.5).
 python-sqlite depende de python (>= 2.4).
 python-eunuchs depende de python (<< 2.5).
 python-eunuchs depende de python (>= 2.4).
 python-eunuchs depende de python (<< 2.5).
 python-eunuchs depende de python (>= 2.4).
 python-imaging-sane depende de python (<< 2.5).
 python-imaging-sane depende de python (>= 2.4).
 python-imaging-sane depende de python (<< 2.5).
 python-imaging-sane depende de python (>= 2.4).
 alacarte depende de python (<< 2.5).
 alacarte depende de python (>= 2.4).
 alacarte depende de python (<< 2.5).
 alacarte depende de python (>= 2.4).
 gnome-menus depende de python (<< 2.5).
 gnome-menus depende de python (>= 2.4).
 gnome-menus depende de python (<< 2.5).
 gnome-menus depende de python (>= 2.4).
 wine-doors depende de python.
 python-gmenu depende de python (<< 2.5).
 python-gmenu depende de python (>= 2.4).
 python-gmenu depende de python (<< 2.5).
 python-gmenu depende de python (>= 2.4).
 python-stats depende de python (<< 2.5).
 python-stats depende de python (>= 2.4).
 python-stats depende de python (<< 2.5).
 python-stats depende de python (>= 2.4).
 python-adns depende de python (<< 2.5).
 python-adns depende de python (>= 2.4).
 python-adns depende de python (<< 2.5).
 python-adns depende de python (>= 2.4).
 python-support depende de python (>= 2.4.3-10).
 gnome-doc-utils depende de python (>= 2.4).
 gnome-doc-utils depende de python (<< 3).
 gnome-doc-utils depende de python (>= 2.4).
 gnome-doc-utils depende de python (<< 3).
 python-newt depende de python (<< 2.5).
 python-newt depende de python (>= 2.4).
 python-newt depende de python (<< 2.5).
 python-newt depende de python (>= 2.4).
 python-netcdf depende de python (>= 2.4).
 python-netcdf depende de python (<< 2.5).
 python-netcdf depende de python (>= 2.4).
 python-netcdf depende de python (<< 2.5).
 pykdeextensions depende de python (<< 2.5).
 pykdeextensions depende de python (>= 2.4).
 pykdeextensions depende de python (<< 2.5).
 pykdeextensions depende de python (>= 2.4).
 python-pexpect depende de python (>= 2.4).
 python-pexpect depende de python (<< 2.5).
 python-pexpect depende de python (>= 2.4).
 python-pexpect depende de python (<< 2.5).
 python-epydoc depende de python (<< 2.5).
 python-epydoc depende de python (>= 2.4).
 python-epydoc depende de python (<< 2.5).
 python-epydoc depende de python (>= 2.4).
 python-clientcookie depende de python (<< 2.5).
 python-clientcookie depende de python (>= 2.4).
 python-clientcookie depende de python (<< 2.5).
 python-clientcookie depende de python (>= 2.4).
 bittornado depende de python (<< 2.5).
 bittornado depende de python (>= 2.4).
 bittornado depende de python (<< 2.5).
 bittornado depende de python (>= 2.4).
 python-pisock depende de python (<< 2.5).
 python-pisock depende de python (>= 2.4).
 python-pisock depende de python (<< 2.5).
 python-pisock depende de python (>= 2.4).
 python-gd depende de python (<< 2.5).
 python-gd depende de python (>= 2.4).
 python-gd depende de python (<< 2.5).
 python-gd depende de python (>= 2.4).
 python-egenix-mxtools depende de python (<< 2.5).
 python-egenix-mxtools depende de python (>= 2.4).
 python-egenix-mxtools depende de python (<< 2.5).
 python-egenix-mxtools depende de python (>= 2.4).
 python-egenix-mxproxy depende de python (<< 2.5).
 python-egenix-mxproxy depende de python (>= 2.4).
 python-egenix-mxproxy depende de python (<< 2.5).
 python-egenix-mxproxy depende de python (>= 2.4).
 python-soappy depende de python (>= 2.4).
 python-soappy depende de python (<< 2.5).
 python-soappy depende de python (>= 2.4).
 python-soappy depende de python (<< 2.5).
 lsb-release depende de python.
 python-mysqldb depende de python (>= 2.4).
 python-mysqldb depende de python (<< 2.5).
 python-mysqldb depende de python (>= 2.4).
 python-mysqldb depende de python (<< 2.5).
 python-reportlab depende de python (<< 2.5).
 python-reportlab depende de python (>= 2.4).
 python-reportlab depende de python (<< 2.5).
 python-reportlab depende de python (>= 2.4).
 python-geoip depende de python (<< 2.5).
 python-geoip depende de python (>= 2.4).
 python-geoip depende de python (<< 2.5).
 python-geoip depende de python (>= 2.4).
 python-tk depende de python (<< 2.6).
 python-tk depende de python (>= 2.4).
 python-tk depende de python (<< 2.6).
 python-tk depende de python (>= 2.4).
 python-dbus depende de python (<< 2.6).
 python-dbus depende de python (>= 2.4).
 python-dbus depende de python (<< 2.6).
 python-dbus depende de python (>= 2.4).
 python-pgsql depende de python (>= 2.4).
 python-pgsql depende de python (<< 2.5).
 python-pgsql depende de python (>= 2.4).
 python-pgsql depende de python (<< 2.5).
 python-simpletal depende de python (>= 2.4).
 python-simpletal depende de python (<< 2.5).
 python-simpletal depende de python (>= 2.4).
 python-simpletal depende de python (<< 2.5).
 python-pqueue depende de python (<< 2.5).
 python-pqueue depende de python (>= 2.4).
 python-pqueue depende de python (<< 2.5).
 python-pqueue depende de python (>= 2.4).
 python-pylibacl depende de python (<< 2.5).
 python-pylibacl depende de python (>= 2.4).
 python-pylibacl depende de python (<< 2.5).
 python-pylibacl depende de python (>= 2.4).
dpkg: error al procesar python (--remove):
 problemas de dependencias - no se desinstala
Se encontraron errores al procesar:
 python

la cosa esta algo complicada :lolflag:
lo que si me sirve el comando para eliminar compiz en
gutsy beryl y compiz es lo mismo ahoara como compiz-fusion
otro paquete conflitivo de feisty a gutsy es wine y los extras 
como wine-doors wine-dev libwine por que que wine para feisty
se vuelve dependiente de wine doorss etc... 

alguna otra idea ?

---

### Post by Hei Ku on 2007-11-26
probaste con el metacity?

podes probar al reves tambien, de hacer update del python forzandolo.

sudo dpkg -i --force-conflicts python

pero yo iria por el metacity. total despues la reinstalacion es tirarle el ubuntu-desktop de ultima

---

### Post by nenesio on 2007-11-26
me sirvio fue 

sudo apt-get -f upgrade

bueno son mas de 600 paquetes terminara mañana
luego que termine de esta forma probare 

sudo aptitude dist-upgrade

para asegurar, bueno gracias por la ayuda

---

