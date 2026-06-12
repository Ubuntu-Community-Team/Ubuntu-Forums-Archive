---
title: "Problem after upgrading firefox to edgy version"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Peterchen Brot on 2006-09-28
After i upgraded my dapper firefox to edgy firefox version everthing looks like shit.

Can someone please help me?

---

### Post by Peterchen Brot on 2006-09-28
I think that the libc6 is the problem:

What i did: sudo apt-get install libc6/dapper

I get this answer:

Reading package lists... Done
Building dependency tree... Done
Selected version 2.3.6-0ubuntu20 (Ubuntu:6.06/dapper) for libc6
Suggested packages:
  glibc-doc
The following packages will be REMOVED:
  acpi-support acpid acroread adduser alacarte alien alsa-base alsa-utils
  anacron apmd appres apt apt-utils aptitude aspell aspell-en at at-spi
  azureus base-files bash bc beforelight bicyclerepair bitmap bittorrent blt
  bluez-cups bluez-pcmcia-support bluez-pin bluez-utils brltty brltty-x11
  bsdmainutils bug-buddy cacao capplets-data cdrdao classpath console-common
  console-tools contact-lookup-applet coreutils cpp cpp-4.0 cpp-4.1 cron
  cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint
  cupsys-driver-gutenprint dbus dbus-1-utils dctc debhelper debianutils defoma
  deskbar-applet desktop-file-utils dhcp3-client dhcp3-common discover1
  diveintopython doc-base dpkg dpkg-dev dselect dvd+rw-tools editres ekiga eog
  evince evms evms-ncurses evolution evolution-data-server evolution-exchange
  evolution-plugins evolution-webcal exfalso fdutils festival festlex-cmu
  festlex-poslex festvox-kallpc16k file-roller firefox flashplugin-nonfree
  fontconfig foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs
  foomatic-filters foomatic-filters-ppds freeglut3 fstobdf ftp gaim gamin
  gcalctool gcc gcc-4.0 gcc-4.1 gconf-editor gconf2 gdb gdebi gdm gedit
  gftp-gtk gimp gimp-print gimp-python gksu gnome-about
  gnome-accessibility-themes gnome-applets gnome-applets-data gnome-btdownload
  gnome-control-center gnome-cups-manager gnome-doc-utils gnome-games
  gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media
  gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager
  gnome-screensaver gnome-session gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes
  gnome-utils gnome-volume-manager gnome2-user-guide gnomebaker gnopernicus
  gnupg gok goobox gparted groff-base grub gs-common gs-esp gsfonts
  gsfonts-x11 gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-tools gstreamer0.10-x gstreamer0.8-cdparanoia
  gstreamer0.8-gnomevfs gstreamer0.8-mad gstreamer0.8-misc gthumb
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast
  gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist
  gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth
  gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gtkpod gucharmap
  guile-1.6-libs gzip hal hal-device-manager hpijs hplip html2text hwdb-client
  iceauth ico ifupdown ijsgutenprint info initscripts irssi
  j2re1.4-mozilla-plugin klogd lame language-pack-de language-pack-de-base
  language-pack-en language-pack-en-base language-pack-gnome-de
  language-pack-gnome-de-base language-pack-gnome-en
  language-pack-gnome-en-base language-selector language-selector-common
  launchpad-integration less lftp libaa1 libaspell15 libatk1.0-0 libatspi1.0-0
  libaudio2 libavahi-client3 libavahi-glib1 libbeagle0 libbeecrypt6
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbtctl2 libc6-i686
  libcairo-java libcairo2 libcamel1.2-8 libcroco3 libcupsimage2 libcupsys2
  libcurl3-gnutls libdbus-1-3 libdbus-glib-1-2 libdc0c2 libdjvulibre15 libdmx1
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libedit2 libeel2-2
  libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libfaac0
  libfontconfig1 libfontenc1 libfreetype6 libfs6 libgail-common
  libgail-gnome-module libgail17 libgamin0 libgc1c2 libgcc1 libgcj7-awt
  libgconf2-4 libgcrypt11 libgd2-noxpm libgda2-3 libgda2-common libgdl-1-0
  libgdl-1-common libggi2 libgii0 libgii0-target-x libgimp2.0 libgksu1.2-1
  libgksuui1.0-1 libgl1-mesa libgl1-mesa-dri libglade2-0 libglew1 libglib-java
  libglib-perl libglib2.0-0 libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa
  libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2
  libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common
  libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0 libgnomecups1.0-1
  libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra
  libgnutls12 libgnutls13 libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpod0
  libgsf-1-113 libgsf-1-114 libgstreamer-gconf0.8-0
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins0.8-0 libgstreamer0.10-0
  libgstreamer0.8-0 libgtk-java libgtk-jni libgtk1.2 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15
  libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtkspell0 libgtop2-7
  libgucharmap4 libgutenprintui2-1 libice6 libicu34 libid3-3.8.3c2a libidl0
  liblaunchpad-integration0 libldap2 liblpint-bonobo0 libmagick9 libmdbtools
  libmetacity0 libmodplug0c2 libmp4v2-0 libmusicbrainz4c2a libmyspell3c2
  libnautilus-burn3 libnautilus-extension1 libncurses5 libneon25 libnotify1
  libopal-2.2.0 libopencdk8 liborbit2 libpam-modules libpanel-applet2-0
  libpango1.0-0 libpango1.0-common libpisock8 libpisync0 libpoppler1
  libpoppler1-glib libpopt0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l
  libpt-plugins-v4l2 libqt3-mt libraptor1 librasqal0 librdf0 libreadline5
  librpm4 librsvg2-2 librsvg2-common libsane libscim8c2a libscrollkeeper0
  libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsepol1 libsexy2
  libsidplay1 libsigc++-2.0-0c2a libsm6 libsmbclient libsoup2.2-8
  libstartup-notification0 libstdc++5 libstdc++6 libstlport4.6c2 libswfdec0.3
  libswt3.1-gtk-java libswt3.1-gtk-jni libtag1c2a libtasn1-3
  libtotem-plparser1 libuniconf4.2 libvte4 libwmf0.2-7 libwnck18 libwpd8c2a
  libwvstreams4.2-base libwvstreams4.2-extras libwxgtk2.6-0 libx11-6 libxau6
  libxaw7 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxfont1
  libxft1 libxft2 libxi6 libxinerama1 libxkbfile1 libxklavier10 libxml2
  libxml2-utils libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxmu6 libxmuu1
  libxosd2 libxp6 libxplc0.3.13 libxpm4 libxrandr2 libxrender1 libxres1
  libxslt1.1 libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxvmc1 libxxf86dga1
  libxxf86misc1 libxxf86vm1 linux-386 linux-headers-2.6.15-26
  linux-headers-2.6.15-26-386 linux-headers-2.6.15-27
  linux-headers-2.6.15-27-386 linux-headers-386 linux-image-2.6.15-26-386
  linux-image-2.6.15-27-386 linux-image-386
  linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-2.6.15-27-386 linux-restricted-modules-386
  linux-source linux-source-2.6.15 listres login logrotate lsb-base
  lsb-release lshw lvm-common lvm2 man-db mdadm mesa-utils metacity
  module-init-tools mozilla-browser mozilla-mplayer mozilla-thunderbird
  mplayer msttcorefonts mtr-tiny nautilus nautilus-cd-burner nautilus-data
  nautilus-sendto ncurses-base ncurses-bin nerolinux netbase nmap
  notification-daemon ntpdate nvidia-kernel-common oclock openssh-client
  openssh-server parted passwd pcmcia-cs pcmciautils pnm2ppa poppler-utils
  popularity-contest powermanagement-interface powernowd ppp pppconfig
  pppoeconf procps psmisc python python-adns python-apt python-cddb
  python-clientcookie python-crypto python-ctypes python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-epydoc python-eunuchs python-examples python-gadfly python-gd
  python-gdbm python-genetic python-geoip python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-gnupginterface python-gst0.10 python-gtk2 python-htmlgen
  python-htmltmpl python-id3lib python-imaging python-imaging-sane
  python-jabber python-kjbuckets python-launchpad-integration python-ldap
  python-libxml2 python-mutagen python-mysqldb python-netcdf python-newt
  python-numeric python-pam python-parted python-pexpect python-pgsql
  python-pisock python-pqueue python-pyao python-pylibacl python-pymad
  python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-tk python-unit python-vte python-xdg python-xml
  python-xmpp python2.4 python2.4-adns python2.4-apt python2.4-cairo
  python2.4-clientcookie python2.4-crypto python2.4-ctypes python2.4-dbus
  python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop
  python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 python2.4-htmlgen
  python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane
  python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf
  python2.4-libxml2 python2.4-libxslt1 python2.4-mysqldb python2.4-numeric
  python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl
  python2.4-pylibacl python2.4-pymad python2.4-pyopenssl python2.4-pyorbit
  python2.4-pyxattr python2.4-reportlab python2.4-simpletal python2.4-soappy
  python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml
  python2.4-xmpp rar rdesktop reiser4progs reportbug rhythmbox rpm rss-glx
  rsync samba-common scim scim-gtk2-immodule scim-modules-socket screen
  screensaver-default-images scrollkeeper serpentine shared-mime-info skype
  slocate smbclient smproxy sound-juicer ssh ssh-askpass-gnome sudo synaptic
  sysklogd sysvinit tangerine-icon-theme tango-icon-theme-common telnet
  thunderbird-locale-de thunderbird-locale-en-gb tk8.4 toshset tsclient
  ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts
  ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gentium
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg
  ubuntu-artwork ubuntu-base ubuntu-docs ubuntu-keyring ubuntu-minimal
  ubuntu-standard udev unattended-upgrades unixodbc update-manager
  update-notifier util-linux valknut viewres vim vino vlc vlc-plugin-alsa
  vnc-common w32codecs w3m whiptail wifi-radar wine wpasupplicant wvdial wxvlc
  x-ttcidfont-conf x-window-system-core x11-common x11perf xauth xbase-clients
  xbiff xcalc xchat-gnome xclipboard xclock xconsole xcursorgen xditview
  xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-scalable xfonts-utils xfontsel xfsprogs xgamma xgc xhost
  xinit xkbutils xkeyboard-config xkill xload xlogo xlsatoms xlsclients
  xlsfonts xmag xman xmessage xmodmap xmore xpmutils xprop xrandr xrdb
  xrefresh xsane xscreensaver-data xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-driver-all xserver-xorg-driver-apm
  xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-chips
  xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev
  xserver-xorg-driver-glint xserver-xorg-driver-i128 xserver-xorg-driver-i740
  xserver-xorg-driver-i810 xserver-xorg-driver-imstt xserver-xorg-driver-mga
  xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-sis xserver-xorg-driver-sisusb xserver-xorg-driver-tdfx
  xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-all xserver-xorg-input-elographics
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xset xsetmode xsetpointer xsetroot xsltproc xsm
  xstdcmap xterm xtrap xutils xvidtune xvinfo xvncviewer xwd xwininfo xwud
  zenity
The following packages will be DOWNGRADED:
  libc6
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libgcc1 (due to apt) libstdc++6 (due to apt) base-files libpam-modules
  (due to base-files) bash debianutils (due to bash) libncurses5 (due to bash)
  coreutils libselinux1 (due to coreutils) dpkg gzip login ncurses-base
  ncurses-bin sysvinit initscripts (due to sysvinit) util-linux lsb-base (due
  to util-linux)
0 upgraded, 0 newly installed, 1 downgraded, 839 to remove and 0 not upgraded.
Need to get 4588kB of archives.
After unpacking 1967MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]

---

### Post by Peterchen Brot on 2006-09-28
Shit means that gtk looks like a very early version.

---

