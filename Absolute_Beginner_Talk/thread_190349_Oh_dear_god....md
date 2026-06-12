---
title: "Oh dear god..."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-06-06
While trying to get wireless working I manually installed libc6 to try and get bcm43xx-fwcutter working but it failed.

The problem is though that I need to clean this up with sudo apt-get install -f.

The problem is though that this is what ...install -f will do:

```
god@Callum:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  3ddesktop aalib1 acpi acpi-support acpid acroread adduser akode alsa-base
  alsa-utils amule anacron angband apmd appres apt apt-utils aptitude
  artsbuilder aspell aspell-en at atanks audacity base-config base-files
  base-passwd bash bc bcm43xx-fwcutter beagle beforelight bicyclerepair bind9
  bind9-host binfmt-support binutils binutils-static bitmap bittornado
  bittornado-gui bittorrent blt bluez-cups bluez-pcmcia-support bluez-pin
  bluez-utils bogofilter bogofilter-bdb bos bsdmainutils bsdutils bsh
  bug-buddy bzip2 cabextract capplets-data cdda2wav cdparanoia cdrdao cdrecord
  comix console-common console-data console-tools contact-lookup-applet
  coreutils cowsay cpio cpp cpp-3.4 cpp-4.0 cron cupsys cupsys-bsd
  cupsys-client cupsys-driver-gimpprint cupsys-driver-gimpprint-data dash dbus
  dbus-1-utils dc dcpp debconf debconf-i18n debconf-utils debhelper
  debianutils defoma desktop-file-utils dhcdbd dhcp3-client dhcp3-common
  dialog dictionaries-common diff discover1 diveintopython dmidecode dmsetup
  dnsutils doc-base docbook-xml dosfstools dpkg dpkg-dev dselect dvd+rw-tools
  dvdrip e2fslibs e2fsprogs easytag ed editres eject eog esound ethtool evince
  evms evms-ncurses evolution evolution-data-server evolution-exchange
  evolution-plugins evolution-webcal faac faad fastjar fdutils fetchmail
  ffmpeg file file-roller findutils finger firefox firefox-gnome-support
  flashplayer-mozilla flashplugin-nonfree fontconfig foomatic-db
  foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters
  foomatic-filters-ppds fortune-mod fortunes-min fping freeciv-client-gtk
  freeciv-server freeglut3 fstobdf ftp gaim gamin gawk gcalctool gcc gcc-3.4
  gcc-4.0 gconf-editor gconf2 gdb gdesklets gdesklets-data gdm gedit gettext
  gettext-base gftp gftp-common gftp-gtk gftp-text gij gij-4.0 gimp gimp-gap
  gimp-python gksu gmail-notify gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-bluetooth gnome-btdownload gnome-control-center
  gnome-cups-manager gnome-doc-utils gnome-games gnome-keyring gnome-media
  gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-splashscreen-manager gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-themes gnome-utils gnome-volume-manager
  gnome2-user-guide gnomebaker gnomemeeting gnupg grep grepmap groff-base grub
  gs-common gs-esp gsfonts gsfonts-x11 gstreamer0.8-a52dec gstreamer0.8-aa
  gstreamer0.8-alsa gstreamer0.8-artsd gstreamer0.8-audiofile
  gstreamer0.8-caca gstreamer0.8-cdio gstreamer0.8-cdparanoia gstreamer0.8-dv
  gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-faad gstreamer0.8-festival
  gstreamer0.8-ffmpeg gstreamer0.8-flac gstreamer0.8-gnomevfs gstreamer0.8-gsm
  gstreamer0.8-gtk gstreamer0.8-hermes gstreamer0.8-jack gstreamer0.8-jpeg
  gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-mikmod gstreamer0.8-misc
  gstreamer0.8-mms gstreamer0.8-mpeg2dec gstreamer0.8-musepack
  gstreamer0.8-oss gstreamer0.8-pitfdll gstreamer0.8-plugin-apps
  gstreamer0.8-plugins gstreamer0.8-sdl gstreamer0.8-sid gstreamer0.8-speex
  gstreamer0.8-swfdec gstreamer0.8-theora gstreamer0.8-tools
  gstreamer0.8-vorbis gstreamer0.8-x gthumb gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-industrial gtk2-engines-lighthouseblue
  gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6
  guile-1.6-libs gzip hal hal-device-manager hdparm hermes1 hostname
  hotkey-setup hotplug hpijs hplip-base hplip-data html2text hwdb-client
  hydrogen iceauth ico ifrename ifupdown ijsgimpprint imagemagick imake info
  initng initramfs-tools initscripts intltool-debian iproute iptables
  iputils-arping iputils-ping iputils-tracepath irssi-text jackd
  java-gcj-compat jfsutils k3b k3blibs kasteroids kbattleship kcontrol
  kdebase-bin kdebase-kio-plugins kdebluetooth kdelibs-bin kdelibs4c2 kdesktop
  kfind khelpcenter klogd konqueror ktuberling lame lame-extras
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base language-selector language-support-en
  laptop-detect laptop-mode launchpad-integration less lesstif-bin lesstif1
  lesstif2 lftp liba52-0.7.4 libaa1 libacl1 libadns1 liballegro4.1 libao2
  libapm1 libart-2.0-2 libarts1c2 libartsc0 libasound2 libaspell15
  libatk1-ruby libatk1.0-0 libatm1 libattr1 libaudio2 libaudiofile0
  libavc1394-0 libbind9-0 libblkid1 libbluetooth1 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbtctl2 libbz2-1.0 libc6 libc6-dev
  libc6-i686 libcairo2 libcamel1.2-6 libcap1 libcdio3 libcdparanoia0
  libclamav1 libcomerr2 libcommons-cli-java libcompfaceg1 libconsole libcroco3
  libcupsimage2 libcupsys2-gnutls10 libcurl3 libdb1-compat libdb3 libdb4.2
  libdb4.3 libdbus-1-1 libdbus-1-cil libdbus-glib-1-1 libdbus-qt-1-1c2
  libdc1394-13 libdevmapper1.01 libdirectfb-0.9-22 libdiscover1 libdjvulibre15
  libdns20 libdrm1 libdv4 libdvbpsi3 libdvdcss2 libdvdnav4 libdvdread3
  libdvdread3-dev libebook1.2-5 libecal1.2-3 libedata-book1.2-2
  libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-6 libedit2
  libeel2-2 libegroupwise1.2-8 libelfg0 libesd-alsa0 libevent-perl libevms-2.5
  libevolution-cil libexchange-storage1.2-0 libexif12 libexpat1 libfaac0
  libfaad2-0 libfame-0.9 libflac++5c2 libflac7 libfontconfig1 libfontenc1
  libfreetype6 libfribidi0 libfs6 libgail-common libgail17 libgamin0 libgc1c2
  libgcc1 libgcj6 libgcj6-common libgconf-cil libgconf2-4 libgconf2-ruby
  libgconf2.0-cil libgcrypt11 libgd1-noxpm libgd2-noxpm libgda2-3
  libgda2-common libgdbm3 libgdchart-gd1-noxpm libgdk-pixbuf2
  libgdk-pixbuf2-ruby libgecko2.0-cil libgeoip1 libggi2 libgii0
  libgii0-target-x libgimp2.0 libgimpprint1 libgksu1.2-0 libgksuui1.0-0
  libgl1-mesa libgl1-mesa-dri libglade-cil libglade2-0 libglade2-ruby
  libglade2.0-cil libgle3 libglib-cil libglib-perl libglib1.2 libglib2-ruby
  libglib2.0-0 libglib2.0-cil libglib2.0-data libglide2 libglu1-mesa libglut3
  libgmime2.1 libgmime2.1-cil libgmp3c2 libgmpxx3 libgnome-cil
  libgnome-desktop-2 libgnome-keyring0 libgnome-menu2 libgnome-pilot2
  libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnomebt0 libgnomecanvas2-0
  libgnomecups1.0-1 libgnomecupsui1.0-1 libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgnucrypto-java libgnujaxp-java libgnujaxp-jni libgnutls11 libgpg-error0
  libgphoto2-2 libgphoto2-port0 libgpmg1 libgsf-1 libgsl0 libgsm1
  libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0
  libgtk-cil libgtk-perl libgtk-pixbuf-perl libgtk1.2 libgtk2-perl
  libgtk2-ruby libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common
  libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview1.0-0 libgtkspell0 libgtop2-5
  libgucharmap4 libguile-ltdl-1 libhal-storage1 libhal1 libhsqldb-java libice6
  libid3-3.8.3c2 libid3tag0 libidl0 libidn11 libieee1284-3 libijs-0.35
  libimlib2 libintl-perl libisc9 libisccc0 libisccfg1 libiso9660-3 libiw28
  libjack0.80.0-0 libjasper-1.701-1 libjaxp1.2-java libjessie-java libjpeg62
  libkdeedu1 libkdegames1 libkonq4 libkpathsea3 libkrb53 liblame0
  liblaunchpad-integration0 liblcms1 libldap2 liblircclient0 liblo0
  liblocale-gettext-perl liblockdev1 liblog4j1.2-java liblpint-bonobo0
  liblrdf0 libltdl3 liblua50 liblualib50 liblwres1 liblzo1 libmad0 libmagic1
  libmagick6 libmdbtools libmetacity0 libmikmod2 libmjpegtools0 libmms0
  libmng1 libmodplug0c2 libmono0 libmp4v2-0 libmpcdec3 libmpeg2-4 libmudflap0
  libmudflap0-dev libmusicbrainz2c2 libmusicbrainz4c2 libmyspell3c2
  libmysqlclient12 libmysqlclient14 libnautilus-burn2 libnautilus-extension1
  libncurses5 libncursesw5 libneon24 libnetpbm10 libnetpbm9 libnewt0.51
  libnotify0 libnspr4 libnss3 libogg0 liboggflac3 liboil0.3 libopenal0
  libopencdk8 libopenexr2c2 libopenh323-1.15.3c2 libopenobex-1.0-0 liborbit2
  libpam-modules libpam0g libpanel-applet2-0 libpango1-ruby libpango1.0-0
  libpango1.0-common libpaper1 libparted1.6-12 libpcap0.8 libpcre3 libperl5.8
  libphysfs-1.0-0 libpisock8 libpisync0 libpng10-0 libpng12-0 libpolyp0
  libpoppler0c2 libpoppler0c2-glib libpopt0 libportaudio0 libpq4 libpt-1.8.3c2
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libpvm3 libqt3-mt
  libqthreads-12 libquicktime1 libraptor1 librasqal0 libraw1394-5 librdf0
  libreadline4 libreadline5 librecode0 libreiserfs0.3-0 librexml-ruby librpm4
  librsvg2-2 librsvg2-common libruby libruby1.8 libsamplerate0 libsane
  libsasl2 libsasl2-modules libscrollkeeper0 libsdl-image1.2 libsdl-mixer1.2
  libsdl-net1.2 libsdl1.2debian libsdl1.2debian-oss libselinux1
  libservlet2.3-java libshout3 libsidplay1 libsigc++-1.2-5c2 libslang2 libslp1
  libsm6 libsmbclient libsmjs1 libsmpeg0c2 libsndfile1 libsnmp5 libsoup2.2-8
  libspeex1 libsqlite0 libsqlite3-0 libss2 libssl0.9.7
  libstartup-notification0 libstdc++5 libstdc++6 libstlport4.6c2 libsvga1
  libswfdec0.3 libswt-gtk-3.1-java libswt-gtk-3.1-jni libsysfs1 libtag1c2
  libtagc0 libtar libtasn1-2 libterm-size-perl libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtheora0 libtiff4
  libtotem-plparser0 libtse3-0.2.7c2 libtunepimp-bin libtunepimp2c2 libungif4g
  libunicode-string-perl libusb-0.1-4 libuuid1 libvcdinfo0 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvte4 libwmf0.2-7 libwnck18 libwpd8c2
  libwrap0 libwvstreams4.0c2-base libwvstreams4.0c2-extras libwxgtk2.4-1
  libwxgtk2.6-0 libx11-6 libxalan2-java libxau6 libxaw7 libxcursor1
  libxdamage1 libxdmcp6 libxerces2-java libxext6 libxfixes3 libxft2 libxi6
  libxine1c2 libxinerama1 libxkbfile1 libxklavier10 libxml2 libxml2-utils
  libxmu6 libxmuu1 libxosd2 libxp6 libxplc0.3.11c2 libxpm4 libxrandr2
  libxrender1 libxres1 libxslt1.1 libxss1 libxt-java libxt6 libxtrap6 libxtst6
  libxv1 libxvidcore4 libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-386
  linux-image-2.6.12-10-386 linux-image-2.6.12-9-386 linux-image-386
  linux-restricted-modules-2.6.12-10-386 linux-restricted-modules-2.6.12-9-386
  linux-restricted-modules-386 linux-restricted-modules-common
  linux-sound-base listres locales login logrotate lsb-base lshw lsof ltrace
  lvm-common lvm2 make makedepend makedev man-db mawk mdadm menu mesa-utils
  metacity mii-diag mkisofs module-assistant module-init-tools mono-common
  mono-jit mount mozilla-acroread mozilla-firefox-locale-en-gb mozilla-mplayer
  mplayer-386 mplayer-fonts msttcorefonts mtr-tiny myspell-de-de myspell-en-gb
  myspell-en-us nano nautilus nautilus-cd-burner nautilus-data nautilus-sendto
  ncurses-base ncurses-bin ndisgtk ndiswrapper-source ndiswrapper-utils
  net-tools netbase netcat netcdfg3 netpanzer netpbm network-manager
  notification-daemon ntpdate nvidia-kernel-common oclock odbcinst1debian1
  openoffice.org-debian-files openoffice.org2 openoffice.org2-base
  openoffice.org2-calc openoffice.org2-common openoffice.org2-core
  openoffice.org2-draw openoffice.org2-evolution openoffice.org2-gnome
  openoffice.org2-impress openoffice.org2-java-common
  openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer
  openssh-client opera parted passwd patch pciutils pcmcia-cs pdmenu perl
  perl-base perl-modules pkg-config planetpenguin-racer pmidi pmount pnm2ppa
  po-debconf popularity-contest powermanagement-interface powermgmt-base
  powernowd ppp pppconfig pppoeconf procmail procps psmisc python python-adns
  python-apt python-cddb python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-epydoc python-eunuchs python-examples
  python-gadfly python-gd python-gdbm python-gdchart python-genetic
  python-geoip python-glade2 python-gmenu python-gnome2 python-gnome2-extras
  python-gnupginterface python-gst python-gtk2 python-htmlgen python-htmltmpl
  python-id3lib python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-launchpad-integration python-ldap python-minimal
  python-musicbrainz python-mysqldb python-netcdf python-newt python-numeric
  python-osd python-pam python-parted python-pexpect python-pgsql
  python-pisock python-pqueue python-pyao python-pylibacl python-pyogg
  python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-tk python-unit python-uno python-vte python-wxgtk2.6
  python-xdg python-xml python-xmpp python2.4 python2.4-adns python2.4-apt
  python2.4-cairo python2.4-clientcookie python2.4-crypto python2.4-dbus
  python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras
  python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-libbtctl python2.4-librdf
  python2.4-libxml2 python2.4-libxslt1 python2.4-minimal python2.4-musicbrainz
  python2.4-mysqldb python2.4-numeric python2.4-osd python2.4-pam
  python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl
  python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab
  python2.4-simpletal python2.4-sqlite python2.4-syck python2.4-tk
  python2.4-unit python2.4-xml python2.4-xmpp qobex rar rdesktop reiser4progs
  reiserfsprogs reportbug rhythmbox rpm rss-glx rsync ruby ruby1.8
  samba-common sane-utils scorched3d screen scrollkeeper sed serpentine
  sessreg sgml-base sgml-data shared-mime-info skype slang1 slocate smbclient
  smeg smproxy sound-juicer ssh-askpass-gnome strace stratagus streamripper
  streamtuner subtitleripper sudo sun-j2re1.5 synaptic sysklogd sysvinit tar
  tcl8.4 tcpd tcpdump telnet texinfo time timidity tk8.4 tomboy toolame
  toshset totem totem-xine transcode tsclient ttf-arabeyes ttf-arphic-bkai00mp
  ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-baekmuk
  ttf-bengali-fonts ttf-bitstream-vera ttf-devanagari-fonts ttf-freefont
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ubuntu-artwork
  ubuntu-desktop ubuntu-docs ubuntu-keyring ubuntu-minimal ubuntu-standard
  udev unace unrar-nonfree unzip update-manager update-notifier usbutils
  usplash util-linux vbetool vcdimager viewres vim vim-common vino vlc
  vnc-common w32codecs w3m wamerican wbritish wget whiptail whois wifi-radar
  wine wireless-tools wpasupplicant wvdial wxvlc x-ttcidfont-conf
  x-window-system-core x11perf xauth xbase-clients xbiff xbindkeys
  xbindkeys-config xcalc xchat xchat-common xclipboard xclock xconsole
  xcursorgen xdesktopwaves xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils xfontsel
  xfsprogs xgamma xgc xhost xinit xkbutils xkill xload xlogo xlsatoms
  xlsclients xlsfonts xmag xman xmessage xmkmf xml-core xmms xmodmap xmore
  xorg-common xorg-driver-synaptics xpmutils xprop xrandr xrdb xrefresh
  xresprobe xrgb xsane xscreensaver xscreensaver-data xscreensaver-gl
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-driver-apm
  xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-chips
  xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev
  xserver-xorg-driver-glide xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt
  xserver-xorg-driver-mga xserver-xorg-driver-neomagic
  xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-acecad xserver-xorg-input-aiptek
  xserver-xorg-input-calcomp xserver-xorg-input-citron
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc
  xserver-xorg-input-dynapro xserver-xorg-input-elographics
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom
  xset xsetmode xsetpointer xsetroot xsltproc xsm xstdcmap xterm xtrap xutils
  xvidtune xvinfo xvncviewer xwd xwininfo xwud yelp zenity zip zlib1g zsnes
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt)
  base-files mawk (due to base-files) base-passwd (due to base-files) bash
  passwd (due to bash) libncurses5 (due to bash) bsdutils coreutils libacl1
  (due to coreutils) debianutils diff dpkg e2fsprogs e2fslibs (due to
  e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2
  (due to e2fsprogs) libuuid1 (due to e2fsprogs) findutils grep gzip hostname
  login libpam-modules (due to login) libpam0g (due to login) mount
  ncurses-base ncurses-bin perl-base python-minimal python2.4-minimal (due to
  python-minimal) sed sysvinit initscripts (due to sysvinit) tar util-linux
  lsb-base (due to util-linux) libslang2 (due to util-linux) zlib1g (due to
  util-linux)
0 upgraded, 0 newly installed, 1261 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2245MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]

```

