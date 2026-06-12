---
title: "actualitzar a natty"
date: 2011-05-03
forum: Catalan Team
---

### Post by quitus on 2011-05-03
Hola, doncs resulta que no puc actualitzar a natty, em dona un error sembla ser de dependències.

Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages

He desinstalat openoffice, i segueix igual...

si algú te alguna idea.

salut

---

### Post by Black_02 on 2011-05-03
Hola, ami em va passar igual, i el vaig instal·lar de zero. També podries provar de baixar la iso i actualitzar-lo des del cd.

---

### Post by Original Flo on 2011-05-03
Si tens la home separada, jo crec que es millor instal·lar sempre de 0.

Les vegades que he fet actualitzacions, sempre he tingut algun problema, de vegades mes gran o de vegades casi sense importància.

Si no tens la /home separada i tens la possibilitat de fer un Back-up de la home en algun disc extern o qualsevol altre suport, pots aprofitar per fer una instal·lació de 0 i aprofitar per posar la /home en una partició separada, aixi per pròximes actualitzacions podràs tornar a fer instal-lacions netes mantenint sempre la home intacta.

---

### Post by wgarcia on 2011-05-04
Jo en canvi vinc actualitzant ordinadors des de la versió Edgy i sempre m'he sortit, sense problemes massa seriosos. Les úniques complicacions que m'he trobat a vegades és amb els mòduls per a les targetes gràfiques, però no m'han impedit actualitzar. 

Quant al problem d'en Quitus, t'ensenya quins són aquesta paquets "held back"? Molt cops fent una "apt-get install" d'aquests paquets se soluciona.

---

### Post by quitus on 2011-05-05
Doncs... no em diu quins paquets son els que tenen problemes amb les dependències, tampoc se com mirar-ho, he provat amb apt-get check però en el terminal no em mostra res, si a generat algun arxiu amb la informació no el se trobar.

---

### Post by wgarcia on 2011-05-05
Has provat

sudo apt-get install -f 

a veure si s'arregla alguna cosa?

---

### Post by quitus on 2011-05-05
si, ja ho vaig provar (ho he tornat a fer per si de cas)

porto 5 dies a estonetes buscant informació i provant coses i res.

salut

---

### Post by kimet on 2011-05-05
Mira si existeix un fitxer /var/log/dist-upgrade o /var/log/apt.

---

### Post by quitus on 2011-05-06
a veure si això pot ajudar aquest es l'arxiu apt.log situat a /var/log/dist-upgrade

---

