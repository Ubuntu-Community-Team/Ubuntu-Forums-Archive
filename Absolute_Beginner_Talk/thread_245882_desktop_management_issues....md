---
title: "desktop management issues..."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by theadventuresofanidealist on 2006-08-28
i dont know what i have managing the desktop.
i know i disabled xfce, but i get some problems anyway, check thumbnails below.
im a total newbie, so i have no idea what to do.
everytime i load xfapps, my screen goes black, why is that?
does it start managing the desktop?
im running xubuntu on a sony vaio pcg-fx340.

---

### Post by Metacarpal on 2006-08-28
Did you start with an Xubuntu install and add Gnome, or vice-versa?  What steps did you take to add the other desktop?

---

### Post by theadventuresofanidealist on 2006-08-28
i know i did a xubuntu install, but as for gnome i have no idea how i installed it.

---

### Post by Metacarpal on 2006-08-28
Okay, sounds like the Gnome install is a bit broken.  Hopefully this will fix your problem.

First, we'll need to remove whatever bits of Gnome are on your system.  Open a Terminal and copy/paste the following (all in one go):
```
sudo apt-get remove alacarte app-install-data app-install-data-commercial at-spi bicyclerepair bittorrent blt bluez-cups bluez-pcmcia-support bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy ca-certificates capplets-data contact-lookup-applet deskbar-applet diveintopython ekiga eog esound esound-common evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal fastjar festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gdb gedit gedit-common gij-4.1 gimp-python gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-lighthouseblue gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client java-common java-gcj-compat libadns1 libatspi1.0-0 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1 libavc1394-0 libbeagle0 libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcurl3 libcurl3-gnutls libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libesd-alsa0 libestools1.2 libexchange-storage1.2-1 libflac7 libgail-common libgail-gnome-module libgail17 libgcj-common libgcj7 libgcj7-jar libgd2-noxpm libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgeoip1 libglew1 libglib-perl libgmp3c2 libgnome-desktop-2 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgphoto2-2 libgphoto2-port0 libgpod0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libhsqldb-java libicu34 libid3-3.8.3c2a libidn11 libieee1284-3 libjasper-1.701-1 libjaxp1.2-java libjessie-java libjline-java liblircclient0 liblpint-bonobo0 libmagick9 libmdbtools libmetacity0 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libneon25 libnetcdf3 libnotify1 liboil0.3 libopal-2.2.0 libopenobex-1.0-0 libpanel-applet2-0 libpisock8 libpisync0 libportaudio0 libpq4 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraptor1 librasqal0 libraw1394-5 librdf0 libsane libsdl1.2debian libsdl1.2debian-alsa libservlet2.3-java libsexy2 libshout3 libsmbclient libsndfile1 libsoup2.2-8 libsqlite0 libsqlite3-0 libstlport4.6c2 libtotem-plparser1 libvorbisenc2 libvorbisfile3 libwnck-common libwnck18 libxalan2-java libxerces2-java libxklavier10 libxml2-utils libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxres1 libxt-java metacity mysql-common nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-writer openssl pkg-config python-adns python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-launchpad-integration python-ldap python-libxml2 python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4-adns python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-mysqldb python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-simpletal python2.4-soappy python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml python2.4-xmpp rdesktop rhythmbox rss-glx screensaver-default-images serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tcl8.4 tk8.4 totem totem-gstreamer tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs update-notifier vino vnc-common whois xsane xsane-common xsltproc xvncviewer yelp zenity
```

Then, enter the following:
```
sudo aptitude install ubuntu-desktop
```

And then, just to make sure all your XFCE apps are there, do:
```
sudo aptitude install xubuntu-desktop
```

Let me know how it goes!

---

### Post by theadventuresofanidealist on 2006-08-28
the thing is i want to keep gnome as my desktop manager and not xfce. how do i do that?

---

### Post by Metacarpal on 2006-08-28
EDIT: Are you currently logging in into gnome?  If so, just do this step, not my previous stuff.  If you're still finding yourself logged into XFCE, then you'll need to do all but the last step of my previous post first... [end Edit]

Ah, well then.