That wouldn't be a happy situation losing over 2GB of things from my computer that I have no idea what half of them do and they're probably quite important.


Please help!

Please!

---

### Post by dmizer on 2006-06-06
if you manually installed it, you can't remove it through apt-get.

what did you do to install it?

---

### Post by Dr Von Bon Bon on 2006-06-06
I downloaded a deb file and then double clicked it.

I think I did a program or followed a guide a while ago that meant .deb's will automatically install when I double click them called dblclk123 which runs:

sudo dpkg -i

on the package.

---

### Post by bruce89 on 2006-06-06
You need to downgrade to the Dapper verison - use Synaptic and find libc6.  Press Contol+E, and force the Dapper one.  Why did you need a 3rd party libc?

---

### Post by Dr Von Bon Bon on 2006-06-06
Oh thank god for that.

Thank you loads, that was brilliant.

I couldn't get bcm43xx-fwcutter to work and I would like to get my wireless working properly and it said I needed libc6 so I downloaded it and installed it but it tried to kill my computer.

Again, thanks loads.

---

### Post by thingy on 2006-08-04
<take this as advice and not criticism>

In the future, don't mess about installing new versions of *vital* system libraries like libc. The reason you got the huge list of apps that apt was going to remove, was that *each* of those apps use libc. It's a standard library that a lot of things rely on and you really shouldn't be messing with it.

I'm surprised that installing a foreign libc deb on your system didn't hose it completely...i.e. you'd get library errors trying to do anything.

Just be careful...ask questions here or on IRC...experimenting is a good way to gain experience as long as you are careful and methodical(research what you're trying to do and take precautions)

---