### Post by quitus on 2011-05-06
```
Log time: 2011-05-05 19:45:34.491610
Log time: 2011-05-05 19:48:59.656985
Log time: 2011-05-05 19:50:49.634565
  Installing xserver-xorg-core as Depends of xserver-xorg
    Installing xserver-common as Depends of xserver-xorg-core
    Installing keyboard-configuration as Depends of xserver-xorg-core
    Installing libgcrypt11 as Depends of xserver-xorg-core
      Installing libgpg-error0 as Depends of libgcrypt11
        Installing multiarch-support as PreDepends of libgpg-error0
          Installing libc6 as Depends of multiarch-support
            Installing libc-bin as Depends of libc6
  Installing python-ubuntuone-client as Depends of ubuntuone-client
    Installing python-ubuntuone-storageprotocol as Depends of python-ubuntuone-client
  Installing gir1.2-unity-3.0 as Depends of ubuntuone-client
    Installing gir1.2-dbusmenu-glib-0.4 as Depends of gir1.2-unity-3.0
      Installing libdbusmenu-glib3 as Depends of gir1.2-dbusmenu-glib-0.4
      Installing gir1.2-glib-2.0 as Depends of gir1.2-dbusmenu-glib-0.4
        Installing libgirepository-1.0-1 as Depends of gir1.2-glib-2.0
        Installing libglib2.0-0 as Depends of gir1.2-glib-2.0
          Installing libpcre3 as Depends of libglib2.0-0
    Installing gir1.2-dee-0.5 as Depends of gir1.2-unity-3.0
      Installing libdee-1.0-1 as Depends of gir1.2-dee-0.5
    Installing libunity4 as Depends of gir1.2-unity-3.0
        Installing libbamf0 as Depends of unity
          Installing bamfdaemon as Depends of libbamf0
        Installing libglew1.5 as Depends of unity
        Installing libglewmx1.5 as Depends of unity
        Installing libglibmm-2.4-1c2a as Depends of unity
        Installing libgtk2.0-0 as Depends of unity
          Installing libpango1.0-0 as Depends of libgtk2.0-0
              Installing libdrm-nouveau1a as Depends of plymouth
              Installing libplymouth2 as Depends of plymouth
              Installing udev as Depends of plymouth
        Installing libindicator3 as Depends of unity
        Installing libnux-0.9-0 as Depends of unity
          Installing libnux-0.9-common as Depends of libnux-0.9-0
        Installing libunity-misc0 as Depends of unity
        Installing libutouch-geis1 as Depends of unity
        Installing unity-common as Depends of unity
        Installing compiz-core as Depends of unity
          previously satisfied important dependency on compiz-plugins
          Installing compiz-plugins as Recommends of compiz-core
            Installing libdecoration0 as Depends of compiz-plugins
            Installing compiz-plugins-extra as Depends of compiz-fusion-plugins-extra
            Installing compiz-plugins-main as Depends of compiz-fusion-plugins-main
              Installing libjpeg62 as Depends of compiz-plugins-main
        Installing nux-tools as Depends of unity
        new important dependency: ubuntuone-control-panel-gtk
        Installing ubuntuone-control-panel-gtk as Recommends of unity
          Installing python as Depends of ubuntuone-control-panel-gtk
            Installing python2.7 as Depends of python
              Installing python2.7-minimal as Depends of python2.7
              Installing libsqlite3-0 as Depends of python2.7
            Installing python-minimal as Depends of python
          Installing python-defer as Depends of ubuntuone-control-panel-gtk
          Installing ubuntu-sso-client as Depends of ubuntuone-control-panel-gtk
          Installing ubuntuone-control-panel as Depends of ubuntuone-control-panel-gtk
            Installing python-ubuntuone-control-panel as Depends of ubuntuone-control-panel
              Installing gir1.2-soup-2.4 as Depends of python-ubuntuone-control-panel
                Installing libsoup2.4-1 as Depends of gir1.2-soup-2.4
                  Installing glib-networking as Depends of libsoup2.4-1
  Installing debconf as PreDepends of popularity-contest
  Installing libappindicator1 as Depends of policykit-1-gnome
    Installing libdbusmenu-gtk3 as Depends of libappindicator1
    previously satisfied important dependency on indicator-application
    Installing indicator-application as Recommends of libappindicator1
      Installing libjson-glib-1.0-0 as Depends of indicator-application
  Installing libpolkit-gobject-1-0 as Depends of policykit-1-gnome
  Installing libpano13-2 as Depends of libpano13-bin
  Installing libgcr0 as Depends of gnome-keyring
  Installing libsane as Depends of libsane-dev
    Installing libgphoto2-2 as Depends of libsane
      Installing libgphoto2-port0 as Depends of libgphoto2-2
  Installing libxapian22 as Depends of qapt-batch
  Installing libdevmapper1.02.1 as Depends of dmsetup
  Installing libasound2 as Depends of gstreamer0.10-alsa
    Installing libpython2.7 as Depends of libasound2
  Installing libgstreamer0.10-0 as Depends of gstreamer0.10-alsa
  Installing libgstreamer-plugins-base0.10-0 as Depends of gstreamer0.10-alsa
  Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing libmlt3 as Depends of melt
    Installing libmlt-data as Recommends of libmlt3
  Installing libkrb5support0 as Depends of libkrb5-3
  Installing libcups2 as Depends of libcups2-dev
  Installing libglib2.0-cil as Depends of gnome-do
  Installing libgtk2.0-cil as Depends of gnome-do
    Installing libgdk-pixbuf2.0-0 as Depends of libgtk2.0-cil
  previously satisfied important dependency on gnome-do-plugins
  Installing gnome-do-plugins as Recommends of gnome-do
    Installing libdbus1.0-cil as Depends of gnome-do-plugins
  Installing libsm6 as Depends of libsm-dev
  Installing libatk1.0-data as Depends of libatk1.0-0
  Installing python-wsgi-intercept as Depends of python-lazr.restfulclient
  Installing libnspr4 as Depends of libpurple0
  Installing libnss3 as Depends of libpurple0
  Installing perl-base as Depends of libpurple0
  Installing liblaunchpad-integration-common as Depends of liblaunchpad-integration1
  Installing syslinux-common as Depends of syslinux
  Installing libavutil50 as Depends of libswscale0
  Installing libkdecore5 as Depends of libkldap4
  Installing libkdeui5 as Depends of libkldap4
    previously satisfied important dependency on kdelibs5-data
    Installing kdelibs5-data as Recommends of libkdeui5
  Installing gcc-4.5-base as Depends of libstdc++6
  Installing libappindicator0.1-cil as Depends of tomboy
  Installing libkabc4 as Depends of libktnef4
    Installing libkio5 as Depends of libkabc4
      Installing libnepomuk4 as Depends of libkio5
        Installing libsoprano4 as Depends of libnepomuk4
          Installing soprano-daemon as Depends of libsoprano4
            Installing librdf0 as Depends of soprano-daemon
      Installing libnepomukutils4 as Depends of libkio5
        Installing libnepomukquery4a as Depends of libnepomukutils4
      Installing libsolid4 as Depends of libkio5
      previously satisfied important dependency on kdelibs5-plugins
      Installing kdelibs5-plugins as Recommends of libkio5
        Installing libkatepartinterfaces4 as Depends of kdelibs5-plugins
          Installing libkcmutils4 as Depends of libkatepartinterfaces4
          Installing libkparts4 as Depends of libkatepartinterfaces4
          Installing libktexteditor4 as Depends of libkatepartinterfaces4
        Installing libkemoticons4 as Depends of kdelibs5-plugins
        Installing libkfile4 as Depends of kdelibs5-plugins
        Installing libkhtml5 as Depends of kdelibs5-plugins
          Installing libkjsapi4 as Depends of libkhtml5
          Installing libphonon4 as Depends of libkhtml5
        Installing libkjsembed4 as Depends of kdelibs5-plugins
        Installing libkntlm4 as Depends of kdelibs5-plugins
        Installing libkrosscore4 as Depends of kdelibs5-plugins
        Installing libpolkit-qt-1-1 as Depends of kdelibs5-plugins
        Installing kdoctools as Depends of kdelibs5-plugins
        Installing kdelibs-bin as Depends of kdelibs5-plugins
    Installing libkresources4 as Depends of libkabc4
  Installing libkcal4 as Depends of libktnef4
    Installing libkpimutils4 as Depends of libkcal4
      Installing libkmime4 as Depends of libkpimutils4
  Installing libkcalcore4 as Depends of libktnef4
  Installing libkcalutils4 as Depends of libktnef4
  Installing python-twisted-bin as Depends of python-twisted-core
  Installing libbz2-1.0 as Depends of bzip2
  Installing libedataserver1.2-14 as Depends of evolution-webcal
  Installing libespeak1 as Depends of espeak
    Installing espeak-data as Depends of libespeak1
  Installing libnih1 as Depends of libnih-dbus1
  Installing computer-janitor as Depends of computer-janitor-gtk
  Installing python-gobject as Depends of computer-janitor-gtk
  Installing gir1.2-gtk-2.0 as Depends of computer-janitor-gtk
    Installing gir1.2-atk-1.0 as Depends of gir1.2-gtk-2.0
    Installing gir1.2-freedesktop as Depends of gir1.2-gtk-2.0
    Installing gir1.2-gdkpixbuf-2.0 as Depends of gir1.2-gtk-2.0
    Installing gir1.2-pango-1.0 as Depends of gir1.2-gtk-2.0
  Installing libakonadi-kabc4 as Depends of kdepim-runtime
  Installing libakonadi-kcal4 as Depends of kdepim-runtime
  Installing libakonadi-kde4 as Depends of kdepim-runtime
    Installing libakonadiprotocolinternals1 as Depends of libakonadi-kde4
  Installing libakonadi-kmime4 as Depends of kdepim-runtime
  Installing libkimap4 as Depends of kdepim-runtime
  Installing libmailtransport4 as Depends of kdepim-runtime
  Installing libmicroblog4 as Depends of kdepim-runtime
  Installing python-couchdb as Depends of python-desktopcouch-records
      Installing python-desktopcouch-application as Depends of desktopcouch
  Installing libqtcore4 as Depends of libqt4-opengl
  Installing libqtgui4 as Depends of libqt4-opengl
    new important dependency: appmenu-qt
    Installing appmenu-qt as Recommends of libqtgui4
  new important dependency: gwibber-service-facebook
  Installing gwibber-service-facebook as Recommends of gwibber-service
  new important dependency: gwibber-service-twitter
  Installing gwibber-service-twitter as Recommends of gwibber-service
  new important dependency: gwibber-service-identica
  Installing gwibber-service-identica as Recommends of gwibber-service
  Installing language-pack-kde-ca as Depends of language-pack-kde-ca-base
    Installing language-pack-ca-base as Depends of language-pack-kde-ca
      Installing language-pack-ca as Depends of language-pack-ca-base
  new important dependency: libalgorithm-diff-xs-perl
  Installing libalgorithm-diff-xs-perl as Recommends of libalgorithm-diff-perl
  Installing libexiv2-10 as Depends of gthumb
  Installing gthumb-data as Depends of gthumb
  new important dependency: gstreamer0.10-gnomevfs
  Installing gstreamer0.10-gnomevfs as Recommends of gthumb
  Installing hplip as Depends of hplip-gui
    Installing libhpmud0 as Depends of hplip
    Installing libsane-hpaio as Depends of hplip
    Installing hplip-data as Depends of hplip
    Installing hplip-cups as Depends of hplip
  Installing libutouch-grail1 as Depends of xserver-xorg-input-evdev
    Installing libmtdev1 as Depends of libutouch-grail1
    Installing libutouch-evemu1 as Depends of libutouch-grail1
    Installing libutouch-frame1 as Depends of libutouch-grail1
  Installing libice6 as Depends of libice-dev
  Installing kdegraphics-libs-data as Depends of libksane0
  Installing update-manager-core as Depends of update-manager
  Installing gir1.0-atk-1.0 as Depends of gnome-shell
  Installing gir1.0-freedesktop as Depends of gnome-shell
  Installing gir1.0-gdkpixbuf-2.0 as Depends of gnome-shell
  Installing gir1.0-glib-2.0 as Depends of gnome-shell
  Installing gir1.0-gtk-2.0 as Depends of gnome-shell
  Installing gir1.0-pango-1.0 as Depends of gnome-shell
  Installing libgirepository1.0-1 as Depends of gnome-shell
  Installing bzr as Depends of bzrtools
    Installing python-bzrlib as Depends of bzr
  Installing python-gnomecanvas as Depends of python-gnome2
  Installing python-gtk2 as Depends of python-gnome2
    Installing python-cairo as Depends of python-gtk2
  Installing python-pyorbit as Depends of python-gnome2
  Installing python-gconf as Depends of python-gnome2
  Installing libqt4-network as Depends of libqt4-declarative
    Installing libqt4-dbus as Depends of libqt4-network
      Installing libqt4-xml as Depends of libqt4-dbus
  Installing libqt4-script as Depends of libqt4-declarative
  Installing libqt4-sql as Depends of libqt4-declarative
  Installing libqt4-xmlpatterns as Depends of libqt4-declarative
  Installing libicu44 as Depends of libboost-regex1.42.0
  Installing gnome-media-common as Depends of gnome-media
  Installing libindicator1 as Depends of libunity0
  Installing libtasn1-3 as Depends of libtasn1-3-dev
  Installing gnome-games-common as Depends of aisleriot
  Installing libbind9-60 as Depends of bind9-host
    Installing libdns69 as Depends of libbind9-60
      Installing libgeoip1 as Depends of libdns69
      Installing libisc62 as Depends of libdns69
    Installing libisccfg62 as Depends of libbind9-60
  Installing liblwres60 as Depends of bind9-host
  Installing libindicate5 as Depends of pidgin-libnotify
  Installing language-pack-en as Depends of language-pack-en-base
  Installing libgamin0 as Depends of gamin
  Installing gvfs as Depends of gvfs-fuse
  Installing dpkg-dev as Depends of debhelper
    Installing libdpkg-perl as Depends of dpkg-dev
  Installing linux-headers-2.6.38-9-generic as Depends of linux-headers-generic
    Installing linux-headers-2.6.38-9 as Depends of linux-headers-2.6.38-9-generic
  Installing isc-dhcp-client as Depends of dhcp3-client
    Installing isc-dhcp-common as Depends of isc-dhcp-client
  Installing gnucash-common as Depends of gnucash
  Installing libaqbanking33 as Depends of gnucash
    Installing libgwenhywfar60 as Depends of libaqbanking33
      Installing libgwenhywfar-data as Depends of libgwenhywfar60
    Installing libaqbanking-data as Depends of libaqbanking33
    Installing libaqbanking33-plugins as Recommends of libaqbanking33
      Installing libaqhbci19 as Depends of libaqbanking33-plugins
      Installing libaqofxconnect7 as Depends of libaqbanking33-plugins
    Installing libaqbanking-plugins-libgwenhywfar60 as Recommends of libaqbanking33
  Installing libgwengui-gtk2-0 as Depends of gnucash
  Installing libwebkitgtk-1.0-0 as Depends of gnucash
    Installing libwebkitgtk-1.0-common as Depends of libwebkitgtk-1.0-0
  Installing libreoffice-core as Depends of libreoffice-base
    Installing libhyphen0 as Depends of libreoffice-core
    Installing libneon27-gnutls as Depends of libreoffice-core
    Installing libtextcat0 as Depends of libreoffice-core
      Installing libtextcat-data as Depends of libtextcat0
  Installing libreoffice-base-core as Depends of libreoffice-base
  Installing xsane-common as Depends of xsane
  Installing libaudio2 as Depends of libaudio-dev
  Installing libpam-modules-bin as PreDepends of libpam-modules
  Installing libgcj-common as Depends of libgcj-bc
  Installing libgcj11 as Depends of libgcj-bc
    Installing gcj-4.5-base as Depends of libgcj11
    Installing gcj-4.5-jre-lib as Recommends of libgcj11
  Installing libxine1-bin as Depends of libxine1-x
  Installing libcupsimage2 as Depends of libcupsimage2-dev
  Installing libsnmp-base as Depends of libsnmp15
  Installing amule-common as Depends of amule
  Installing libbrasero-media1 as Depends of brasero-cdrkit
  Installing libdjvulibre-text as Depends of libdjvulibre21
  Installing perl as Depends of libyaml-syck-perl
    Installing perl-modules as Depends of perl
  Installing libcamel1.2-19 as Depends of evolution-indicator
      Installing libebackend1.2-0 as Depends of evolution
      Installing libebook1.2-10 as Depends of evolution
      Installing libecal1.2-8 as Depends of evolution
        Installing libgdata11 as Depends of libecal1.2-8
      Installing libedataserverui1.2-11 as Depends of evolution
      Installing libegroupwise1.2-13 as Depends of evolution
      Installing libevolution as Depends of evolution
      Installing evolution-data-server as Depends of evolution
        Installing libedata-book1.2-8 as Depends of evolution-data-server
        Installing libedata-cal1.2-10 as Depends of evolution-data-server
        Installing evolution-data-server-common as Depends of evolution-data-server
  Installing samba-common as Depends of smbclient
  Installing libvorbis0a as Depends of libvorbisfile3
  Installing libgucharmap7 as Depends of gucharmap
  Installing libatspi1.0-0 as Depends of brltty-x11
  Installing brltty as Depends of brltty-x11
  Installing gir1.2-clutter-1.0 as Depends of libseed0
    Installing gir1.2-json-glib-1.0 as Depends of gir1.2-clutter-1.0
    Installing libclutter-1.0-0 as Depends of gir1.2-clutter-1.0
      new important dependency: libclutter-1.0-common
      Installing libclutter-1.0-common as Recommends of libclutter-1.0-0
  Installing gir1.2-gstreamer-0.10 as Depends of libseed0
  Installing libqtwebkit4 as Depends of libqtwebkit-dev
  Installing upstart as Depends of avahi-daemon
  Installing libxcb-shm0 as Depends of libxcb-shm0-dev
  Installing icedtea-plugin as Depends of icedtea6-plugin
    Installing icedtea-netx as Depends of icedtea-plugin
  Installing cheese-common as Depends of cheese
  Installing grub-pc as Depends of grub2
    Installing grub-common as Depends of grub-pc
    Installing grub-gfxpayload-lists as Depends of grub-pc
  Installing gdebi-core as Depends of gdebi
    Installing python-apt as Depends of gdebi-core
      Installing apt as Depends of python-apt
      Installing python-apt-common as Depends of python-apt
  Installing libimobiledevice2 as Depends of upower
  Installing libpulse0 as Depends of libpulse-dev
  Installing libpulse-mainloop-glib0 as Depends of libpulse-dev
  Installing libpulse-browse0 as Depends of libpulse-dev
  Installing libtdb1 as Depends of pulseaudio
  Installing libclamav6 as Depends of clamav
  new important dependency: gnome-user-share
  Installing gnome-user-share as Recommends of gnome-bluetooth
    Installing libnotify4 as Depends of gnome-user-share
  Installing libgs9 as Depends of libspectre1
    Installing libjbig2dec0 as Depends of libgs9
    Installing libgs9-common as Depends of libgs9
    Installing gs-cjk-resource as Depends of libgs9
      Installing cmap-adobe-japan1 as Recommends of gs-cjk-resource
  Installing python-aptdaemon.gtkwidgets as Depends of python-aptdaemon-gtk
    Installing python-aptdaemon as Depends of python-aptdaemon.gtkwidgets
    Installing aptdaemon-data as Depends of python-aptdaemon.gtkwidgets
  Installing python-aptdaemon.gtk3widgets as Depends of python-aptdaemon-gtk
    Installing gir1.2-vte-0.0 as Depends of python-aptdaemon.gtk3widgets
  Installing language-pack-kde-en-base as Depends of language-pack-kde-en
  Installing libgladeui-1-11 as Depends of libgnome-media0
  Installing libzeitgeist-1.0-1 as Depends of unity-place-applications
  Installing zeitgeist-extension-fts as Depends of unity-place-applications
  Installing liblvm2app2.2 as Depends of udisks
    Installing libdevmapper-event1.02.1 as Depends of liblvm2app2.2
  Installing gcc-4.4-base as Depends of g++-4.4
  Installing gcc-4.4 as Depends of g++-4.4
    Installing cpp-4.4 as Depends of gcc-4.4
    previously satisfied important dependency on libc6-dev
    Installing libc6-dev as Recommends of gcc-4.4
      Installing libc-dev-bin as Depends of libc6-dev
  Installing libstdc++6-4.4-dev as Depends of g++-4.4
  Installing libatkmm-1.6-1 as Depends of gparted
      Installing libpangomm-1.4-1 as Depends of libgtkmm-2.4-1c2a
  Installing libcurl3-gnutls as Depends of python-pycurl
  Installing totem as Depends of totem-plugins
    previously satisfied important dependency on totem-mozilla
    Installing totem-mozilla as Recommends of totem
  Installing libkidletime4 as Depends of kdebase-runtime
  Installing libntrack-qt4-1 as Depends of kdebase-runtime
    Installing libntrack0 as Depends of libntrack-qt4-1
      Installing ntrack-module-libnl-0 as Depends of libntrack0
  Installing libplasma3 as Depends of kdebase-runtime
    Installing libkdewebkit5 as Depends of libplasma3
    Installing libkdnssd4 as Depends of libplasma3
    Installing libknewstuff3-4 as Depends of libplasma3
      Installing libattica0 as Depends of libknewstuff3-4
    Installing libthreadweaver4 as Depends of libplasma3
  Installing kdebase-runtime-data as Depends of kdebase-runtime
  Installing plasma-scriptengine-javascript as Depends of kdebase-runtime
  Installing plasma-scriptengine-declarative as Depends of kdebase-runtime
  new important dependency: thunderbird-globalmenu
  Installing thunderbird-globalmenu as Recommends of thunderbird
  Installing clamav-base as Depends of clamav-freshclam
  Installing libsdl-image1.2 as Depends of libsdl-image1.2-dev
  Installing libtotem-plparser17 as Depends of rhythmbox
    Installing libquvi0 as Depends of libtotem-plparser17
  Installing libgssdp-1.0-2 as Depends of libgstfarsight0.10-0
  Installing libgupnp-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libnice10 as Depends of libgstfarsight0.10-0
  Installing libx264-106 as Depends of gstreamer0.10-plugins-ugly-multiverse
  Installing libkde3support4 as Depends of kdelibs5
    Installing libkpty4 as Depends of libkde3support4
  Installing libkdesu5 as Depends of kdelibs5
  Installing libkmediaplayer4 as Depends of kdelibs5
  Installing libknewstuff2-4 as Depends of kdelibs5
  Installing libknotifyconfig4 as Depends of kdelibs5
  Installing libkrossui4 as Depends of kdelibs5
  Installing libkutils4 as Depends of kdelibs5
    Installing libkprintutils4 as Depends of libkutils4
  Installing python-gmenu as Depends of gnome-menus
  Installing libnewt0.52 as Depends of python-newt
  Installing growisofs as Depends of dvd+rw-tools
  Installing libprotoc6 as Depends of protobuf-compiler
  Installing libmysqlclient16 as Depends of mysql-client-core-5.1
    Installing mysql-common as Depends of libmysqlclient16
  previously satisfied important dependency on virtualbox-ose-dkms
  Installing virtualbox-ose-dkms as Recommends of virtualbox-ose
  previously satisfied important dependency on virtualbox-ose-qt
  Installing virtualbox-ose-qt as Recommends of virtualbox-ose
  Installing libgmp3c2 as Depends of libgmp3-dev
  Installing libgmpxx4ldbl as Depends of libgmp3-dev
  Installing cups-common as Depends of cups-client
  Installing linux-image-2.6.38-9-generic-pae as Depends of linux-image-generic-pae
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libwebkit-1.0-common as Depends of libwebkit-1.0-2
  Installing libqt4-designer as Depends of libqt4-qt3support
  Installing libbluray0 as Depends of mplayer
  Installing language-pack-gnome-en as Depends of language-pack-gnome-en-base
  Installing libgnome-window-settings1 as Depends of gnome-control-center
  Installing capplets-data as Depends of gnome-control-center
  Installing libsasl2-2 as Depends of libsasl2-modules
  Installing gir1.2-gnomegamessupport-1.0 as Depends of lightsoff
  Installing gir1.2-gconf-2.0 as Depends of lightsoff
  Installing gir1.2-clutter-gtk-0.10 as Depends of lightsoff
  Installing libxi6 as Depends of libxi-dev
  Installing x11proto-input-dev as Depends of libxi-dev
  Installing xorg-sgml-doctools as Depends of libxi-dev
  Installing gconf2-common as Depends of gconf2
  Installing language-selector-gnome as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing language-selector-common as Depends of language-selector-gnome
    Installing aptdaemon as Depends of language-selector-gnome
      new important dependency: lintian
      Installing lintian as Recommends of aptdaemon
        Installing diffstat as Depends of lintian
        Installing libapt-pkg-perl as Depends of lintian
        Installing libemail-valid-perl as Depends of lintian
          Installing libnet-domain-tld-perl as Depends of libemail-valid-perl
        Installing libipc-run-perl as Depends of lintian
          Installing libio-pty-perl as Depends of libipc-run-perl
  Installing rfkill as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: banshee-extension-ubuntuonemusicstore
  Installing banshee-extension-ubuntuonemusicstore as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libubuntuone1.0-cil as Depends of banshee-extension-ubuntuonemusicstore
  new important dependency: ginn
  Installing ginn as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: libreoffice-help-en-us
  Installing libreoffice-help-en-us as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: overlay-scrollbar
  Installing overlay-scrollbar as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing liboverlay-scrollbar-0.1-0 as Depends of overlay-scrollbar
  Installing libqt4-dev as Depends of libqt4-opengl-dev
    Installing libqt4-svg as Depends of libqt4-dev
    Installing libqt4-scripttools as Depends of libqt4-dev
    Installing libqt4-help as Depends of libqt4-dev
    Installing qt4-qmake as Depends of libqt4-dev
  Installing libfolks-telepathy22 as Depends of empathy
    Installing libfolks22 as Depends of libfolks-telepathy22
  Installing libtelepathy-logger2 as Depends of empathy
  Installing empathy-common as Depends of empathy
  Installing gnome-pilot as Depends of gnome-pilot-conduits
  Installing libgtkhtml-editor-common as Depends of libgtkhtml-editor0
  Installing libcairo2 as Depends of libcairo2-dev
  Installing libcairo-gobject2 as Depends of libcairo2-dev
  Installing libcairo-script-interpreter2 as Depends of libcairo2-dev
  Installing python2.7-dev as Depends of python-dev
  Installing libawn1 as Depends of python-awn
  Installing fontconfig-config as Depends of libfontconfig1
  Installing libpanel-applet-3-0 as Depends of indicator-applet
  Installing python-reportlab as Depends of python-reportlab-accel
  Installing libsvn1 as Depends of subversion
  Installing libxdmcp6 as Depends of libxdmcp-dev
  Installing krb5-multidev as Depends of libkrb5-dev
    Installing libk5crypto3 as Depends of krb5-multidev
    Installing libgssapi-krb5-2 as Depends of krb5-multidev
    Installing libgssrpc4 as Depends of krb5-multidev
    Installing libkadm5srv-mit7 as Depends of krb5-multidev
  Installing openjdk-6-jre-headless as Depends of icedtea-6-jre-cacao
    Installing openjdk-6-jre-lib as Depends of openjdk-6-jre-headless
    new important dependency: icedtea-6-jre-jamvm
    Installing icedtea-6-jre-jamvm as Recommends of openjdk-6-jre-headless
  Installing cpp as Depends of g++
    Installing cpp-4.5 as Depends of cpp
      Installing libcloog-ppl0 as Depends of cpp-4.5
        Installing libppl-c2 as Depends of libcloog-ppl0
          Installing libppl7 as Depends of libppl-c2
      Installing libelfg0 as Depends of cpp-4.5
      Installing libmpc2 as Depends of cpp-4.5
  Installing gcc as Depends of g++
    Installing gcc-4.5 as Depends of gcc
      Installing libgcc1 as Depends of gcc-4.5
  Installing g++-4.5 as Depends of g++
    Installing libstdc++6-4.5-dev as Depends of g++-4.5
  Installing libavahi-client3 as Depends of libavahi-client-dev
  Installing libparted0debian1 as Depends of libparted0
  Installing libbluetooth3 as Depends of bluez
    Installing libsoundtouch0 as Depends of gstreamer0.10-plugins-bad
    Installing libwildmidi1 as Depends of gstreamer0.10-plugins-bad
  Installing libgtk-sharp-beans-cil as Depends of banshee
  previously satisfied important dependency on banshee-extension-soundmenu
  Installing banshee-extension-soundmenu as Recommends of banshee
  Installing libavcodec52 as Depends of libavformat52
  Installing e2fslibs as PreDepends of e2fsprogs
  Installing libpng12-0 as Depends of libpng12-dev
  Installing libwpd-0.9-9 as Depends of libreoffice-writer
  Installing libwpg-0.2-2 as Depends of libreoffice-writer
  Installing libwps-0.2-2 as Depends of libreoffice-writer
  Installing libkonq5a as Depends of dolphin
  Installing gcj-4.4-base as Depends of gcj-4.4-jre-lib
  Installing libgcj10 as Depends of gcj-4.4-jre-lib
  previously satisfied important dependency on telepathy-mission-control-5
  Installing telepathy-mission-control-5 as Recommends of libmission-control-plugins0
  Installing libm17n-0 as Depends of m17n-db
  Installing msr-tools as Depends of cpu-checker
  Installing mount as Depends of libfuse2
  Installing amsn-data as Depends of amsn
  Installing libasyncns0 as Depends of libloudmouth1-0
  Installing libmozjs185-1.0 as Depends of couchdb-bin
  Installing libdb4.7-java as Depends of libdb4.7-java-gcj
  Installing libkdcraw9 as Depends of kipi-plugins
  Installing libkexiv2-9 as Depends of kipi-plugins
  Installing libkipi8 as Depends of kipi-plugins
  Installing libqjson0 as Depends of kipi-plugins
  Installing kipi-plugins-common as Depends of kipi-plugins
  Installing libphononexperimental4 as Depends of libphonon-dev
  Installing python-piston-mini-client as Depends of software-center
  Installing python-ubuntuone as Depends of rhythmbox-ubuntuone-music-store
    Installing libubuntuone-1.0-1 as Depends of python-ubuntuone
  Installing rhythmbox-plugins as Depends of rhythmbox-ubuntuone-music-store
  Installing libxcursor1 as Depends of libxcursor-dev
  Installing python-sip as Depends of python-qt3
  Installing at-spi as Depends of python-pyatspi
  Installing libxmlrpc-core-c3-0 as Depends of cmake
  Installing libexif12 as Depends of libexif-dev
  Installing libgpgme++2 as Depends of libqgpgme1
  Installing gnome-session-bin as Depends of gnome3-session
  Installing python-compizconfig as Depends of compizconfig-settings-manager
  Installing libebml3 as Depends of vlc-nox
  Installing libmatroska3 as Depends of vlc-nox
  Installing speech-dispatcher as Depends of python-speechd
  Installing libreadline6-dev as Depends of libreadline-dev
    Installing libreadline6 as Depends of libreadline6-dev
  Installing hugin-tools as Depends of hugin
  Installing libgjs0b as Depends of gjs
    Installing xulrunner-2.0-mozjs as Depends of libgjs0b
  Installing libdrm-nouveau1 as Depends of libdrm-dev
  Installing libmarblewidget11 as Depends of digikam
    Installing marble-data as Depends of libmarblewidget11
    Installing marble-plugins as Recommends of libmarblewidget11
      Installing libgps19 as Depends of marble-plugins
  Installing digikam-data as Depends of digikam
  Installing libssl0.9.8 as Depends of libssl-dev
  Installing usb-creator-common as Depends of usb-creator-gtk
  Installing libnm-glib-vpn1 as Depends of libnm-glib2
  Installing libxt6 as Depends of libxt-dev
  Installing stellarium-data as Depends of stellarium
  Installing avant-window-navigator-data as Depends of avant-window-navigator
  new important dependency: dockmanager
  Installing dockmanager as Recommends of avant-window-navigator
    Installing python-mpd as Depends of dockmanager
  new important dependency: awn-applet-animal-farm
  Installing awn-applet-animal-farm as Recommends of avant-window-navigator
  new important dependency: awn-applet-awn-notification-daemon
  Installing awn-applet-awn-notification-daemon as Recommends of avant-window-navigator
  new important dependency: awn-applet-awn-system-monitor
  Installing awn-applet-awn-system-monitor as Recommends of avant-window-navigator
  new important dependency: awn-applet-awnterm
  Installing awn-applet-awnterm as Recommends of avant-window-navigator
  new important dependency: awn-applet-bandwidth-monitor
  Installing awn-applet-bandwidth-monitor as Recommends of avant-window-navigator
  new important dependency: awn-applet-battery-applet
  Installing awn-applet-battery-applet as Recommends of avant-window-navigator
  new important dependency: awn-applet-cairo-clock
  Installing awn-applet-cairo-clock as Recommends of avant-window-navigator
  new important dependency: awn-applet-cairo-main-menu
  Installing awn-applet-cairo-main-menu as Recommends of avant-window-navigator
  new important dependency: awn-applet-comics
  Installing awn-applet-comics as Recommends of avant-window-navigator
  new important dependency: awn-applet-common-folder
  Installing awn-applet-common-folder as Recommends of avant-window-navigator
  new important dependency: awn-applet-cpufreq
  Installing awn-applet-cpufreq as Recommends of avant-window-navigator
  new important dependency: awn-applet-dialect
  Installing awn-applet-dialect as Recommends of avant-window-navigator
  new important dependency: awn-applet-feeds
  Installing awn-applet-feeds as Recommends of avant-window-navigator
  new important dependency: awn-applet-file-browser-launcher
  Installing awn-applet-file-browser-launcher as Recommends of avant-window-navigator
  new important dependency: awn-applet-garbage
  Installing awn-applet-garbage as Recommends of avant-window-navigator
  new important dependency: awn-applet-hardware-sensors
  Installing awn-applet-hardware-sensors as Recommends of avant-window-navigator
  new important dependency: awn-applet-indicator
  Installing awn-applet-indicator as Recommends of avant-window-navigator
  new important dependency: awn-applet-mail
  Installing awn-applet-mail as Recommends of avant-window-navigator
  new important dependency: awn-applet-media-control
  Installing awn-applet-media-control as Recommends of avant-window-navigator
  new important dependency: awn-applet-media-icon-applet
  Installing awn-applet-media-icon-applet as Recommends of avant-window-navigator
  new important dependency: awn-applet-media-player
  Installing awn-applet-media-player as Recommends of avant-window-navigator
  new important dependency: awn-applet-notification-area
  Installing awn-applet-notification-area as Recommends of avant-window-navigator
  new important dependency: awn-applet-quit-applet
  Installing awn-applet-quit-applet as Recommends of avant-window-navigator
  new important dependency: awn-applet-related
  Installing awn-applet-related as Recommends of avant-window-navigator
  new important dependency: awn-applet-shinyswitcher
  Installing awn-applet-shinyswitcher as Recommends of avant-window-navigator
  new important dependency: awn-applet-showdesktop
  Installing awn-applet-showdesktop as Recommends of avant-window-navigator
  new important dependency: awn-applet-stack
  Installing awn-applet-stack as Recommends of avant-window-navigator
  new important dependency: awn-applet-thinkhdaps
  Installing awn-applet-thinkhdaps as Recommends of avant-window-navigator
  new important dependency: awn-applet-todo
  Installing awn-applet-todo as Recommends of avant-window-navigator
  new important dependency: awn-applet-volume-control
  Installing awn-applet-volume-control as Recommends of avant-window-navigator
  new important dependency: awn-applet-weather
  Installing awn-applet-weather as Recommends of avant-window-navigator
  new important dependency: awn-applet-webapplet
  Installing awn-applet-webapplet as Recommends of avant-window-navigator
  Installing tzdata as Depends of tzdata-java
  Installing libgwibber1 as Depends of indicator-me
  Installing libxext6 as Depends of libxext-dev
  Installing gsettings-desktop-schemas as Depends of mousetweaks
  previously satisfied important dependency on usb-modeswitch
  Installing usb-modeswitch as Recommends of usb-modeswitch-data
  Installing libavdevice52 as Depends of ffmpeg
  Installing libavfilter1 as Depends of ffmpeg
  Installing libpoppler13 as Depends of cups
  Installing libudev0 as Depends of libgudev-1.0-0
  Installing libbonobo2-common as Depends of libbonobo2-0
  Installing zlib1g as Depends of zlib1g-dev
  Installing libsmpeg0 as Depends of libsmpeg-dev
  Installing libpoppler-glib6 as Depends of libevdocument3
  Installing cuyo-data as Depends of cuyo
  Installing libmagic1 as Depends of file
  Installing libtiff4 as Depends of libtiff4-dev
  Installing libtiffxx0c2 as Depends of libtiff4-dev
  Installing libfreetype6 as Depends of libfreetype6-dev
  Installing libmono-system-data-linq2.0-cil as Depends of libmono-system-web2.0-cil
  Installing python-keyring as Depends of python-launchpadlib
  Installing libwbclient0 as Depends of samba
  new important dependency: libfile-mimeinfo-perl
  Installing libfile-mimeinfo-perl as Recommends of xdg-utils
    Installing libfile-basedir-perl as Depends of libfile-mimeinfo-perl
    Installing libfile-desktopentry-perl as Depends of libfile-mimeinfo-perl
  new important dependency: ecryptfs-utils
  Installing ecryptfs-utils as Recommends of adduser
    Installing libecryptfs0 as Depends of ecryptfs-utils
    Installing keyutils as Depends of ecryptfs-utils
  Installing libsyndication4 as Depends of libkblog4
  Installing libgeoclue0 as Depends of indicator-datetime
  Installing geoclue-ubuntu-geoip as Depends of indicator-datetime
    Installing geoclue as Depends of geoclue-ubuntu-geoip
  Installing libstreams0 as Depends of libstreamanalyzer0
  Installing mono-gmcs as Depends of mono-csharp-shell
  Installing libperl-dev as Depends of libsnmp-dev
    Installing libperl5.10 as Depends of libperl-dev
  previously satisfied important dependency on vlc-plugin-notify
  Installing vlc-plugin-notify as Recommends of vlc
  previously satisfied important dependency on vlc-plugin-pulse
  Installing vlc-plugin-pulse as Recommends of vlc
  Installing yelp-xsl as Depends of yelp
  Installing libkholidays4 as Depends of kdepimlibs5
  Installing kdepimlibs-kio-plugins as Depends of kdepimlibs5
  Installing libxrandr2 as Depends of libxrandr-dev
  Installing python-ibus as Depends of ibus
  Installing libslang2 as Depends of libslang2-dev
  Installing ncurses-bin as Depends of libncurses5-dev
  Installing gnome-applets-data as Depends of gnome-applets
  Installing gir1.2-panelapplet-3.0 as Depends of gnome-applets
  previously satisfied important dependency on ktorrent
  Installing ktorrent as Recommends of ktorrent-data
  Installing gir1.2-notify-0.7 as Depends of jockey-gtk
  Installing gir1.2-appindicator-0.1 as Depends of jockey-gtk
  Installing libpipeline1 as Depends of man-db
  Installing python-papyon as Depends of telepathy-butterfly
  Installing gnome-panel-data as Depends of gnome-panel
  new important dependency: indicator-applet-complete
  Installing indicator-applet-complete as Recommends of gnome-panel
    Installing indicator-sound as Recommends of indicator-applet-complete
  new important dependency: indicator-applet-appmenu
  Installing indicator-applet-appmenu as Recommends of gnome-panel
  new important dependency: gnome-panel-bonobo
  Installing gnome-panel-bonobo as Recommends of gnome-panel
  Installing python-desktopcouch-recordtypes as Depends of python-desktopcouch
  Installing libavahi-common3 as Depends of libavahi-common-dev
  Installing linux-headers-2.6.38-9-generic-pae as Depends of linux-headers-generic-pae
  Installing libxinerama1 as Depends of libxinerama-dev
  Installing libltdl7 as Depends of libltdl-dev
  new important dependency: ssh-import-id
  Installing ssh-import-id as Recommends of openssh-server
  Installing kdebase-workspace-bin as Depends of kde-window-manager
    Installing libcln6 as Depends of kdebase-workspace-bin
    Installing libkephal4a as Depends of kdebase-workspace-bin
    Installing libkscreensaver5 as Depends of kdebase-workspace-bin
    Installing libplasmagenericshell4 as Depends of kdebase-workspace-bin
    Installing libpowerdevilcore0 as Depends of kdebase-workspace-bin
    Installing libprocesscore4b as Depends of kdebase-workspace-bin
    Installing libprocessui4a as Depends of kdebase-workspace-bin
    Installing libqalculate5 as Depends of kdebase-workspace-bin
    Installing libsolidcontrolifaces4a as Depends of kdebase-workspace-bin
  Installing libnfnetlink0 as Depends of iptables
  Installing language-pack-gnome-ca-base as Depends of language-pack-gnome-ca
  Installing libgnomeprintui2.2-common as Depends of libgnomeprintui2.2-0
  Installing libcanberra-gtk3-0 as Depends of mutter
    Installing libgtk-3-0 as Depends of libcanberra-gtk3-0
      Installing libgtk-3-common as Depends of libgtk-3-0
      Installing libgtk-3-bin as Recommends of libgtk-3-0
    Installing libcanberra-gtk3-module as Recommends of libcanberra-gtk3-0
  Installing libmutter0 as Depends of mutter
Starting
Starting 2
Investigating (0) gir1.2-glib-2.0 [ i386 ] < none -> 0.10.7-0ubuntu1 > ( libs )
Broken gir1.2-glib-2.0:i386 Conflicts on gir1.0-glib-2.0 [ i386 ] < 0.9.3-0ubuntu4 > ( libs )
  Considering gir1.0-glib-2.0:i386 23 as a solution to gir1.2-glib-2.0:i386 112
  Added gir1.0-glib-2.0:i386 to the remove list
  Fixing gir1.2-glib-2.0:i386 via remove of gir1.0-glib-2.0:i386
Investigating (0) libgirepository-1.0-1 [ i386 ] < none -> 0.10.7-0ubuntu1 > ( libs )
Broken libgirepository-1.0-1:i386 Conflicts on libgirepository1.0-1 [ i386 ] < 0.9.3-0ubuntu4 > ( libs )
  Considering libgirepository1.0-1:i386 15 as a solution to libgirepository-1.0-1:i386 91
  Added libgirepository1.0-1:i386 to the remove list
  Fixing libgirepository-1.0-1:i386 via remove of libgirepository1.0-1:i386
Investigating (0) xserver-xorg-core [ i386 ] < 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick -> 2:1.10.1-1ubuntu1 > ( x11 )
Broken xserver-xorg-core:i386 Breaks on xserver-xorg-video-8 [ i386 ] < none > ( none )
  Considering xserver-xorg-video-tseng:i386 -1 as a solution to xserver-xorg-core:i386 68
  Added xserver-xorg-video-tseng:i386 to the remove list
  Fixing xserver-xorg-core:i386 via remove of xserver-xorg-video-tseng:i386
Investigating (0) libindicator3 [ i386 ] < none -> 0.3.22-0ubuntu1 > ( libs )
Broken libindicator3:i386 Breaks on libindicator1 [ i386 ] < 0.3.14-0ubuntu1 > ( libs ) (<= 0.3.22-0ubuntu1)
  Considering libindicator1:i386 3 as a solution to libindicator3:i386 53
  Added libindicator1:i386 to the remove list
  Fixing libindicator3:i386 via remove of libindicator1:i386
Investigating (0) gir1.2-gtk-2.0 [ i386 ] < none -> 2.24.4-0ubuntu2 > ( libs )
Broken gir1.2-gtk-2.0:i386 Conflicts on gir1.0-gtk-2.0 [ i386 ] < 2.22.0-0ubuntu1 > ( libs )
  Considering gir1.0-gtk-2.0:i386 3 as a solution to gir1.2-gtk-2.0:i386 33
  Added gir1.0-gtk-2.0:i386 to the remove list
  Fixing gir1.2-gtk-2.0:i386 via remove of gir1.0-gtk-2.0:i386
Investigating (0) gir1.2-freedesktop [ i386 ] < none -> 0.10.7-0ubuntu1 > ( libs )
Broken gir1.2-freedesktop:i386 Conflicts on gir1.0-freedesktop [ i386 ] < 0.9.3-0ubuntu4 > ( libs )
  Considering gir1.0-freedesktop:i386 13 as a solution to gir1.2-freedesktop:i386 31
  Added gir1.0-freedesktop:i386 to the remove list
  Fixing gir1.2-freedesktop:i386 via remove of gir1.0-freedesktop:i386
Investigating (0) python-desktop-agnostic [ i386 ] < 0.3.93~bzr405+201103161905~maverick1 > ( universe/python )
Broken python-desktop-agnostic:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to python-desktop-agnostic:i386 28
  Removing python-desktop-agnostic:i386 rather than change python:i386
Investigating (0) gnome-user-guide [ i386 ] < 2.30.0+git20100403ubuntu2 -> 3.0.0+git20110406ubuntu9 > ( gnome )
Broken gnome-user-guide:i386 Conflicts on gnome-user-guide-ca [ i386 ] < 2.30.0+git20100403ubuntu2 > ( gnome ) (< 2.91.90+git20110306ubuntu1)
  Considering gnome-user-guide-ca:i386 -1 as a solution to gnome-user-guide:i386 28
  Added gnome-user-guide-ca:i386 to the remove list
Broken gnome-user-guide:i386 Conflicts on gnome-user-guide-en [ i386 ] < 2.30.0+git20100403ubuntu2 > ( gnome ) (< 2.91.90+git20110306ubuntu1)
  Considering gnome-user-guide-en:i386 -1 as a solution to gnome-user-guide:i386 28
  Added gnome-user-guide-en:i386 to the remove list
  Fixing gnome-user-guide:i386 via remove of gnome-user-guide-ca:i386
  Fixing gnome-user-guide:i386 via remove of gnome-user-guide-en:i386
Investigating (0) gir1.2-gdkpixbuf-2.0 [ i386 ] < none -> 2.23.3-0ubuntu1 > ( libs )
Broken gir1.2-gdkpixbuf-2.0:i386 Conflicts on gir1.0-gdkpixbuf-2.0 [ i386 ] < 2.22.0-0ubuntu1 > ( libs )
  Considering gir1.0-gdkpixbuf-2.0:i386 5 as a solution to gir1.2-gdkpixbuf-2.0:i386 25
  Added gir1.0-gdkpixbuf-2.0:i386 to the remove list
  Fixing gir1.2-gdkpixbuf-2.0:i386 via remove of gir1.0-gdkpixbuf-2.0:i386
Investigating (0) gir1.2-pango-1.0 [ i386 ] < none -> 1.28.4-0ubuntu1 > ( libs )
Broken gir1.2-pango-1.0:i386 Conflicts on gir1.0-pango-1.0 [ i386 ] < 1.28.2-0ubuntu1.1 > ( libs )
  Considering gir1.0-pango-1.0:i386 7 as a solution to gir1.2-pango-1.0:i386 25
  Added gir1.0-pango-1.0:i386 to the remove list
  Fixing gir1.2-pango-1.0:i386 via remove of gir1.0-pango-1.0:i386
Investigating (0) gir1.2-atk-1.0 [ i386 ] < none -> 2.0.0-0ubuntu1 > ( libs )
Broken gir1.2-atk-1.0:i386 Conflicts on gir1.0-atk-1.0 [ i386 ] < 1.32.0-0ubuntu1 > ( libs )
  Considering gir1.0-atk-1.0:i386 5 as a solution to gir1.2-atk-1.0:i386 23
  Added gir1.0-atk-1.0:i386 to the remove list
  Fixing gir1.2-atk-1.0:i386 via remove of gir1.0-atk-1.0:i386
Investigating (0) libimobiledevice2 [ i386 ] < none -> 1.1.0-3 > ( libs )
Broken libimobiledevice2:i386 Conflicts on libimobiledevice1 [ i386 ] < 1.0.1-1 > ( libs )
  Considering libimobiledevice1:i386 -1 as a solution to libimobiledevice2:i386 18
  Added libimobiledevice1:i386 to the remove list
  Fixing libimobiledevice2:i386 via remove of libimobiledevice1:i386
Investigating (0) libdrm-nouveau1a [ i386 ] < none -> 2.4.23-1ubuntu6 > ( libs )
Broken libdrm-nouveau1a:i386 Breaks on libdrm-nouveau1 [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libs )
  Considering libdrm-nouveau1:i386 5 as a solution to libdrm-nouveau1a:i386 12
  Added libdrm-nouveau1:i386 to the remove list
  Fixing libdrm-nouveau1a:i386 via remove of libdrm-nouveau1:i386
Investigating (0) libwebkitgtk-1.0-common [ i386 ] < none -> 1.3.13-0ubuntu2 > ( libs )
Broken libwebkitgtk-1.0-common:i386 Conflicts on libwebkit-1.0-common [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs )
  Considering libwebkit-1.0-common:i386 0 as a solution to libwebkitgtk-1.0-common:i386 12
  Added libwebkit-1.0-common:i386 to the remove list
  Fixing libwebkitgtk-1.0-common:i386 via remove of libwebkit-1.0-common:i386
Investigating (0) awn-settings [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/gnome )
Broken awn-settings:i386 Depends on python-desktop-agnostic [ i386 ] < 0.3.93~bzr405+201103161905~maverick1 > ( universe/python )
  Considering python-desktop-agnostic:i386 28 as a solution to awn-settings:i386 10
  Removing awn-settings:i386 rather than change python-desktop-agnostic:i386
Investigating (0) python-gnomeprint [ i386 ] < 2.30.0-0ubuntu1 > ( python )
Broken python-gnomeprint:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to python-gnomeprint:i386 9
  Removing python-gnomeprint:i386 rather than change python:i386
Investigating (0) libakonadiprotocolinternals1 [ i386 ] < none -> 1.5.2-0ubuntu1 > ( libs )
Broken libakonadiprotocolinternals1:i386 Breaks on libakonadiprivate1 [ i386 ] < 1.4.0-0ubuntu1 > ( libs )
  Considering libakonadiprivate1:i386 -2 as a solution to libakonadiprotocolinternals1:i386 9
  Added libakonadiprivate1:i386 to the remove list
  Fixing libakonadiprotocolinternals1:i386 via remove of libakonadiprivate1:i386
Investigating (0) gir1.2-gconf-2.0 [ i386 ] < none -> 2.32.2-0ubuntu2 > ( libs )
Broken gir1.2-gconf-2.0:i386 Conflicts on gir1.0-gconf-2.0 [ i386 ] < 2.31.91-0ubuntu3.1 > ( libs )
  Considering gir1.0-gconf-2.0:i386 1 as a solution to gir1.2-gconf-2.0:i386 7
  Added gir1.0-gconf-2.0:i386 to the remove list
  Fixing gir1.2-gconf-2.0:i386 via remove of gir1.0-gconf-2.0:i386
Investigating (0) gir1.2-clutter-1.0 [ i386 ] < none -> 1.6.14-0ubuntu3 > ( libs )
Broken gir1.2-clutter-1.0:i386 Conflicts on gir1.0-clutter-1.0 [ i386 ] < 1.2.12-0ubuntu13 > ( libs )
  Considering gir1.0-clutter-1.0:i386 3 as a solution to gir1.2-clutter-1.0:i386 7
  Added gir1.0-clutter-1.0:i386 to the remove list
  Fixing gir1.2-clutter-1.0:i386 via remove of gir1.0-clutter-1.0:i386
Investigating (0) libpolkit-qt-1-1 [ i386 ] < none -> 0.99.0-0ubuntu3 > ( libs )
Broken libpolkit-qt-1-1:i386 Conflicts on libpolkit-qt-1-0 [ i386 ] < 0.95.1-1ubuntu1 > ( libs ) (<= 0.99.0-0ubuntu1)
  Considering libpolkit-qt-1-0:i386 -2 as a solution to libpolkit-qt-1-1:i386 7
  Added libpolkit-qt-1-0:i386 to the remove list
Broken libpolkit-qt-1-1:i386 Breaks on libpolkit-qt-1-0 [ i386 ] < 0.95.1-1ubuntu1 > ( libs ) (<= 0.99.0-0ubuntu1)
  Considering libpolkit-qt-1-0:i386 -2 as a solution to libpolkit-qt-1-1:i386 7
  Added libpolkit-qt-1-0:i386 to the remove list
  Fixing libpolkit-qt-1-1:i386 via remove of libpolkit-qt-1-0:i386
  Fixing libpolkit-qt-1-1:i386 via remove of libpolkit-qt-1-0:i386
Investigating (0) libmlt3 [ i386 ] < none -> 0.6.2-2 > ( universe/libs )
Broken libmlt3:i386 Conflicts on libmlt2 [ i386 ] < 0.5.6+git20100727-1 > ( libs )
  Considering libmlt2:i386 -1 as a solution to libmlt3:i386 7
  Added libmlt2:i386 to the remove list
  Fixing libmlt3:i386 via remove of libmlt2:i386
Investigating (0) libgladeui-1-11 [ i386 ] < none -> 3.8.0-0ubuntu1 > ( libdevel )
Broken libgladeui-1-11:i386 Conflicts on libgladeui-1-9 [ i386 ] < 3.7.0.is.3.6.7-0ubuntu2 > ( libdevel )
  Considering libgladeui-1-9:i386 -1 as a solution to libgladeui-1-11:i386 5
  Added libgladeui-1-9:i386 to the remove list
  Fixing libgladeui-1-11:i386 via remove of libgladeui-1-9:i386
Investigating (0) gir1.2-json-glib-1.0 [ i386 ] < none -> 0.12.2-0ubuntu1 > ( libs )
Broken gir1.2-json-glib-1.0:i386 Conflicts on gir1.0-json-glib-1.0 [ i386 ] < 0.10.2-2ubuntu2.1 > ( libs )
  Considering gir1.0-json-glib-1.0:i386 5 as a solution to gir1.2-json-glib-1.0:i386 5
  Holding Back gir1.2-json-glib-1.0:i386 rather than change gir1.0-json-glib-1.0:i386
Investigating (0) libkonq5a [ i386 ] < none -> 4:4.6.2-0ubuntu1 > ( libs )
Broken libkonq5a:i386 Conflicts on libkonq5 [ i386 ] < 4:4.5.5-0ubuntu2 > ( libs )
  Considering libkonq5:i386 -1 as a solution to libkonq5a:i386 5
  Added libkonq5:i386 to the remove list
  Fixing libkonq5a:i386 via remove of libkonq5:i386
Investigating (0) wine1.2-gecko [ i386 ] < 1.0.0-0ubuntu4 -> 1.0.0+1 > ( multiverse/otherosfs )
Broken wine1.2-gecko:i386 Conflicts on wine-gecko [ i386 ] < 1.2.2-1ubuntu1~maverick2 > ( multiverse/otherosfs )
  Considering wine-gecko:i386 -2 as a solution to wine1.2-gecko:i386 5
  Added wine-gecko:i386 to the remove list
  Conflicts//Breaks against version 1.2.2-0ubuntu4 for wine-gecko but that is not InstVer, ignoring
  Fixing wine1.2-gecko:i386 via remove of wine-gecko:i386
Investigating (0) gir1.0-json-glib-1.0 [ i386 ] < 0.10.2-2ubuntu2.1 > ( libs )
Broken gir1.0-json-glib-1.0:i386 Depends on gir1.0-glib-2.0 [ i386 ] < 0.9.3-0ubuntu4 > ( libs )
  Considering gir1.0-glib-2.0:i386 23 as a solution to gir1.0-json-glib-1.0:i386 5
  Removing gir1.0-json-glib-1.0:i386 rather than change gir1.0-glib-2.0:i386
Investigating (0) awn-applet-awn-notification-daemon [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-awn-notification-daemon:i386 Breaks on awn-applets-c-core [ i386 ] < 0.4.0+bzr1372-0ubuntu3 > ( gnome ) (< 0.4.1~bzr1485-0ubuntu1)
  Considering awn-applets-c-core:i386 -1 as a solution to awn-applet-awn-notification-daemon:i386 4
  Added awn-applets-c-core:i386 to the remove list
  Fixing awn-applet-awn-notification-daemon:i386 via remove of awn-applets-c-core:i386
Investigating (0) awn-applet-volume-control [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-volume-control:i386 Breaks on awn-applets-python-core [ i386 ] < 0.4.0+bzr1372-0ubuntu3 > ( gnome ) (< 0.4.1~bzr1485-0ubuntu1)
  Considering awn-applets-python-core:i386 1 as a solution to awn-applet-volume-control:i386 4
  Added awn-applets-python-core:i386 to the remove list
  Fixing awn-applet-volume-control:i386 via remove of awn-applets-python-core:i386
Investigating (0) marble-data [ i386 ] < 4:4.5.5-0ubuntu2 -> 4:4.6.2-0ubuntu2 > ( misc )
Broken marble-data:i386 Conflicts on libmarblewidget10 [ i386 ] < 4:4.5.5-0ubuntu2 > ( libs )
  Considering libmarblewidget10:i386 -1 as a solution to marble-data:i386 4
  Added libmarblewidget10:i386 to the remove list
  Fixing marble-data:i386 via remove of libmarblewidget10:i386
Investigating (0) awn-applet-media-icon-applet [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-media-icon-applet:i386 Breaks on awn-applets-python-extras [ i386 ] < 0.4.0+bzr1372-0ubuntu3 > ( gnome ) (< 0.4.1~bzr1485-0ubuntu1)
  Considering awn-applets-python-extras:i386 -1 as a solution to awn-applet-media-icon-applet:i386 4
  Added awn-applets-python-extras:i386 to the remove list
  Fixing awn-applet-media-icon-applet:i386 via remove of awn-applets-python-extras:i386
Investigating (0) libkephal4a [ i386 ] < none -> 4:4.6.2a-0ubuntu5.1 > ( libs )
Broken libkephal4a:i386 Conflicts on libkephal4 [ i386 ] < 4:4.5.5-0ubuntu2.1 > ( libs )
  Considering libkephal4:i386 -1 as a solution to libkephal4a:i386 3
  Added libkephal4:i386 to the remove list
  Fixing libkephal4a:i386 via remove of libkephal4:i386
Investigating (0) gir1.2-clutter-gtk-0.10 [ i386 ] < none -> 0.10.8-1ubuntu1 > ( libs )
Broken gir1.2-clutter-gtk-0.10:i386 Depends on gir1.2-json-glib-1.0 [ i386 ] < none -> 0.12.2-0ubuntu1 > ( libs )
  Considering gir1.2-json-glib-1.0:i386 5 as a solution to gir1.2-clutter-gtk-0.10:i386 3
  Holding Back gir1.2-clutter-gtk-0.10:i386 rather than change gir1.2-json-glib-1.0:i386
Investigating (0) nvidia-common [ i386 ] < 0.2.24 -> 0.2.30 > ( x11 )
Broken nvidia-common:i386 Conflicts on nvidia-185-modaliases [ i386 ] < 260.19.29-0ubuntu1~xup1~maverick > ( admin )
  Considering nvidia-185-modaliases:i386 -1 as a solution to nvidia-common:i386 3
  Added nvidia-185-modaliases:i386 to the remove list
Broken nvidia-common:i386 Conflicts on nvidia-current-modaliases [ i386 ] < 260.19.29-0ubuntu1~xup1~maverick > ( admin )
  Considering nvidia-current-modaliases:i386 1 as a solution to nvidia-common:i386 3
  Added nvidia-current-modaliases:i386 to the remove list
  Fixing nvidia-common:i386 via remove of nvidia-185-modaliases:i386
  Fixing nvidia-common:i386 via remove of nvidia-current-modaliases:i386
Investigating (0) gir1.2-gstreamer-0.10 [ i386 ] < none -> 0.10.32-3ubuntu3 > ( libs )
Broken gir1.2-gstreamer-0.10:i386 Conflicts on gir1.0-gstreamer-0.10 [ i386 ] < 0.10.30-1build2 > ( libs )
  Considering gir1.0-gstreamer-0.10:i386 -1 as a solution to gir1.2-gstreamer-0.10:i386 1
  Added gir1.0-gstreamer-0.10:i386 to the remove list
  Fixing gir1.2-gstreamer-0.10:i386 via remove of gir1.0-gstreamer-0.10:i386
Investigating (0) python-mlt2 [ i386 ] < 0.5.6+git20100727-1 > ( python )
Broken python-mlt2:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to python-mlt2:i386 1
  Removing python-mlt2:i386 rather than change python:i386
Investigating (0) xserver-xorg-input-mouse [ i386 ] < 1:1.6.99+git20101204.6b5a82e4-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-input-mouse:i386 Depends on xorg-input-abi-11.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-input-mouse:i386 1
  Removing xserver-xorg-input-mouse:i386 rather than change xorg-input-abi-11.0:i386
Investigating (0) xserver-xorg-video-r128 [ i386 ] < 6.8.1+git20101204.3de85360-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-r128:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-r128:i386 1
  Removing xserver-xorg-video-r128:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) libwebkit-1.0-2 [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs )
Broken libwebkit-1.0-2:i386 Depends on libwebkit-1.0-common [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs ) (>= 1.2.5)
  Considering libwebkit-1.0-common:i386 0 as a solution to libwebkit-1.0-2:i386 1
  Added libwebkit-1.0-common:i386 to the remove list
  Fixing libwebkit-1.0-2:i386 via keep of libwebkit-1.0-common:i386
Investigating (0) lightsoff [ i386 ] < 1:2.32.0-0ubuntu1 -> 1:2.32.1-0ubuntu5 > ( universe/games )
Broken lightsoff:i386 Depends on gir1.2-clutter-gtk-0.10 [ i386 ] < none -> 0.10.8-1ubuntu1 > ( libs )
  Considering gir1.2-clutter-gtk-0.10:i386 3 as a solution to lightsoff:i386 1
  Removing lightsoff:i386 rather than change gir1.2-clutter-gtk-0.10:i386
Investigating (0) xserver-xorg-video-mach64 [ i386 ] < 6.8.2+git20101204.d60087f0-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-mach64:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-mach64:i386 1
  Removing xserver-xorg-video-mach64:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) swell-foop [ i386 ] < 1:2.32.0-0ubuntu1 -> 1:2.32.1-0ubuntu5 > ( universe/games )
Broken swell-foop:i386 Depends on gir1.2-clutter-gtk-0.10 [ i386 ] < none -> 0.10.8-1ubuntu1 > ( libs )
  Considering gir1.2-clutter-gtk-0.10:i386 3 as a solution to swell-foop:i386 1
  Removing swell-foop:i386 rather than change gir1.2-clutter-gtk-0.10:i386
Investigating (0) xserver-xorg-input-synaptics [ i386 ] < 1:1.2.99+git20100610.a489ec15-0ubuntu0sarvatt2 > ( x11 )
Broken xserver-xorg-input-synaptics:i386 Depends on xorg-input-abi-11.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-input-synaptics:i386 1
  Removing xserver-xorg-input-synaptics:i386 rather than change xorg-input-abi-11.0:i386
Investigating (0) xserver-xorg-video-radeon [ i386 ] < 1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-radeon:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-radeon:i386 1
  Removing xserver-xorg-video-radeon:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) gnome-games [ i386 ] < 1:2.32.0-0ubuntu1 -> 1:2.32.1-0ubuntu5 > ( universe/gnome )
Broken gnome-games:i386 Depends on lightsoff [ i386 ] < 1:2.32.0-0ubuntu1 -> 1:2.32.1-0ubuntu5 > ( universe/games )
  Considering lightsoff:i386 1 as a solution to gnome-games:i386 0
  Removing gnome-games:i386 rather than change lightsoff:i386
Investigating (0) libdrm-dev [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libdevel )
Broken libdrm-dev:i386 Depends on libdrm-nouveau1 [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libs ) (= 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick)
  Considering libdrm-nouveau1:i386 5 as a solution to libdrm-dev:i386 0
  Removing libdrm-dev:i386 rather than change libdrm-nouveau1:i386
Investigating (0) libsolidcontrolifaces4a [ i386 ] < none -> 4:4.6.2a-0ubuntu5.1 > ( libs )
Broken libsolidcontrolifaces4a:i386 Conflicts on libsolidcontrolifaces4 [ i386 ] < 4:4.5.5-0ubuntu2.1 > ( libs )
  Considering libsolidcontrolifaces4:i386 -1 as a solution to libsolidcontrolifaces4a:i386 0
  Added libsolidcontrolifaces4:i386 to the remove list
  Fixing libsolidcontrolifaces4a:i386 via remove of libsolidcontrolifaces4:i386
Investigating (0) libxmlrpc-core-c3-0 [ i386 ] < none -> 1.16.32-0ubuntu3 > ( libs )
Broken libxmlrpc-core-c3-0:i386 Conflicts on libxmlrpc-core-c3 [ i386 ] < 1.06.27-1ubuntu7 > ( libs )
  Considering libxmlrpc-core-c3:i386 -1 as a solution to libxmlrpc-core-c3-0:i386 0
  Added libxmlrpc-core-c3:i386 to the remove list
  Fixing libxmlrpc-core-c3-0:i386 via remove of libxmlrpc-core-c3:i386
Investigating (0) libgjs0a [ i386 ] < 0.7.1-1ubuntu4 > ( libs )
Broken libgjs0a:i386 Depends on libgirepository1.0-1 [ i386 ] < 0.9.3-0ubuntu4 > ( libs ) (>= 0.6.14)
  Considering libgirepository1.0-1:i386 15 as a solution to libgjs0a:i386 0
  Removing libgjs0a:i386 rather than change libgirepository1.0-1:i386
Investigating (0) xserver-xorg-video-rendition [ i386 ] < 1:4.2.4+git20101204.541d1193-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-rendition:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-rendition:i386 -1
  Removing xserver-xorg-video-rendition:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) openshot [ i386 ] < 1.3.0-maverick1 > ( universe/video )
Broken openshot:i386 Depends on python-mlt3 [ i386 ] < none -> 0.6.2-2 > ( universe/python )
  Considering python-mlt3:i386 1 as a solution to openshot:i386 -1
  Try Installing python-mlt3 [ i386 ] < none -> 0.6.2-2 > ( universe/python ) before changing openshot:i386
Investigating (0) gnome-shell [ i386 ] < 2.31.5-2ubuntu2 > ( gnome )
Broken gnome-shell:i386 Depends on gir1.0-atk-1.0 [ i386 ] < 1.32.0-0ubuntu1 > ( libs )
  Considering gir1.0-atk-1.0:i386 5 as a solution to gnome-shell:i386 -1
  Removing gnome-shell:i386 rather than change gir1.0-atk-1.0:i386
Investigating (0) libunity0 [ i386 ] < 0.2.46-0ubuntu5 > ( libs )
Broken libunity0:i386 Depends on libindicator1 [ i386 ] < 0.3.14-0ubuntu1 > ( libs )
  Considering libindicator1:i386 3 as a solution to libunity0:i386 -1
  Removing libunity0:i386 rather than change libindicator1:i386
Investigating (0) xserver-xorg-video-s3virge [ i386 ] < 1:1.10.4+git20101204.a568407e-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-s3virge:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-s3virge:i386 -1
  Removing xserver-xorg-video-s3virge:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-apm [ i386 ] < 1:1.2.3+git20101204.6f8a776f-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-apm:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-apm:i386 -1
  Removing xserver-xorg-video-apm:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-ark [ i386 ] < 1:0.7.3+git20101204.5013a760-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-ark:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-ark:i386 -1
  Removing xserver-xorg-video-ark:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-ati [ i386 ] < 1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-ati:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-ati:i386 -1
  Removing xserver-xorg-video-ati:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-tdfx [ i386 ] < 1:1.4.3+git20101204.0c4ffbec-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-tdfx:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-tdfx:i386 -1
  Removing xserver-xorg-video-tdfx:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-trident [ i386 ] < 1:1.3.4+git20101204.de79bbea-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-trident:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-trident:i386 -1
  Removing xserver-xorg-video-trident:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) libmutter-private0 [ i386 ] < 2.31.5-0ubuntu9 > ( libs )
Broken libmutter-private0:i386 Depends on libgirepository1.0-1 [ i386 ] < 0.9.3-0ubuntu4 > ( libs ) (>= 0.6.3)
  Considering libgirepository1.0-1:i386 15 as a solution to libmutter-private0:i386 -1
  Removing libmutter-private0:i386 rather than change libgirepository1.0-1:i386
Investigating (0) ubuntu-tweak [ i386 ] < 0.5.12-1~maverick1 > ( utils )
Broken ubuntu-tweak:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to ubuntu-tweak:i386 -1
  Removing ubuntu-tweak:i386 rather than change python:i386
Investigating (0) xserver-xorg-video-fbdev [ i386 ] < 1:0.4.2+git20100707.7ec9d466-0ubuntu0sarvatt > ( x11 )
Broken xserver-xorg-video-fbdev:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-fbdev:i386 -1
  Removing xserver-xorg-video-fbdev:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-vesa [ i386 ] < 1:2.3.0+git20101204.fba7f460-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-vesa:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-vesa:i386 -1
  Removing xserver-xorg-video-vesa:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-siliconmotion [ i386 ] < 1:1.7.4+git20101204.903aac1d-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-siliconmotion:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-siliconmotion:i386 -1
  Removing xserver-xorg-video-siliconmotion:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-sis [ i386 ] < 1:0.10.3+git20101204.b3368984-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-sis:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-sis:i386 -1
  Removing xserver-xorg-video-sis:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-s3 [ i386 ] < 1:0.6.3+git20101204.bc10d3ac-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-s3:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-s3:i386 -1
  Removing xserver-xorg-video-s3:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-nv [ i386 ] < 1:2.1.18+git20101204.95108089-0ubuntu0sarvatt~maverick > ( universe/x11 )
Broken xserver-xorg-video-nv:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-nv:i386 -1
  Removing xserver-xorg-video-nv:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-savage [ i386 ] < 1:2.3.2+git20101205.cdfbd967-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-savage:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-savage:i386 -1
  Removing xserver-xorg-video-savage:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) lutris [ i386 ] < 0.2.4 > ( games )
Broken lutris:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to lutris:i386 -1
  Removing lutris:i386 rather than change python:i386
Investigating (0) xserver-xorg-video-i128 [ i386 ] < 1:1.3.4+git20101204.b9e0edbd-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-i128:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-i128:i386 -1
  Removing xserver-xorg-video-i128:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-neomagic [ i386 ] < 1:1.2.5+git20101204.a9d69f6d-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-neomagic:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-neomagic:i386 -1
  Removing xserver-xorg-video-neomagic:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-chips [ i386 ] < 1:1.2.3+git20101204.5830fed3-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-chips:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-chips:i386 -1
  Removing xserver-xorg-video-chips:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-voodoo [ i386 ] < 1:1.2.4+git20101204.614ccdf6-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-voodoo:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-voodoo:i386 -1
  Removing xserver-xorg-video-voodoo:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) gir1.0-clutter-gtk-0.10 [ i386 ] < 0.10.4-1ubuntu3 > ( libs )
Broken gir1.0-clutter-gtk-0.10:i386 Depends on gir1.0-atk-1.0 [ i386 ] < 1.32.0-0ubuntu1 > ( libs )
  Considering gir1.0-atk-1.0:i386 5 as a solution to gir1.0-clutter-gtk-0.10:i386 -1
  Removing gir1.0-clutter-gtk-0.10:i386 rather than change gir1.0-atk-1.0:i386
Investigating (0) xserver-xorg-video-i740 [ i386 ] < 1:1.3.2+git20101204.87da594b-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-i740:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-i740:i386 -1
  Removing xserver-xorg-video-i740:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-sisusb [ i386 ] < 1:0.9.4+git20101204.471636ec-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-sisusb:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-sisusb:i386 -1
  Removing xserver-xorg-video-sisusb:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-cirrus [ i386 ] < 1:1.3.2+git20101204.e4f80ffd-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-cirrus:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-cirrus:i386 -1
  Removing xserver-xorg-video-cirrus:i386 rather than change xorg-video-abi-8.0:i386
Investigating (0) xserver-xorg-video-intel [ i386 ] < 2:2.14.0+git20110220.9599fde6-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-video-intel:i386 Depends on xorg-video-abi-8.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-video-intel:i386 -1
  Removing xserver-xorg-video-intel:i386 rather than change xorg-video-abi-8.0:i386
Investigating (1) libgl1-mesa-dri [ i386 ] < 7.11.0+git20110222.7aeb610f-0ubuntu0sarvatt~maverick > ( libs )
Broken libgl1-mesa-dri:i386 Depends on libdrm-nouveau1 [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libs ) (>= 2.4.21-1)
  Considering libdrm-nouveau1:i386 5 as a solution to libgl1-mesa-dri:i386 107
  Added libdrm-nouveau1:i386 to the remove list
  Fixing libgl1-mesa-dri:i386 via keep of libdrm-nouveau1:i386
Investigating (1) xserver-xorg-core [ i386 ] < 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick -> 2:1.10.1-1ubuntu1 > ( x11 )
Broken xserver-xorg-core:i386 Breaks on xserver-xorg-video-8 [ i386 ] < none > ( none )
  Conflicts//Breaks against version 1:1.2.4+git20101204.a1232852-0ubuntu0sarvatt~maverick for xserver-xorg-video-tseng but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.7.4+git20101204.903aac1d-0ubuntu0sarvatt~maverick for xserver-xorg-video-siliconmotion but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick for xserver-xorg-video-ati but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.3.2+git20101204.87da594b-0ubuntu0sarvatt~maverick for xserver-xorg-video-i740 but that is not InstVer, ignoring
  Conflicts//Breaks against version 2.11.11-1~maverick1 for xserver-xorg-video-geode but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:2.1.18+git20101204.95108089-0ubuntu0sarvatt~maverick for xserver-xorg-video-nv but that is not InstVer, ignoring
  Conflicts//Breaks against version 6.8.2+git20101204.d60087f0-0ubuntu0sarvatt~maverick for xserver-xorg-video-mach64 but that is not InstVer, ignoring
  Conflicts//Breaks against version 2:2.14.0+git20110220.9599fde6-0ubuntu0sarvatt~maverick for xserver-xorg-video-intel but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.2.3+git20101204.5830fed3-0ubuntu0sarvatt~maverick for xserver-xorg-video-chips but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.3.4+git20101204.de79bbea-0ubuntu0sarvatt~maverick for xserver-xorg-video-trident but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:0.6.3+git20101204.bc10d3ac-0ubuntu0sarvatt~maverick for xserver-xorg-video-s3 but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.3.4+git20101204.b9e0edbd-0ubuntu0sarvatt~maverick for xserver-xorg-video-i128 but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.4.13+git20101204.f7a2ef60-0ubuntu0sarvatt~maverick for xserver-xorg-video-mga but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.2.5+git20101204.a9d69f6d-0ubuntu0sarvatt~maverick for xserver-xorg-video-neomagic but that is not InstVer, ignoring
  Conflicts//Breaks against version 6.8.1+git20101204.3de85360-0ubuntu0sarvatt~maverick for xserver-xorg-video-r128 but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.3.2+git20101204.e4f80ffd-0ubuntu0sarvatt~maverick for xserver-xorg-video-cirrus but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:0.7.3+git20101204.5013a760-0ubuntu0sarvatt~maverick for xserver-xorg-video-ark but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.4.3+git20101204.0c4ffbec-0ubuntu0sarvatt~maverick for xserver-xorg-video-tdfx but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:0.9.4+git20101204.471636ec-0ubuntu0sarvatt~maverick for xserver-xorg-video-sisusb but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:4.2.4+git20101204.541d1193-0ubuntu0sarvatt~maverick for xserver-xorg-video-rendition but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:2.3.0+git20101204.fba7f460-0ubuntu0sarvatt~maverick for xserver-xorg-video-vesa but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:0.4.2+git20100707.7ec9d466-0ubuntu0sarvatt for xserver-xorg-video-fbdev but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:2.3.2+git20101205.cdfbd967-0ubuntu0sarvatt~maverick for xserver-xorg-video-savage but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick for xserver-xorg-video-radeon but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:11.0.2+git20101004.083a663b-0ubuntu0sarvatt2 for xserver-xorg-video-vmware but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:0.2.904+svn842-0ubuntu1 for xserver-xorg-video-openchrome but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.10.4+git20101204.a568407e-0ubuntu0sarvatt~maverick for xserver-xorg-video-s3virge but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.2.4+git20101204.614ccdf6-0ubuntu0sarvatt~maverick for xserver-xorg-video-voodoo but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:1.2.3+git20101204.6f8a776f-0ubuntu0sarvatt~maverick for xserver-xorg-video-apm but that is not InstVer, ignoring
  Conflicts//Breaks against version 1:0.10.3+git20101204.b3368984-0ubuntu0sarvatt~maverick for xserver-xorg-video-sis but that is not InstVer, ignoring
  Considering xserver-xorg-video-v4l:i386 -1 as a solution to xserver-xorg-core:i386 68
  Added xserver-xorg-video-v4l:i386 to the remove list
  Fixing xserver-xorg-core:i386 via remove of xserver-xorg-video-v4l:i386
Investigating (1) python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python )
Broken python-awn:i386 Depends on python-desktop-agnostic [ i386 ] < 0.3.93~bzr405+201103161905~maverick1 > ( universe/python )
  Considering python-desktop-agnostic:i386 28 as a solution to python-awn:i386 29
  Added python-desktop-agnostic:i386 to the remove list
  Fixing python-awn:i386 via keep of python-desktop-agnostic:i386
Investigating (1) python-desktop-agnostic [ i386 ] < 0.3.93~bzr405+201103161905~maverick1 > ( universe/python )
Broken python-desktop-agnostic:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to python-desktop-agnostic:i386 28
  Removing python-desktop-agnostic:i386 rather than change python:i386
Investigating (1) libdrm-nouveau1a [ i386 ] < none -> 2.4.23-1ubuntu6 > ( libs )
Broken libdrm-nouveau1a:i386 Breaks on libdrm-nouveau1 [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libs )
  Considering libdrm-nouveau1:i386 5 as a solution to libdrm-nouveau1a:i386 12
  Added libdrm-nouveau1:i386 to the remove list
  Fixing libdrm-nouveau1a:i386 via remove of libdrm-nouveau1:i386
Investigating (1) libwebkitgtk-1.0-common [ i386 ] < none -> 1.3.13-0ubuntu2 > ( libs )
Broken libwebkitgtk-1.0-common:i386 Conflicts on libwebkit-1.0-common [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs )
  Considering libwebkit-1.0-common:i386 0 as a solution to libwebkitgtk-1.0-common:i386 12
  Added libwebkit-1.0-common:i386 to the remove list
  Fixing libwebkitgtk-1.0-common:i386 via remove of libwebkit-1.0-common:i386
Investigating (1) python-gnome2-desktop [ i386 ] < 2.30.0-0ubuntu1 > ( python )
Broken python-gnome2-desktop:i386 Depends on python-gnomeprint [ i386 ] < 2.30.0-0ubuntu1 > ( python ) (>= 2.30.0-0ubuntu1)
  Considering python-gnomeprint:i386 9 as a solution to python-gnome2-desktop:i386 12
  Added python-gnomeprint:i386 to the remove list
  Fixing python-gnome2-desktop:i386 via keep of python-gnomeprint:i386
Investigating (1) python-gnomeprint [ i386 ] < 2.30.0-0ubuntu1 > ( python )
Broken python-gnomeprint:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to python-gnomeprint:i386 9
  Removing python-gnomeprint:i386 rather than change python:i386
Investigating (1) gir1.2-clutter-1.0 [ i386 ] < none -> 1.6.14-0ubuntu3 > ( libs )
Broken gir1.2-clutter-1.0:i386 Depends on gir1.2-json-glib-1.0 [ i386 ] < none -> 0.12.2-0ubuntu1 > ( libs ) (>= 0.12.0)
  Considering gir1.2-json-glib-1.0:i386 5 as a solution to gir1.2-clutter-1.0:i386 7
  Holding Back gir1.2-clutter-1.0:i386 rather than change gir1.2-json-glib-1.0:i386
Investigating (1) xserver-xorg-input-all [ i386 ] < 1:7.5+6+xserver1.9 -> 1:7.6+4ubuntu3 > ( x11 )
Broken xserver-xorg-input-all:i386 Depends on xserver-xorg-input-synaptics [ i386 ] < 1:1.2.99+git20100610.a489ec15-0ubuntu0sarvatt2 > ( x11 )
  Considering xserver-xorg-input-synaptics:i386 1 as a solution to xserver-xorg-input-all:i386 4
  Added xserver-xorg-input-synaptics:i386 to the remove list
  Fixing xserver-xorg-input-all:i386 via keep of xserver-xorg-input-synaptics:i386
Investigating (1) libseed0 [ i386 ] < 2.31.91-0ubuntu1 -> 2.31.91-0ubuntu4 > ( universe/libs )
Broken libseed0:i386 Depends on gir1.2-clutter-1.0 [ i386 ] < none -> 1.6.14-0ubuntu3 > ( libs )
  Considering gir1.2-clutter-1.0:i386 7 as a solution to libseed0:i386 3
  Removing libseed0:i386 rather than change gir1.2-clutter-1.0:i386
Investigating (1) xserver-xorg-input-vmmouse [ i386 ] < 1:12.6.10+git20101204.e5987a4e-0ubuntu0sarvatt~maverick -> 1:12.6.99.901-1ubuntu2 > ( x11 )
Broken xserver-xorg-input-vmmouse:i386 Depends on xserver-xorg-input-mouse [ i386 ] < 1:1.6.99+git20101204.6b5a82e4-0ubuntu0sarvatt~maverick > ( x11 )
  Considering xserver-xorg-input-mouse:i386 1 as a solution to xserver-xorg-input-vmmouse:i386 2
  Added xserver-xorg-input-mouse:i386 to the remove list
  Fixing xserver-xorg-input-vmmouse:i386 via keep of xserver-xorg-input-mouse:i386
Investigating (1) mesa-common-dev [ i386 ] < 7.11.0+git20110222.7aeb610f-0ubuntu0sarvatt~maverick > ( devel )
Broken mesa-common-dev:i386 Depends on libdrm-dev [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libdevel )
  Considering libdrm-dev:i386 0 as a solution to mesa-common-dev:i386 2
  Added libdrm-dev:i386 to the remove list
  Fixing mesa-common-dev:i386 via keep of libdrm-dev:i386
Investigating (1) xserver-xorg-input-mouse [ i386 ] < 1:1.6.99+git20101204.6b5a82e4-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-input-mouse:i386 Depends on xorg-input-abi-11.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-input-mouse:i386 1
  Removing xserver-xorg-input-mouse:i386 rather than change xorg-input-abi-11.0:i386
Investigating (1) libwebkit-1.0-2 [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs )
Broken libwebkit-1.0-2:i386 Depends on libwebkit-1.0-common [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs ) (>= 1.2.5)
  Considering libwebkit-1.0-common:i386 0 as a solution to libwebkit-1.0-2:i386 1
  Added libwebkit-1.0-common:i386 to the remove list
  Fixing libwebkit-1.0-2:i386 via keep of libwebkit-1.0-common:i386
Investigating (1) xserver-xorg-input-synaptics [ i386 ] < 1:1.2.99+git20100610.a489ec15-0ubuntu0sarvatt2 > ( x11 )
Broken xserver-xorg-input-synaptics:i386 Depends on xorg-input-abi-11.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-input-synaptics:i386 1
  Removing xserver-xorg-input-synaptics:i386 rather than change xorg-input-abi-11.0:i386
Investigating (1) gnome3-session [ i386 ] < 2.32.0-0ubuntu1 -> 2.32.1-0ubuntu20 > ( universe/gnome )
Broken gnome3-session:i386 Depends on gnome-shell [ i386 ] < 2.31.5-2ubuntu2 > ( gnome )
  Considering gnome-shell:i386 -1 as a solution to gnome3-session:i386 0
  Added gnome-shell:i386 to the remove list
  Fixing gnome3-session:i386 via keep of gnome-shell:i386
Investigating (1) libdrm-dev [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libdevel )
Broken libdrm-dev:i386 Depends on libdrm-nouveau1 [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libs ) (= 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick)
  Considering libdrm-nouveau1:i386 5 as a solution to libdrm-dev:i386 0
  Removing libdrm-dev:i386 rather than change libdrm-nouveau1:i386
Investigating (1) gnome-shell [ i386 ] < 2.31.5-2ubuntu2 > ( gnome )
Broken gnome-shell:i386 Depends on gir1.0-atk-1.0 [ i386 ] < 1.32.0-0ubuntu1 > ( libs )
  Considering gir1.0-atk-1.0:i386 5 as a solution to gnome-shell:i386 -1
  Removing gnome-shell:i386 rather than change gir1.0-atk-1.0:i386
Investigating (2) libgl1-mesa-dri [ i386 ] < 7.11.0+git20110222.7aeb610f-0ubuntu0sarvatt~maverick > ( libs )
Broken libgl1-mesa-dri:i386 Depends on libdrm-nouveau1 [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libs ) (>= 2.4.21-1)
  Considering libdrm-nouveau1:i386 5 as a solution to libgl1-mesa-dri:i386 107
  Added libdrm-nouveau1:i386 to the remove list
  Fixing libgl1-mesa-dri:i386 via keep of libdrm-nouveau1:i386
Investigating (2) python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python )
Broken python-awn:i386 Depends on python-desktop-agnostic [ i386 ] < 0.3.93~bzr405+201103161905~maverick1 > ( universe/python )
  Considering python-desktop-agnostic:i386 28 as a solution to python-awn:i386 29
  Added python-desktop-agnostic:i386 to the remove list
  Fixing python-awn:i386 via keep of python-desktop-agnostic:i386
Investigating (2) python-desktop-agnostic [ i386 ] < 0.3.93~bzr405+201103161905~maverick1 > ( universe/python )
Broken python-desktop-agnostic:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to python-desktop-agnostic:i386 29
  Removing python-desktop-agnostic:i386 rather than change python:i386
Investigating (2) libdrm-nouveau1a [ i386 ] < none -> 2.4.23-1ubuntu6 > ( libs )
Broken libdrm-nouveau1a:i386 Breaks on libdrm-nouveau1 [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libs )
  Considering libdrm-nouveau1:i386 107 as a solution to libdrm-nouveau1a:i386 12
  Holding Back libdrm-nouveau1a:i386 rather than change libdrm-nouveau1:i386
Investigating (2) libwebkitgtk-1.0-common [ i386 ] < none -> 1.3.13-0ubuntu2 > ( libs )
Broken libwebkitgtk-1.0-common:i386 Conflicts on libwebkit-1.0-common [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs )
  Considering libwebkit-1.0-common:i386 0 as a solution to libwebkitgtk-1.0-common:i386 12
  Added libwebkit-1.0-common:i386 to the remove list
  Fixing libwebkitgtk-1.0-common:i386 via remove of libwebkit-1.0-common:i386
Investigating (2) python-gnome2-desktop [ i386 ] < 2.30.0-0ubuntu1 > ( python )
Broken python-gnome2-desktop:i386 Depends on python-gnomeprint [ i386 ] < 2.30.0-0ubuntu1 > ( python ) (>= 2.30.0-0ubuntu1)
  Considering python-gnomeprint:i386 9 as a solution to python-gnome2-desktop:i386 12
  Added python-gnomeprint:i386 to the remove list
  Fixing python-gnome2-desktop:i386 via keep of python-gnomeprint:i386
Investigating (2) python-gnomeprint [ i386 ] < 2.30.0-0ubuntu1 > ( python )
Broken python-gnomeprint:i386 Depends on python [ i386 ] < 2.6.6-2ubuntu2 -> 2.7.1-0ubuntu5 > ( python ) (< 2.7)
  Considering python:i386 2100 as a solution to python-gnomeprint:i386 12
  Removing python-gnomeprint:i386 rather than change python:i386
Investigating (2) seed [ i386 ] < 2.31.91-0ubuntu1 -> 2.31.91-0ubuntu4 > ( universe/interpreters )
Broken seed:i386 Depends on libseed0 [ i386 ] < 2.31.91-0ubuntu1 -> 2.31.91-0ubuntu4 > ( universe/libs ) (= 2.31.91-0ubuntu4)
  Considering libseed0:i386 3 as a solution to seed:i386 4
  Removing seed:i386 rather than change libseed0:i386
Investigating (2) xserver-xorg-input-all [ i386 ] < 1:7.5+6+xserver1.9 -> 1:7.6+4ubuntu3 > ( x11 )
Broken xserver-xorg-input-all:i386 Depends on xserver-xorg-input-synaptics [ i386 ] < 1:1.2.99+git20100610.a489ec15-0ubuntu0sarvatt2 > ( x11 )
  Considering xserver-xorg-input-synaptics:i386 1 as a solution to xserver-xorg-input-all:i386 4
  Added xserver-xorg-input-synaptics:i386 to the remove list
  Fixing xserver-xorg-input-all:i386 via keep of xserver-xorg-input-synaptics:i386
Investigating (2) xserver-xorg-input-vmmouse [ i386 ] < 1:12.6.10+git20101204.e5987a4e-0ubuntu0sarvatt~maverick -> 1:12.6.99.901-1ubuntu2 > ( x11 )
Broken xserver-xorg-input-vmmouse:i386 Depends on xserver-xorg-input-mouse [ i386 ] < 1:1.6.99+git20101204.6b5a82e4-0ubuntu0sarvatt~maverick > ( x11 )
  Considering xserver-xorg-input-mouse:i386 1 as a solution to xserver-xorg-input-vmmouse:i386 2
  Added xserver-xorg-input-mouse:i386 to the remove list
  Fixing xserver-xorg-input-vmmouse:i386 via keep of xserver-xorg-input-mouse:i386
Investigating (2) mesa-common-dev [ i386 ] < 7.11.0+git20110222.7aeb610f-0ubuntu0sarvatt~maverick > ( devel )
Broken mesa-common-dev:i386 Depends on libdrm-dev [ i386 ] < 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~maverick > ( libdevel )
  Considering libdrm-dev:i386 0 as a solution to mesa-common-dev:i386 2
  Added libdrm-dev:i386 to the remove list
  Fixing mesa-common-dev:i386 via keep of libdrm-dev:i386
Investigating (2) xserver-xorg-input-mouse [ i386 ] < 1:1.6.99+git20101204.6b5a82e4-0ubuntu0sarvatt~maverick > ( x11 )
Broken xserver-xorg-input-mouse:i386 Depends on xorg-input-abi-11.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-input-mouse:i386 2
  Removing xserver-xorg-input-mouse:i386 rather than change xorg-input-abi-11.0:i386
Investigating (2) libwebkit-1.0-2 [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs )
Broken libwebkit-1.0-2:i386 Depends on libwebkit-1.0-common [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs ) (>= 1.2.5)
  Considering libwebkit-1.0-common:i386 12 as a solution to libwebkit-1.0-2:i386 1
  Removing libwebkit-1.0-2:i386 rather than change libwebkit-1.0-common:i386
Investigating (2) xserver-xorg-input-synaptics [ i386 ] < 1:1.2.99+git20100610.a489ec15-0ubuntu0sarvatt2 > ( x11 )
Broken xserver-xorg-input-synaptics:i386 Depends on xorg-input-abi-11.0 [ i386 ] < none > ( none )
  Considering xserver-xorg-core:i386 68 as a solution to xserver-xorg-input-synaptics:i386 4
  Removing xserver-xorg-input-synaptics:i386 rather than change xorg-input-abi-11.0:i386
Investigating (2) gnome3-session [ i386 ] < 2.32.0-0ubuntu1 -> 2.32.1-0ubuntu20 > ( universe/gnome )
Broken gnome3-session:i386 Depends on gnome-shell [ i386 ] < 2.31.5-2ubuntu2 > ( gnome )
  Considering gnome-shell:i386 -1 as a solution to gnome3-session:i386 0
  Added gnome-shell:i386 to the remove list
  Fixing gnome3-session:i386 via keep of gnome-shell:i386
Investigating (2) gnome-shell [ i386 ] < 2.31.5-2ubuntu2 > ( gnome )
Broken gnome-shell:i386 Depends on gir1.0-atk-1.0 [ i386 ] < 1.32.0-0ubuntu1 > ( libs )
  Considering gir1.0-atk-1.0:i386 5 as a solution to gnome-shell:i386 0
  Removing gnome-shell:i386 rather than change gir1.0-atk-1.0:i386
Investigating (2) midori [ i386 ] < 0.3.3-1~getdeb1 > ( universe/web )
Broken midori:i386 Depends on libwebkit-1.0-2 [ i386 ] < 1.2.5-0ubuntu0.10.10.1 > ( libs ) (>= 1.1.23)
  Considering libwebkit-1.0-2:i386 12 as a solution to midori:i386 -1
  Removing midori:i386 rather than change libwebkit-1.0-2:i386
Investigating (3) python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python )
Broken python-awn:i386 Depends on python-desktop-agnostic [ i386 ] < 0.3.93~bzr405+201103161905~maverick1 > ( universe/python )
  Considering python-desktop-agnostic:i386 2100 as a solution to python-awn:i386 29
  Removing python-awn:i386 rather than change python-desktop-agnostic:i386
Investigating (3) plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth:i386 Depends on libdrm-nouveau1a [ i386 ] < none -> 2.4.23-1ubuntu6 > ( libs ) (>= 2.4.23)
  Considering libdrm-nouveau1a:i386 12 as a solution to plymouth:i386 22
  Removing plymouth:i386 rather than change libdrm-nouveau1a:i386
Investigating (3) plymouth-theme-ubuntu-text [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth-theme-ubuntu-text:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
  Considering plymouth:i386 22 as a solution to plymouth-theme-ubuntu-text:i386 15
  Removing plymouth-theme-ubuntu-text:i386 rather than change plymouth:i386
Investigating (3) python-gnome2-desktop [ i386 ] < 2.30.0-0ubuntu1 > ( python )
Broken python-gnome2-desktop:i386 Depends on python-gnomeprint [ i386 ] < 2.30.0-0ubuntu1 > ( python ) (>= 2.30.0-0ubuntu1)
  Considering python-gnomeprint:i386 2100 as a solution to python-gnome2-desktop:i386 12
  Removing python-gnome2-desktop:i386 rather than change python-gnomeprint:i386
Investigating (3) awn-applet-volume-control [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-volume-control:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-volume-control:i386 4
  Holding Back awn-applet-volume-control:i386 rather than change python-awn:i386
Investigating (3) awn-applet-cpufreq [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-cpufreq:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-cpufreq:i386 4
  Holding Back awn-applet-cpufreq:i386 rather than change python-awn:i386
Investigating (3) awn-applet-thinkhdaps [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-thinkhdaps:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-thinkhdaps:i386 4
  Holding Back awn-applet-thinkhdaps:i386 rather than change python-awn:i386
Investigating (3) awn-applet-cairo-clock [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-cairo-clock:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-cairo-clock:i386 4
  Holding Back awn-applet-cairo-clock:i386 rather than change python-awn:i386
Investigating (3) awn-applet-animal-farm [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-animal-farm:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-animal-farm:i386 4
  Holding Back awn-applet-animal-farm:i386 rather than change python-awn:i386
Investigating (3) awn-applet-dialect [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-dialect:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-dialect:i386 4
  Holding Back awn-applet-dialect:i386 rather than change python-awn:i386
Investigating (3) awn-applet-quit-applet [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-quit-applet:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-quit-applet:i386 4
  Holding Back awn-applet-quit-applet:i386 rather than change python-awn:i386
Investigating (3) awn-applet-hardware-sensors [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-hardware-sensors:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-hardware-sensors:i386 4
  Holding Back awn-applet-hardware-sensors:i386 rather than change python-awn:i386
Investigating (3) xserver-xorg-input-all [ i386 ] < 1:7.5+6+xserver1.9 -> 1:7.6+4ubuntu3 > ( x11 )
Broken xserver-xorg-input-all:i386 Depends on xserver-xorg-input-synaptics [ i386 ] < 1:1.2.99+git20100610.a489ec15-0ubuntu0sarvatt2 > ( x11 )
  Considering xserver-xorg-input-synaptics:i386 68 as a solution to xserver-xorg-input-all:i386 4
  Removing xserver-xorg-input-all:i386 rather than change xserver-xorg-input-synaptics:i386
Investigating (3) awn-applet-todo [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-todo:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-todo:i386 4
  Holding Back awn-applet-todo:i386 rather than change python-awn:i386
Investigating (3) awn-applet-weather [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-weather:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-weather:i386 4
  Holding Back awn-applet-weather:i386 rather than change python-awn:i386
Investigating (3) awn-applet-bandwidth-monitor [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-bandwidth-monitor:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-bandwidth-monitor:i386 4
  Holding Back awn-applet-bandwidth-monitor:i386 rather than change python-awn:i386
Investigating (3) awn-applet-file-browser-launcher [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-file-browser-launcher:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-file-browser-launcher:i386 4
  Holding Back awn-applet-file-browser-launcher:i386 rather than change python-awn:i386
Investigating (3) awn-applet-stack [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-stack:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-stack:i386 4
  Holding Back awn-applet-stack:i386 rather than change python-awn:i386
Investigating (3) awn-applet-comics [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-comics:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-comics:i386 4
  Holding Back awn-applet-comics:i386 rather than change python-awn:i386
Investigating (3) awn-applet-media-player [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-media-player:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-media-player:i386 4
  Holding Back awn-applet-media-player:i386 rather than change python-awn:i386
Investigating (3) awn-applet-media-icon-applet [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-media-icon-applet:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-media-icon-applet:i386 4
  Holding Back awn-applet-media-icon-applet:i386 rather than change python-awn:i386
Investigating (3) awn-applet-battery-applet [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-battery-applet:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-battery-applet:i386 4
  Holding Back awn-applet-battery-applet:i386 rather than change python-awn:i386
Investigating (3) awn-applet-mail [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-mail:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-mail:i386 4
  Holding Back awn-applet-mail:i386 rather than change python-awn:i386
Investigating (3) awn-applet-feeds [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-feeds:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-feeds:i386 4
  Holding Back awn-applet-feeds:i386 rather than change python-awn:i386
Investigating (3) awn-applet-media-control [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-media-control:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-media-control:i386 4
  Holding Back awn-applet-media-control:i386 rather than change python-awn:i386
Investigating (3) awn-applet-common-folder [ i386 ] < none -> 0.4.1~bzr1507-0ubuntu1 > ( universe/gnome )
Broken awn-applet-common-folder:i386 Depends on python-awn [ i386 ] < 0.4.0-2ubuntu1 -> 0.4.1~bzr822-0ubuntu3 > ( universe/python ) (>= 0.3.2.1)
  Considering python-awn:i386 2100 as a solution to awn-applet-common-folder:i386 4
  Holding Back awn-applet-common-folder:i386 rather than change python-awn:i386
Investigating (3) plymouth-label [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth-label:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 ) (= 0.8.2-2ubuntu23)
  Considering plymouth:i386 22 as a solution to plymouth-label:i386 2
  Removing plymouth-label:i386 rather than change plymouth:i386
Investigating (3) xserver-xorg-input-vmmouse [ i386 ] < 1:12.6.10+git20101204.e5987a4e-0ubuntu0sarvatt~maverick -> 1:12.6.99.901-1ubuntu2 > ( x11 )
Broken xserver-xorg-input-vmmouse:i386 Depends on xserver-xorg-input-mouse [ i386 ] < 1:1.6.99+git20101204.6b5a82e4-0ubuntu0sarvatt~maverick > ( x11 )
  Considering xserver-xorg-input-mouse:i386 68 as a solution to xserver-xorg-input-vmmouse:i386 2
  Removing xserver-xorg-input-vmmouse:i386 rather than change xserver-xorg-input-mouse:i386
Investigating (3) plymouth-theme-ubuntu-logo [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth-theme-ubuntu-logo:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
  Considering plymouth:i386 22 as a solution to plymouth-theme-ubuntu-logo:i386 1
  Removing plymouth-theme-ubuntu-logo:i386 rather than change plymouth:i386
Investigating (3) plymouth-x11 [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( universe/x11 )
Broken plymouth-x11:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 ) (= 0.8.2-2ubuntu23)
  Considering plymouth:i386 22 as a solution to plymouth-x11:i386 0
  Removing plymouth-x11:i386 rather than change plymouth:i386
Investigating (3) gnome3-session [ i386 ] < 2.32.0-0ubuntu1 -> 2.32.1-0ubuntu20 > ( universe/gnome )
Broken gnome3-session:i386 Depends on gnome-shell [ i386 ] < 2.31.5-2ubuntu2 > ( gnome )
  Considering gnome-shell:i386 5 as a solution to gnome3-session:i386 0
  Removing gnome3-session:i386 rather than change gnome-shell:i386
Investigating (3) dockbarx [ i386 ] < 0.24.0-1~ppa1 > ( gnome )
Broken dockbarx:i386 Depends on python-gnome2-desktop [ i386 ] < 2.30.0-0ubuntu1 > ( python )
  Considering python-gnome2-desktop:i386 2100 as a solution to dockbarx:i386 -2
  Removing dockbarx:i386 rather than change python-gnome2-desktop:i386
Investigating (4) mountall [ i386 ] < 2.19 -> 2.25ubuntu1 > ( admin )
Broken mountall:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
  Considering plymouth:i386 22 as a solution to mountall:i386 24
  Added plymouth:i386 to the remove list
  Fixing mountall:i386 via keep of plymouth:i386
 Try to Re-Instate (4) plymouth:i386
Investigating (4) plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth:i386 Depends on libplymouth2 [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( libs ) (= 0.8.2-2ubuntu5.1)
  Considering libplymouth2:i386 27 as a solution to plymouth:i386 24
  Removing plymouth:i386 rather than change libplymouth2:i386
Investigating (5) mountall [ i386 ] < 2.19 -> 2.25ubuntu1 > ( admin )
Broken mountall:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
  Considering plymouth:i386 27 as a solution to mountall:i386 24
  Removing mountall:i386 rather than change plymouth:i386
Investigating (6) upstart [ i386 ] < 0.6.6-4 -> 0.9.7-1 > ( admin )
Broken upstart:i386 Depends on mountall [ i386 ] < 2.19 -> 2.25ubuntu1 > ( admin )
  Considering mountall:i386 27 as a solution to upstart:i386 63
  Added mountall:i386 to the remove list
  Fixing upstart:i386 via keep of mountall:i386
 Try to Re-Instate (6) mountall:i386
Investigating (6) mountall [ i386 ] < 2.19 -> 2.25ubuntu1 > ( admin )
Broken mountall:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
  Considering plymouth:i386 27 as a solution to mountall:i386 63
  Added plymouth:i386 to the remove list
  Fixing mountall:i386 via keep of plymouth:i386
Investigating (6) plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth:i386 Depends on libplymouth2 [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( libs ) (= 0.8.2-2ubuntu5.1)
  Considering libplymouth2:i386 27 as a solution to plymouth:i386 63
  Added libplymouth2:i386 to the remove list
  Fixing plymouth:i386 via keep of libplymouth2:i386
Investigating (7) libpango1.0-0 [ i386 ] < 1.28.2-0ubuntu1.1 -> 1.28.4-0ubuntu1 > ( libs )
Broken libpango1.0-0:i386 Breaks on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 ) (< 0.8.2-2ubuntu19)
  Considering plymouth:i386 63 as a solution to libpango1.0-0:i386 1286
  Upgrading plymouth:i386 due to Breaks field in libpango1.0-0:i386
 Try to Re-Instate (7) libplymouth2:i386
Re-Instated libplymouth2:i386 (1 vs 1)
Investigating (7) plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth:i386 Depends on libdrm-nouveau1a [ i386 ] < none -> 2.4.23-1ubuntu6 > ( libs ) (>= 2.4.23)
  Considering libdrm-nouveau1a:i386 12 as a solution to plymouth:i386 63
  Removing plymouth:i386 rather than change libdrm-nouveau1a:i386
Investigating (8) mountall [ i386 ] < 2.19 -> 2.25ubuntu1 > ( admin )
Broken mountall:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu5.1 -> 0.8.2-2ubuntu23 > ( x11 )
  Considering plymouth:i386 63 as a solution to mountall:i386 63
  Removing mountall:i386 rather than change plymouth:i386
Investigating (9) upstart [ i386 ] < 0.6.6-4 -> 0.9.7-1 > ( admin )
Broken upstart:i386 Depends on mountall [ i386 ] < 2.19 -> 2.25ubuntu1 > ( admin )
  Considering mountall:i386 63 as a solution to upstart:i386 63
  Removing upstart:i386 rather than change mountall:i386
Investigating (9) cups [ i386 ] < 1.4.4-6ubuntu2.3 -> 1.4.6-5ubuntu1 > ( net )
Broken cups:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to cups:i386 49
  Removing cups:i386 rather than change upstart-job:i386
Investigating (9) keyboard-configuration [ i386 ] < none -> 1.57ubuntu20 > ( utils )
Broken keyboard-configuration:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to keyboard-configuration:i386 48
  Holding Back keyboard-configuration:i386 rather than change upstart-job:i386
Investigating (9) initscripts [ i386 ] < 2.87dsf-4ubuntu19.2 -> 2.87dsf-4ubuntu23 > ( admin )
Broken initscripts:i386 Depends on upstart [ i386 ] < 0.6.6-4 -> 0.9.7-1 > ( admin )
  Considering upstart:i386 63 as a solution to initscripts:i386 47
  Removing initscripts:i386 rather than change upstart:i386
Investigating (9) avahi-daemon [ i386 ] < 0.6.27-2ubuntu3.1 -> 0.6.30-0ubuntu2 > ( net )
Broken avahi-daemon:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to avahi-daemon:i386 40
  Removing avahi-daemon:i386 rather than change upstart-job:i386
Investigating (9) ecryptfs-utils [ i386 ] < none -> 87-0ubuntu1 > ( misc )
Broken ecryptfs-utils:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to ecryptfs-utils:i386 35
  Holding Back ecryptfs-utils:i386 rather than change upstart-job:i386
Investigating (9) ifupdown [ i386 ] < 0.6.10ubuntu3.1 -> 0.6.10ubuntu4 > ( admin )
Broken ifupdown:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to ifupdown:i386 33
  Removing ifupdown:i386 rather than change upstart-job:i386
Investigating (9) cron [ i386 ] < 3.0pl1-114ubuntu1 -> 3.0pl1-116ubuntu1 > ( admin )
Broken cron:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to cron:i386 25
  Removing cron:i386 rather than change upstart-job:i386
Investigating (9) console-setup [ i386 ] < 1.34ubuntu15 -> 1.57ubuntu20 > ( utils )
Broken console-setup:i386 Depends on keyboard-configuration [ i386 ] < none -> 1.57ubuntu20 > ( utils )
  Considering keyboard-configuration:i386 48 as a solution to console-setup:i386 20
  Holding Back console-setup:i386 rather than change keyboard-configuration:i386
Investigating (9) cups-driver-gutenprint [ i386 ] < 5.2.6-0ubuntu8 -> 5.2.6-1ubuntu1 > ( graphics )
Broken cups-driver-gutenprint:i386 Depends on cups [ i386 ] < 1.4.4-6ubuntu2.3 -> 1.4.6-5ubuntu1 > ( net ) (>= 1.3.0)
  Considering cups:i386 63 as a solution to cups-driver-gutenprint:i386 18
  Removing cups-driver-gutenprint:i386 rather than change cups:i386
Investigating (9) anacron [ i386 ] < 2.3-14ubuntu1 > ( admin )
Broken anacron:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to anacron:i386 15
  Removing anacron:i386 rather than change upstart-job:i386
Investigating (9) rsyslog [ i386 ] < 4.2.0-2ubuntu8 -> 4.6.4-2ubuntu4 > ( admin )
Broken rsyslog:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to rsyslog:i386 13
  Removing rsyslog:i386 rather than change upstart-job:i386
Investigating (9) ureadahead [ i386 ] < 0.100.0-8 -> 0.100.0-11 > ( admin )
Broken ureadahead:i386 Depends on upstart [ i386 ] < 0.6.6-4 -> 0.9.7-1 > ( admin ) (>= 0.6.0)
  Considering upstart:i386 63 as a solution to ureadahead:i386 12
  Removing ureadahead:i386 rather than change upstart:i386
Investigating (9) apport [ i386 ] < 1.14.1-0ubuntu8.1 -> 1.20.1-0ubuntu5 > ( utils )
Broken apport:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to apport:i386 11
  Removing apport:i386 rather than change upstart-job:i386
Investigating (9) libnss-mdns [ i386 ] < 0.10-3ubuntu4 -> 0.10-3.1ubuntu1 > ( admin )
Broken libnss-mdns:i386 Depends on avahi-daemon [ i386 ] < 0.6.27-2ubuntu3.1 -> 0.6.30-0ubuntu2 > ( net ) (>= 0.6.16-1)
  Considering avahi-daemon:i386 63 as a solution to libnss-mdns:i386 11
  Removing libnss-mdns:i386 rather than change avahi-daemon:i386
Investigating (9) irqbalance [ i386 ] < 0.56-0ubuntu2 -> 0.56-1ubuntu3 > ( utils )
Broken irqbalance:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to irqbalance:i386 5
  Removing irqbalance:i386 rather than change upstart-job:i386
Investigating (9) at [ i386 ] < 3.1.12-1ubuntu2 > ( admin )
Broken at:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to at:i386 5
  Removing at:i386 rather than change upstart-job:i386
Investigating (9) friendly-recovery [ i386 ] < 0.2.10 -> 0.2.11 > ( admin )
Broken friendly-recovery:i386 Depends on upstart [ i386 ] < 0.6.6-4 -> 0.9.7-1 > ( admin )
  Considering upstart:i386 63 as a solution to friendly-recovery:i386 5
  Removing friendly-recovery:i386 rather than change upstart:i386
Investigating (9) alsa-utils [ i386 ] < 1.0.23-2ubuntu3.4 -> 1.0.24.2-0ubuntu6 > ( sound )
Broken alsa-utils:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to alsa-utils:i386 5
  Removing alsa-utils:i386 rather than change upstart-job:i386
Investigating (9) ufw [ i386 ] < 0.30.0-1ubuntu2 -> 0.30.1-1ubuntu1 > ( admin )
Broken ufw:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to ufw:i386 5
  Removing ufw:i386 rather than change upstart-job:i386
Investigating (9) apport-gtk [ i386 ] < 1.14.1-0ubuntu8.1 -> 1.20.1-0ubuntu5 > ( gnome )
Broken apport-gtk:i386 Depends on apport [ i386 ] < 1.14.1-0ubuntu8.1 -> 1.20.1-0ubuntu5 > ( utils ) (>= 0.41)
  Considering apport:i386 63 as a solution to apport-gtk:i386 5
  Removing apport-gtk:i386 rather than change apport:i386
Investigating (9) hplip-cups [ i386 ] < 3.10.6-1ubuntu10.2 -> 3.11.1-2ubuntu2 > ( text )
Broken hplip-cups:i386 Depends on cups [ i386 ] < 1.4.4-6ubuntu2.3 -> 1.4.6-5ubuntu1 > ( net )
  Considering cups:i386 63 as a solution to hplip-cups:i386 4
  Removing hplip-cups:i386 rather than change cups:i386
Investigating (9) hplip [ i386 ] < 3.10.6-1ubuntu10.2 -> 3.11.1-2ubuntu2 > ( utils )
Broken hplip:i386 Depends on hplip-cups [ i386 ] < 3.10.6-1ubuntu10.2 -> 3.11.1-2ubuntu2 > ( text ) (= 3.11.1-2ubuntu2)
  Considering hplip-cups:i386 63 as a solution to hplip:i386 4
  Removing hplip:i386 rather than change hplip-cups:i386
Investigating (9) ubuntu-minimal [ i386 ] < 1.207 -> 1.220 > ( metapackages )
Broken ubuntu-minimal:i386 Depends on ifupdown [ i386 ] < 0.6.10ubuntu3.1 -> 0.6.10ubuntu4 > ( admin )
  Considering ifupdown:i386 63 as a solution to ubuntu-minimal:i386 4
  Removing ubuntu-minimal:i386 rather than change ifupdown:i386
Investigating (9) openssh-server [ i386 ] < 1:5.5p1-4ubuntu5 -> 1:5.8p1-1ubuntu3 > ( net )
Broken openssh-server:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to openssh-server:i386 4
  Removing openssh-server:i386 rather than change upstart-job:i386
Investigating (9) network-manager [ i386 ] < 0.8.1+git.20100810t184654.ab580f4-0ubuntu2.1 -> 0.8.4~git.20110319t175609.d14809b-0ubuntu3 > ( net )
Broken network-manager:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to network-manager:i386 3
  Removing network-manager:i386 rather than change upstart-job:i386
Investigating (9) bluez-cups [ i386 ] < 4.69-0ubuntu2 -> 4.91-0ubuntu1 > ( admin )
Broken bluez-cups:i386 Depends on cups [ i386 ] < 1.4.4-6ubuntu2.3 -> 1.4.6-5ubuntu1 > ( net )
  Considering cups:i386 63 as a solution to bluez-cups:i386 3
  Removing bluez-cups:i386 rather than change cups:i386
Investigating (9) network-manager-gnome [ i386 ] < 0.8.1+git.20100809t190028.290dc70-0ubuntu3 -> 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1 > ( net )
Broken network-manager-gnome:i386 Depends on network-manager [ i386 ] < 0.8.1+git.20100810t184654.ab580f4-0ubuntu2.1 -> 0.8.4~git.20110319t175609.d14809b-0ubuntu3 > ( net ) (>= 0.8.4~)
  Considering network-manager:i386 63 as a solution to network-manager-gnome:i386 3
  Removing network-manager-gnome:i386 rather than change network-manager:i386
Investigating (9) gdm [ i386 ] < 2.30.5-0ubuntu4.1+langfixes~maverick1 -> 2.32.1-0ubuntu3.1 > ( gnome )
Broken gdm:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to gdm:i386 3
  Removing gdm:i386 rather than change upstart-job:i386
Investigating (9) telepathy-salut [ i386 ] < 0.3.12-1 -> 0.4.0-1 > ( net )
Broken telepathy-salut:i386 Depends on avahi-daemon [ i386 ] < 0.6.27-2ubuntu3.1 -> 0.6.30-0ubuntu2 > ( net )
  Considering avahi-daemon:i386 63 as a solution to telepathy-salut:i386 2
  Removing telepathy-salut:i386 rather than change avahi-daemon:i386
Investigating (9) ubuntu-standard [ i386 ] < 1.207 -> 1.220 > ( metapackages )
Broken ubuntu-standard:i386 Depends on at [ i386 ] < 3.1.12-1ubuntu2 > ( admin )
  Considering at:i386 63 as a solution to ubuntu-standard:i386 2
  Removing ubuntu-standard:i386 rather than change at:i386
Investigating (9) sreadahead [ i386 ] < 1:0.100.0-8 > ( admin )
Broken sreadahead:i386 Depends on ureadahead [ i386 ] < 0.100.0-8 -> 0.100.0-11 > ( admin )
  Considering ureadahead:i386 63 as a solution to sreadahead:i386 2
  Removing sreadahead:i386 rather than change ureadahead:i386
Investigating (9) avahi-utils [ i386 ] < 0.6.27-2ubuntu3.1 -> 0.6.30-0ubuntu2 > ( net )
Broken avahi-utils:i386 Depends on avahi-daemon [ i386 ] < 0.6.27-2ubuntu3.1 -> 0.6.30-0ubuntu2 > ( net )
  Considering avahi-daemon:i386 63 as a solution to avahi-utils:i386 2
  Removing avahi-utils:i386 rather than change avahi-daemon:i386
Investigating (9) acpid [ i386 ] < 1.0.10-5ubuntu4 -> 1:2.0.7-1ubuntu2 > ( admin )
Broken acpid:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to acpid:i386 2
  Removing acpid:i386 rather than change upstart-job:i386
Investigating (9) ssh [ i386 ] < 1:5.5p1-4ubuntu5 -> 1:5.8p1-1ubuntu3 > ( net )
Broken ssh:i386 Depends on openssh-server [ i386 ] < 1:5.5p1-4ubuntu5 -> 1:5.8p1-1ubuntu3 > ( net )
  Considering openssh-server:i386 63 as a solution to ssh:i386 2
  Removing ssh:i386 rather than change openssh-server:i386
Investigating (9) pxljr [ i386 ] < 1.1-0ubuntu7 > ( text )
Broken pxljr:i386 Depends on cups [ i386 ] < 1.4.4-6ubuntu2.3 -> 1.4.6-5ubuntu1 > ( net )
  Considering cups:i386 63 as a solution to pxljr:i386 1
  Removing pxljr:i386 rather than change cups:i386
Investigating (9) screen [ i386 ] < 4.0.3-14ubuntu4 -> 4.0.3-14ubuntu7 > ( misc )
Broken screen:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to screen:i386 1
  Removing screen:i386 rather than change upstart-job:i386
Investigating (9) splix [ i386 ] < 2.0.0+20100802-0ubuntu4 -> 2.0.0+20110219-0ubuntu1 > ( text )
Broken splix:i386 Depends on cups [ i386 ] < 1.4.4-6ubuntu2.3 -> 1.4.6-5ubuntu1 > ( net )
  Considering cups:i386 63 as a solution to splix:i386 1
  Removing splix:i386 rather than change cups:i386
Investigating (9) acpi-support [ i386 ] < 0.137 -> 0.138 > ( admin )
Broken acpi-support:i386 Depends on acpid [ i386 ] < 1.0.10-5ubuntu4 -> 1:2.0.7-1ubuntu2 > ( admin ) (>= 1.0.4-1ubuntu4)
  Considering acpid:i386 63 as a solution to acpi-support:i386 1
  Removing acpi-support:i386 rather than change acpid:i386
Investigating (9) foo2zjs [ i386 ] < 20100728-0ubuntu1 -> 20110210dfsg-1ubuntu2 > ( text )
Broken foo2zjs:i386 Depends on cups [ i386 ] < 1.4.4-6ubuntu2.3 -> 1.4.6-5ubuntu1 > ( net )
  Considering cups:i386 63 as a solution to foo2zjs:i386 1
  Removing foo2zjs:i386 rather than change cups:i386
Investigating (9) gdm-guest-session [ i386 ] < 0.17 -> 0.24 > ( gnome )
Broken gdm-guest-session:i386 Depends on gdm [ i386 ] < 2.30.5-0ubuntu4.1+langfixes~maverick1 -> 2.32.1-0ubuntu3.1 > ( gnome ) (>= 2.30.0-0ubuntu5)
  Considering gdm:i386 63 as a solution to gdm-guest-session:i386 1
  Removing gdm-guest-session:i386 rather than change gdm:i386
Investigating (9) byobu [ i386 ] < 3.5-0ubuntu1 -> 3.33-0ubuntu1 > ( misc )
Broken byobu:i386 Depends on screen [ i386 ] < 4.0.3-14ubuntu4 -> 4.0.3-14ubuntu7 > ( misc )
  Considering screen:i386 63 as a solution to byobu:i386 0
  Removing byobu:i386 rather than change screen:i386
Investigating (9) hplip-gui [ i386 ] < 3.10.6-1ubuntu10.2 -> 3.11.1-2ubuntu2 > ( universe/utils )
Broken hplip-gui:i386 Depends on hplip [ i386 ] < 3.10.6-1ubuntu10.2 -> 3.11.1-2ubuntu2 > ( utils ) (= 3.11.1-2ubuntu2)
  Considering hplip:i386 63 as a solution to hplip-gui:i386 0
  Removing hplip-gui:i386 rather than change hplip:i386
Investigating (9) ubuntu-desktop [ i386 ] < 1.207 -> 1.220 > ( metapackages )
Broken ubuntu-desktop:i386 Depends on alsa-utils [ i386 ] < 1.0.23-2ubuntu3.4 -> 1.0.24.2-0ubuntu6 > ( sound )
  Considering alsa-utils:i386 63 as a solution to ubuntu-desktop:i386 0
  Removing ubuntu-desktop:i386 rather than change alsa-utils:i386
Investigating (9) samba [ i386 ] < 2:3.5.4~dfsg-1ubuntu8.4 -> 2:3.5.8~dfsg-1ubuntu2.1 > ( net )
Broken samba:i386 Depends on upstart-job [ i386 ] < none > ( none )
  Considering upstart:i386 63 as a solution to samba:i386 0
  Removing samba:i386 rather than change upstart-job:i386
Investigating (9) apport-hooks-medibuntu [ i386 ] < 1medibuntu1 > ( utils )
Broken apport-hooks-medibuntu:i386 Depends on apport [ i386 ] < 1.14.1-0ubuntu8.1 -> 1.20.1-0ubuntu5 > ( utils ) (>= 0.146~)
  Considering apport:i386 63 as a solution to apport-hooks-medibuntu:i386 -1
  Removing apport-hooks-medibuntu:i386 rather than change apport:i386
Done
Log time: 2011-05-05 20:00:40.395815
```