Follow my previous steps ('cause it sounds like you're still having partial-gnome problems), but after you install ubuntu-desktop, then reboot the computer (don't re-install xubuntu-desktop).  When you get to the login screen, click Session and choose Gnome.

After logging in, open Terminal (Applications > Accessories > Terminal) and paste in the following (again, all in one go):
```
sudo apt-get remove abiword abiword-common abiword-help abiword-plugins anthy gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce im-switch latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libbeecrypt6 libchewing-data libchewing2 libenchant1c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-1-common libgoffice-gtk-1-2 libgsf-gnome-1-113 libgtkmathview0c2a libjpeg-progs libmodplug0c2 libots0 libpcre3 librpm4 libt1-5 libtagc0 libthunar-vfs-1 libwpd-stream8c2a libxcomposite1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine-main1 libxvmc1 mousepad mozilla-thunderbird orage rpm scim-anthy scim-chewing scim-hangul scim-pinyin thunar thunar-media-tags-plugin xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfmedia xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs
```

That should do it!

---

### Post by theadventuresofanidealist on 2006-08-28
how do i know which one im logged into?
ive unchecked the let xfce manage my desktop.

---

### Post by Metacarpal on 2006-08-28
> **theadventuresofanidealist said:**
> how do i know which one im logged into?
ive unchecked the let xfce manage my desktop.

Reboot, and at the login screen, click "session".  If xfce is listed, then it's still installed.  Also, you can tell by the splash screen as your desktop loads: if it's a rectangle labeled "Ubuntu" with stuff happening at the bottom, you're logging into Gnome.  If it's a mouse in a wheel, that's xfce

---

### Post by theadventuresofanidealist on 2006-08-28
thanks.
this is taking awhile, so i will get back to u as soon as it finishes.

---

### Post by theadventuresofanidealist on 2006-08-28
as i typed sudo aptitude install ubuntu desktop, this message appeared:


Need to get 244MB/351MB of archives. After unpacking 1143MB will be used.
The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.14.0-0ubuntu11 is to be installed.
  evince-gtk: Conflicts: evince but 0.5.2-0ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
bsh [Not Installed]
evince [Not Installed]
gnome-system-tools [Not Installed]
openoffice.org [Not Installed]
openoffice.org-base [Not Installed]
openoffice.org-evolution [Not Installed]
openoffice.org-java-common [Not Installed]
openoffice.org-writer [Not Installed]
ubuntu-desktop [Not Installed]Need to get 244MB/351MB of archives. After unpacking 1143MB will be used.
The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.14.0-0ubuntu11 is to be installed.
  evince-gtk: Conflicts: evince but 0.5.2-0ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
bsh [Not Installed]
evince [Not Installed]
gnome-system-tools [Not Installed]
openoffice.org [Not Installed]
openoffice.org-base [Not Installed]
openoffice.org-evolution [Not Installed]
openoffice.org-java-common [Not Installed]
openoffice.org-writer [Not InstalNeed to get 244MB/351MB of archives. After unpacking 1143MB will be used.
The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.14.0-0ubuntu11 is to be installed.
  evince-gtk: Conflicts: evince but 0.5.2-0ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
bsh [Not Installed]
evince [Not Installed]
gnome-system-tools [Not Installed]
openoffice.org [Not Installed]
openoffice.org-base [Not Installed]
openoffice.org-evolution [Not Installed]
openoffice.org-java-common [Not Installed]
openoffice.org-writer [Not Installed]
ubuntu-desktop [Not Installed]

Score is 73

Accept this solution? [Y/n/q/?]

led]
ubuntu-desktop [Not Installed]

Score is 73

Accept this solution? [Y/n/q/?]



Score is 73
Need to get 244MB/351MB of archives. After unpacking 1143MB will be used.
The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.14.0-0ubuntu11 is to be installed.
  evince-gtk: Conflicts: evince but 0.5.2-0ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
bsh [Not Installed]
evince [Not Installed]
gnome-system-tools [Not Installed]
openoffice.org [Not Installed]
openoffice.org-base [Not Installed]
openoffice.org-evolution [Not Installed]
openoffice.org-java-common [Not Installed]
openoffice.org-writer [Not Installed]
ubuntu-desktop [Not Installed]

Score is 73

Accept this solution? [Y/n/q/?]


Accept this solution? [Y/n/q/?]

do i accept or not?

---

### Post by theadventuresofanidealist on 2006-08-28
anyway i accepted, so im keeping my fingers crossed, while i wait til it finishes.

---

### Post by Metacarpal on 2006-08-28
Woof.  That's ugly.  Did you do the first removal step I recommended in post #4 in this thread?  You'd have to be logged in to XFCE to do it, but that should have gotten rid of all the gnome packages already on your system, so you could do a clean install of gnome using the 'sudo aptitude install ubuntu-desktop' command.

If you did that and it didn't work... Your best bet might be to back up your personal files, download an Ubuntu install CD, and start from scratch...

---

### Post by theadventuresofanidealist on 2006-08-28
you are the man!
cool gnome desktop, everything works like a charm!

---

### Post by Metacarpal on 2006-08-28
Excellent!  I'm glad I could help. :D

---