---

### Post by kimet on 2011-05-06
No es veu cap error, pero hi han molts reports de bugs semblants al teu, en alguns casos ho han sol.lucionat desinstal.lant xserver-xorg-video-nouveau

Salut.

---

### Post by quitus on 2011-05-06
Si, també ho vaig provar.

Sembla que serà un dels pocs casos en que la solució instal·lació des de 0 serà la més adient.

---

### Post by wgarcia on 2011-05-06
A mi no m'agrada gens tornar a instal·lar, penso que una de les grans virtuts des Linux és que no s'ha de començar de nou cada X temps com passa a altres sistemes operatius tecnològicament inferiors.

Al registre que has mostrat, es veu que tens habilitat el dipòsit "medibuntu". Prova de deshabilitar-lo de moment (normalment es deshabilita sol quan actualitzes de versió d'Ubuntu per això m'estranya que estigui habilitat). 

Mira també que totes les línies de /etc/apt/sources.list (les que no estiguin comentades) apuntin a la versió actual.
Després intenta donar totes les ordres següents:

sudo apt-get clean 
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
sudo apt-get upgrade

---

### Post by quitus on 2011-05-07
Estic totalment d'acord amb tu, porto actualitzant des de el 8.04 amb un funcionament perfecte del sistema (les limitacions son a causa del hardware P4, ati radeonX700, 1Gb ram) per això m'estranya aquest problema amb les dependències.

He provat reduir el sources.list a la mínima expressió com hem demanes, cosa que ja havia provat i segueix sense èxit, però hi ha una cosa que no m'agrada.

He generat amb aquest lloc [http://repogen.simplylinux.ch/index.php]("http://repogen.simplylinux.ch/index.php") un nou sources.list però després de substituir-lo, en obrir /sistema /administració/font de programari en la pestanya "altre programari" no apareixen les línies tal i com jo les he posat en el nou sources.list:confused: apareixen línies d'un intent d'actualització anterior. Si que sembla que quan cerca actualitzacions utilitzi el sources.list nou 

Espero que això ajudi a resoldre el problema

---

### Post by quitus on 2011-05-08
Bé, tot el problema de les dependències no ho he pogut solucionar, però en iniciar el livecd per fer una nova instal·lació he vist que hi havia una opció per actualitzar el sistema instal·lat des de el cd.

Clar jo ho havia provat afegint el cd des de synaptic, no executant el livecd i actualitzar, cosa que desconeixia que es podia fer, tant de temps sense instal·lar de 0...

En definitiva, l'ubuntu s'ha actualitzat sense problemes, tan sols he hagut de recuperar el grub

salut i gracies.

---

### Post by wgarcia on 2011-05-08
Sí, es una opció nova del CD (o USB) autònom d'aquest versió 11.04, abans amb els autònoms (Live) sols es podia instal·lar de nou i ara també es pot actualitzar. 

El que no sé com funciona és amb el programari addicional que no ve a la imatge del autònom, suposo que el deixa sense actualitzar i en quant té connexió t'ofereix actualitzar-lo...

---

### Post by quitus on 2011-05-08
Doncs... no, en el meu cas no, m'ha donat un error d'instal·lació d'alguns programes o paquets, però han sigut tots els programes els que s'han afectat m'ha deixat el sistema pelat. Però ha sigut realment una actualització, ja que la partició home la mantingut tal qual i jo no he especificat res.

Veig que també s'ha modificat el fstab, m'ha canviat el nom del segon disc dur, l'hauré de retocar per que coincideixi amb la configuració dels programes que es veuen afectats.

salut

---

