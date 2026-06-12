---
title: "&quot;unmet dependencies&quot;?"
date: 2005-06-10
forum: Absolute Beginner Talk
---

### Post by diomedesxx on 2005-06-10
Upon attempting to install the J2SE Runtime Environment (JRE), I encounter this error. I also encounter this same kind of error with most apps I attempt to install.

josh@josh:~ $ sudo apt-get install sun-j2re1.5
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  smeg: Depends: python (>= 2.4) but 2.3.4-1ubuntu1 is to be installed
        Depends: python2.4-gtk2 (>= 2.5.4) but it is not going to be installed
        Depends: python-xdg (>= 0.9) but 0.5-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Any assistance would be greatly appreciated.

Thanks, 
Diomedes

---

### Post by Xian on 2005-06-10
What is the output of the following:

```
sudo apt-get -f install
```

---

### Post by diomedesxx on 2005-06-10
josh@josh:~ $ sudo apt-get -f install sun-j2re1.5
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  smeg: Depends: python (>= 2.4) but 2.3.4-1ubuntu1 is to be installed
        Depends: python2.4-gtk2 (>= 2.5.4) but it is not going to be installed
        Depends: python-xdg (>= 0.9) but 0.5-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
josh@josh:~ $

---

### Post by Xian on 2005-06-10
You only want to run the command with no package at the end.
Just as below:

```
$ sudo apt-get -f install
```

---

### Post by diomedesxx on 2005-06-10
Sory...Here is what came out:

josh@josh:~ $ sudo apt-get -f install
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  anacron apt apt-utils aptitude bicyclerepair cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data gaim gaim-data gimp gimp-data gimp-python
  libgcrypt11 libgimp2.0 libglade2-0 libgnutls11 libgtk2.0-0 libgtk2.0-bin
  libhal-storage0 libopencdk8 libparted1.6-12 libvte-common libvte4 libwnck16
  libxinerama1 libxosd2 libxss1 pymacs python python-adns python-apt
  python-cddb python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-eunuchs python-examples python-gadfly python-gd python-gdbm
  python-gdchart python-genetic python-geoip python-glade2
  python-gnupginterface python-gtk2 python-hip python-htmlgen python-htmltmpl
  python-id3lib python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-ldap python-minimal python-musicbrainz
  python-mysqldb python-netcdf python-numarray python-numeric python-osd
  python-pam python-parted python-pexpect python-pgsql python-pisock
  python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl
  python-pyorbit python-pyvorbis python-pyxattr python-reportlab
  python-simpletal python-soappy python-sqlite python-stats python-syck
  python-tk python-unit python-xdg python-xml python-xmpp python2.4
  python2.4-adns python2.4-clientcookie python2.4-crypto python2.4-dbus
  python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-eunuchs python2.4-examples
  python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip
  python2.4-glade2 python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl
  python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-minimal python2.4-musicbrainz
  python2.4-mysqldb python2.4-numarray python2.4-numeric python2.4-osd
  python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pylibacl
  python2.4-pymacs python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr
  python2.4-reportlab python2.4-simpletal python2.4-sqlite python2.4-syck
  python2.4-tk python2.4-twisted python2.4-twisted-bin python2.4-unit
  python2.4-xml python2.4-xmpp synaptic
Suggested packages:
  apt-doc vim-python idle gimpprint-doc gimpprint-locales libzephyr3
  gimp-help-en gimp-help libgimp-perl gimp-data-extras gnutls-bin
  libparted1.6-dev libparted1.6-i18n xfonts-base-transcoded python-doc
  python-profiler python-imaging-doc python-egenix-mxdatetime
  python-numarray-doc python-numeric-tutorial python-reportlab-doc
  python2.4-doc python-ldap-doc mysql-server pyopenssl-doc tix8.1
  python2.4-qt3 libwxgtk2.4-python twisted-doc python2.4-twisted-conch
  python2.4-profiler apt-watch
Recommended packages:
  aptitude-doc-en aptitude-doc gimp-svg deborphan libgnome2-perl
The following packages will be REMOVED:
  bug-buddy capplets contact-lookup-applet eog evolution evolution-data-server
  evolution-exchange evolution-webcal file-roller gcalctool gconf-editor gdm
  gedit gedit-common gnome-about gnome-applets gnome-applets-data
  gnome-control-center gnome-cpufreq-applet gnome-cups-manager gnome-games
  gnome-gv gnome-media gnome-netstatus-applet gnome-nettool gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils
  gnome-volume-manager gnomemeeting gthumb gtkhtml3.2 gucharmap
  hal-device-manager libbonoboui2-0 libeel2-2 libgal2.2-1 libgal2.2-common
  libgnome-desktop-2 libgnome2-0 libgnomecupsui1.0-1 libgnomeui-0
  libgtkhtml3.2-11 libgucharmap4 libnautilus2-2 libpanel-applet2-0 nautilus
  nautilus-cd-burner python-fixedpoint python-gnome2 python-mpz python-newt
  python2.3-gnome2 rhythmbox sound-juicer totem-gstreamer trashapplet tsclient
  ubuntu-desktop vino yelp
The following NEW packages will be installed:
  anacron cupsys-driver-gimpprint cupsys-driver-gimpprint-data gaim-data
  libgcrypt11 libgnutls11 libhal-storage0 libparted1.6-12 libwnck16
  libxinerama1 libxss1 python-minimal python2.4 python2.4-adns
  python2.4-clientcookie python2.4-crypto python2.4-dbus
  python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-eunuchs python2.4-examples
  python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip
  python2.4-glade2 python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl
  python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-minimal python2.4-musicbrainz
  python2.4-mysqldb python2.4-numarray python2.4-numeric python2.4-osd
  python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pylibacl
  python2.4-pymacs python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr
  python2.4-reportlab python2.4-simpletal python2.4-sqlite python2.4-syck
  python2.4-tk python2.4-twisted python2.4-twisted-bin python2.4-unit
  python2.4-xml python2.4-xmpp
The following packages will be upgraded:
  apt apt-utils aptitude bicyclerepair gaim gimp gimp-data gimp-python
  libgimp2.0 libglade2-0 libgtk2.0-0 libgtk2.0-bin libopencdk8 libvte-common
  libvte4 libxosd2 pymacs python python-adns python-apt python-cddb
  python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-eunuchs python-examples python-gadfly python-gd python-gdbm
  python-gdchart python-genetic python-geoip python-glade2
  python-gnupginterface python-gtk2 python-hip python-htmlgen python-htmltmpl
  python-id3lib python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-ldap python-musicbrainz python-mysqldb python-netcdf
  python-numarray python-numeric python-osd python-pam python-parted
  python-pexpect python-pgsql python-pisock python-pqueue python-pyao
  python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis
  python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite
  python-stats python-syck python-tk python-unit python-xdg python-xml
  python-xmpp synaptic
78 upgraded, 62 newly installed, 68 to remove and 102 not upgraded.
1 not fully installed or removed.
Need to get 35.6MB of archives.
After unpacking 161MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libgnutls11 1.0.16-13ubuntu 0.1 [293kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-minimal 2.4.1-0 [743kB]
Get:3 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main synaptic 0.56+r evertedto+officialhoary+0.55+cvs20050406-1~5.04ubp1 [1611kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4 2.4.1-0 [2782kB]
Get:5 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main libgimp2.0 2.2.7-1~5.04ubp1 [526kB]
Get:6 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gimp 2.2.7-1~5.04ubp1 [2988kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-syck 0.42-5ubuntu1 [42.2kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-syck 0.42-5ubuntu1 [6634B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-simpletal 3.9-1ubuntu2 [24.2kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-simpletal 3.9-1ubuntu2 [6906B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-xdg 0.9-1 [20.4kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pyogg 1.3-1ubuntu1 [16.4kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pyvorbis 1.3-1ubuntu1 [31.9kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-xmpp 0.1-rc4-1ubuntu3 [39.2kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-xmpp 0.1-rc4-1ubuntu3 [9810B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-xml 0.8.4-1ubuntu1 [699kB]
Get:17 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gimp-data 2.2.7-1~5.04ubp1 [6367kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-xml 0.8.4-1ubuntu1 [11.2kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-tk 2.4.1-0 [110kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-unit 1.4.1-9ubuntu3 [32.6kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-tk 2.4.1-0ubuntu2 [7024B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-unit 1.4.1-9ubuntu3 [6616B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-stats 0.6-5ubuntu1 [64.7kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-sqlite 1.0.1-1ubuntu1 [22.7kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-sqlite 1.0.1-1ubuntu1 [2680B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-soappy 0.11.3-1ubuntu1 [134kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-numeric 23.7-2ubuntu1 [99.2kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-numeric 23.7-2ubuntu1 [21.6kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-netcdf 2.4.9-1ubuntu2 [27.6kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-reportlab 1.19debian-0.2ubuntu2 [891kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-reportlab 1.19debian-0.2ubuntu2 [61.6kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pyxattr 0.2-2ubuntu3 [10.3kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pyxattr 0.2-2ubuntu3 [2796B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pylibacl 0.2.1-2ubuntu3 [21.5kB]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pylibacl 0.2.1-2ubuntu3 [2946B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pqueue 0.2-6ubuntu1 [12.2kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-egenix-mxtools 2.0.6-0ubuntu1 [86.5kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-egenix-mxdatetime 2.0.6-0ubuntu1 [104kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pgsql 2.4.0-5ubuntu2 [144kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pgsql 2.4.0-5ubuntu2 [17.4kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libparted1.6-12 1.6.20-0.exp.2ubuntu2 [199kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-parted 0.11.2ubuntu2 [20.9kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pam 0.4.2-10.1ubuntu3 [11.8kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pam 0.4.2-10.1ubuntu3 [4078B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libxinerama1 6.8.2-10 [177kB]
Get:46 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gimp-python 2.2.7-1~5.04ubp1 [118kB]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libxosd2 2.2.14-1ubuntu1 [25.0kB]
Get:48 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gaim-data 1:1.3.0-1~5.04ubp1 [2935kB]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-osd 0.2.6-1.1ubuntu3 [17.8kB]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-osd 0.2.6-1.1ubuntu3 [2672B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-numarray 1.1.1-3ubuntu1 [434kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-numarray 1.1.1-3ubuntu1 [1018B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-mysqldb 1.1.6-1ubuntu2 [42.5kB]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-mysqldb 1.1.6-1ubuntu2 [46.5kB]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-ldap 2.0.4-1ubuntu2 [61.9kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-ldap 2.0.4-1ubuntu2 [11.2kB]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-imaging 1.1.4-3ubuntu2 [232kB]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-imaging-sane 1.1.4-3ubuntu2 [36.2kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-imaging-sane 1.1.4-3ubuntu2 [21.4kB]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-imaging 1.1.4-3ubuntu2 [21.8kB]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-htmltmpl 1.22-5ubuntu2 [61.0kB]
Get:62 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gaim 1:1.3.0-1~5.04ubp1 [884kB]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-htmltmpl 1.22-5ubuntu2 [4350B]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libgtk2.0-0 2.6.4-0ubuntu3 [2043kB]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libgtk2.0-bin 2.6.4-0ubuntu3 [18.0kB]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-gtk2 2.6.1-0ubuntu2 [632kB]
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-gtk2 2.6.1-0ubuntu2 [59.3kB]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libglade2-0 1:2.5.1-0ubuntu1 [81.4kB]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-glade2 2.6.1-0ubuntu2 [47.0kB]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-glade2 2.6.1-0ubuntu2 [36.9kB]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-geoip 1.2.0-1ubuntu2 [2814B]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-geoip 1.2.0-1ubuntu2 [6496B]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-gdchart 0.6.1-8ubuntu2 [30.3kB]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-gd 0.52.0-0ubuntu1 [9126B]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-gd 0.52.0-0ubuntu1 [20.2kB]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-gdbm 2.4.1-0 [27.4kB]
Get:77 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-gdbm 2.4.1-0ubuntu2 [6898B]
Get:78 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-examples 2.4.1-0 [580kB]
Get:79 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-examples 2.4.1-0ubuntu2 [6910B]
Get:80 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-crypto 2.0+dp1-2ubuntu1 [115kB]
Get:81 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-crypto 2.0+dp1-2ubuntu1 [10.6kB]
Get:82 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-cddb 1.4-3ubuntu1 [15.9kB]
Get:83 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libvte4 1:0.11.12-0ubuntu2 [662kB]
Get:84 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libvte-common 1:0.11.12-0ubuntu2 [65.2kB]
Get:85 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main aptitude 0.2.15.8-1ubuntu12 [864kB]
Get:86 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python 2.4.1-0ubuntu2 [128kB]
Get:87 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-minimal 2.4.1-0ubuntu2 [954B]
Get:88 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-adns 1.0.0-6ubuntu3 [16.2kB]
Get:89 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-adns 1.0.0-6ubuntu3 [4548B]
Get:90 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pyorbit 2.0.1-1ubuntu5 [52.2kB]
Get:91 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pyorbit 2.0.1-1ubuntu5 [7116B]
Get:92 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pyopenssl 0.6-1ubuntu3 [41.9kB]
Get:93 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pyopenssl 0.6-1ubuntu3 [7048B]
Get:94 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pymacs 0.22-3ubuntu2 [39.6kB]
Get:95 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main pymacs 0.22-3ubuntu2 [235kB]
Get:96 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-id3lib 0.5.1-3ubuntu2 [23.3kB]
Get:97 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-id3lib 0.5.1-3ubuntu2 [9874B]
Get:98 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pyao 0.82-1ubuntu1 [9308B]
Get:99 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pisock 0.11.8-10ubuntu1 [33.8kB]
Get:100 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-pexpect 0.999-2ubuntu2 [16.2kB]
Get:101 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pexpect 0.999-2ubuntu2 [3100B]
Get:102 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-musicbrainz 2.0.2-10ubuntu1 [22.3kB]
Get:103 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-musicbrainz 2.0.2-10ubuntu1 [4758B]
Get:104 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe python-hip 0.1.2.1ubuntu1 [7346B]
Get:105 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-jabber 0.5.0-1ubuntu2 [92.5kB]
Get:106 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-jabber 0.5.0-1ubuntu2 [3810B]
Get:107 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-htmlgen 2.2.2-10ubuntu2 [74.1kB]
Get:108 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-htmlgen 2.2.2-10ubuntu2 [260kB]
Get:109 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-gnupginterface 0.3.2-4ubuntu3 [19.2kB]
Get:110 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-genetic 0.1.1b-3ubuntu1 [21.8kB]
Get:111 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-kjbuckets 1:1.0.0-8ubuntu3 [41.5kB]
Get:112 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-kjbuckets 1:1.0.0-8ubuntu3 [1116B]
Get:113 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-gadfly 1.0.0-8ubuntu3 [175kB]
Get:114 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-gadfly 1.0.0-8ubuntu3 [4564B]
Get:115 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-twisted-bin 1.3.0-8ubuntu3 [16.5kB]
Get:116 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-twisted 1.3.0-8ubuntu3 [1067kB]
Get:117 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-eunuchs 20030824.1ubuntu1 [11.0kB]
Get:118 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-eunuchs 20030824.1ubuntu1 [3406B]
Get:119 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-egenix-mxtools 2.0.6-0ubuntu1 [5966B]
Get:120 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-egenix-mxtexttools 2.0.6-0ubuntu1 [64.7kB]
Get:121 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-egenix-mxtexttools 2.0.6-0ubuntu1 [6070B]
Get:122 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-egenix-mxstack 2.0.6-0ubuntu1 [19.6kB]
Get:123 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-egenix-mxstack 2.0.6-0ubuntu1 [5848B]
Get:124 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-egenix-mxproxy 2.0.6-0ubuntu1 [29.6kB]
Get:125 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-egenix-mxproxy 2.0.6-0ubuntu1 [6056B]
Get:126 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-clientcookie 0.4.19-1ubuntu3 [74.7kB]
Get:127 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-clientcookie 0.4.19-1ubuntu3 [16.3kB]
Get:128 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main bicyclerepair 0.9-3ubuntu1 [110kB]
Get:129 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main apt-utils 0.6.35ubuntu2 [183kB]
Get:130 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-apt 0.5.36ubuntu3 [44.9kB]
Get:131 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main apt 0.6.35ubuntu2 [616kB]
Get:132 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libgcrypt11 1.2.0-11 [177kB]
Get:133 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libopencdk8 0.5.5-10 [76.0kB]
Get:134 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libxss1 6.8.2-10 [177kB]
Get:135 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main anacron 2.3-10ubuntu1 [30.3kB]
Get:136 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main cupsys-driver-gimpprint-data 4.2.7-4ubuntu4 [1387kB]
Get:137 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main cupsys-driver-gimpprint 4.2.7-4ubuntu4 [952kB]
Get:138 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libhal-storage0 0.4.7-1ubuntu15 [92.2kB]
Get:139 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libwnck16 2.10.0-0ubuntu1 [95.3kB]
Get:140 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-dbus 0.23.4-0ubuntu3 [142kB]
Fetched 35.6MB in 3m40s (161kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-numeric/python2.4-numeric_23.7-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-numeric/python2.4-numeric_23.7-2ubuntu1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-ldap/python-ldap_2.0.4-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-ldap/python-ldap_2.0.4-1ubuntu2_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyopenssl/python-pyopenssl_0.6-1ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyopenssl/python-pyopenssl_0.6-1ubuntu3_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jabber.py/python2.4-jabber_0.5.0-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jabber.py/python2.4-jabber_0.5.0-1ubuntu2_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gadfly/python2.4-gadfly_1.0.0-8ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gadfly/python2.4-gadfly_1.0.0-8ubuntu3_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.23.4-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.23.4-0ubuntu3_i386.deb)  MD5Sum mismatchE: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
josh@josh:~ $ sudo apt-get -f install --fix-missing?
E: Command line option --fix-missing? is not understood
josh@josh:~ $ sudo apt-get -f install --fix-missing
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  anacron apt apt-utils aptitude bicyclerepair cupsys-driver-gimpprint cupsys-driver-gimpprint-data gaim gaim-data gimp
  gimp-data gimp-python libgcrypt11 libgimp2.0 libglade2-0 libgnutls11 libgtk2.0-0 libgtk2.0-bin libhal-storage0
  libopencdk8 libparted1.6-12 libvte-common libvte4 libwnck16 libxinerama1 libxosd2 libxss1 pymacs python python-adns
  python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack
  python-egenix-mxtexttools python-egenix-mxtools python-eunuchs python-examples python-gadfly python-gd python-gdbm
  python-gdchart python-genetic python-geoip python-glade2 python-gnupginterface python-gtk2 python-hip python-htmlgen
  python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap
  python-minimal python-musicbrainz python-mysqldb python-netcdf python-numarray python-numeric python-osd python-pam
  python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg
  python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy
  python-sqlite python-stats python-syck python-tk python-unit python-xdg python-xml python-xmpp python2.4 python2.4-adns
  python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-eunuchs python2.4-examples
  python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-glade2 python2.4-gtk2 python2.4-htmlgen
  python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets
  python2.4-ldap python2.4-minimal python2.4-musicbrainz python2.4-mysqldb python2.4-numarray python2.4-numeric
  python2.4-osd python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pylibacl python2.4-pymacs python2.4-pyopenssl
  python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-simpletal python2.4-sqlite python2.4-syck python2.4-tk
  python2.4-twisted python2.4-twisted-bin python2.4-unit python2.4-xml python2.4-xmpp synaptic
Suggested packages:
  apt-doc vim-python idle gimpprint-doc gimpprint-locales libzephyr3 gimp-help-en gimp-help libgimp-perl gimp-data-extras
  gnutls-bin libparted1.6-dev libparted1.6-i18n xfonts-base-transcoded python-doc python-profiler python-imaging-doc
  python-egenix-mxdatetime python-numarray-doc python-numeric-tutorial python-reportlab-doc python2.4-doc python-ldap-doc
  mysql-server pyopenssl-doc tix8.1 python2.4-qt3 libwxgtk2.4-python twisted-doc python2.4-twisted-conch python2.4-profiler
  apt-watch
Recommended packages:
  aptitude-doc-en aptitude-doc gimp-svg deborphan libgnome2-perl
The following packages will be REMOVED:
  bug-buddy capplets contact-lookup-applet eog evolution evolution-data-server evolution-exchange evolution-webcal
  file-roller gcalctool gconf-editor gdm gedit gedit-common gnome-about gnome-applets gnome-applets-data
  gnome-control-center gnome-cpufreq-applet gnome-cups-manager gnome-games gnome-gv gnome-media gnome-netstatus-applet
  gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils gnome-volume-manager gnomemeeting gthumb gtkhtml3.2
  gucharmap hal-device-manager libbonoboui2-0 libeel2-2 libgal2.2-1 libgal2.2-common libgnome-desktop-2 libgnome2-0
  libgnomecupsui1.0-1 libgnomeui-0 libgtkhtml3.2-11 libgucharmap4 libnautilus2-2 libpanel-applet2-0 nautilus
  nautilus-cd-burner python-fixedpoint python-gnome2 python-mpz python-newt python2.3-gnome2 rhythmbox sound-juicer
  totem-gstreamer trashapplet tsclient ubuntu-desktop vino yelp
The following NEW packages will be installed:
  anacron cupsys-driver-gimpprint cupsys-driver-gimpprint-data gaim-data libgcrypt11 libgnutls11 libhal-storage0
  libparted1.6-12 libwnck16 libxinerama1 libxss1 python-minimal python2.4 python2.4-adns python2.4-clientcookie
  python2.4-crypto python2.4-dbus python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd
  python2.4-gdbm python2.4-geoip python2.4-glade2 python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-minimal
  python2.4-musicbrainz python2.4-mysqldb python2.4-numarray python2.4-numeric python2.4-osd python2.4-pam
  python2.4-pexpect python2.4-pgsql python2.4-pylibacl python2.4-pymacs python2.4-pyopenssl python2.4-pyorbit
  python2.4-pyxattr python2.4-reportlab python2.4-simpletal python2.4-sqlite python2.4-syck python2.4-tk python2.4-twisted
  python2.4-twisted-bin python2.4-unit python2.4-xml python2.4-xmpp
The following packages will be upgraded:
  apt apt-utils aptitude bicyclerepair gaim gimp gimp-data gimp-python libgimp2.0 libglade2-0 libgtk2.0-0 libgtk2.0-bin
  libopencdk8 libvte-common libvte4 libxosd2 pymacs python python-adns python-apt python-cddb python-clientcookie
  python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-eunuchs
  python-examples python-gadfly python-gd python-gdbm python-gdchart python-genetic python-geoip python-glade2
  python-gnupginterface python-gtk2 python-hip python-htmlgen python-htmltmpl python-id3lib python-imaging
  python-imaging-sane python-jabber python-kjbuckets python-ldap python-musicbrainz python-mysqldb python-netcdf
  python-numarray python-numeric python-osd python-pam python-parted python-pexpect python-pgsql python-pisock
  python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-tk python-unit python-xdg
  python-xml python-xmpp synaptic
78 upgraded, 62 newly installed, 68 to remove and 102 not upgraded.
1 not fully installed or removed.
Need to get 527kB/35.6MB of archives.
After unpacking 161MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-numeric 23.7-2ubuntu1 [99.2kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-ldap 2.0.4-1ubuntu2 [11.2kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python-pyopenssl 0.6-1ubuntu3 [7048B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-jabber 0.5.0-1ubuntu2 [92.5kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-gadfly 1.0.0-8ubuntu3 [175kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main python2.4-dbus 0.23.4-0ubuntu3 [142kB]
Fetched 527kB in 4s (110kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-numeric/python2.4-numeric_23.7-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-numeric/python2.4-numeric_23.7-2ubuntu1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-ldap/python-ldap_2.0.4-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-ldap/python-ldap_2.0.4-1ubuntu2_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyopenssl/python-pyopenssl_0.6-1ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyopenssl/python-pyopenssl_0.6-1ubuntu3_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jabber.py/python2.4-jabber_0.5.0-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jabber.py/python2.4-jabber_0.5.0-1ubuntu2_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gadfly/python2.4-gadfly_1.0.0-8ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gadfly/python2.4-gadfly_1.0.0-8ubuntu3_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.23.4-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.23.4-0ubuntu3_i386.deb)  MD5Sum mismatchUnable to correct missing packages.
E: Aborting Install.
josh@josh:~ $

---

### Post by Xian on 2005-06-10
This is a problem:

```
The following packages will be REMOVED:
bug-buddy capplets contact-lookup-applet eog evolution evolution-data-server
evolution-exchange evolution-webcal file-roller gcalctool gconf-editor gdm
gedit gedit-common gnome-about gnome-applets gnome-applets-data
gnome-control-center gnome-cpufreq-applet gnome-cups-manager gnome-games
gnome-gv gnome-media gnome-netstatus-applet gnome-nettool gnome-panel
gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils
gnome-volume-manager gnomemeeting gthumb gtkhtml3.2 gucharmap
hal-device-manager libbonoboui2-0 libeel2-2 libgal2.2-1 libgal2.2-common
libgnome-desktop-2 libgnome2-0 libgnomecupsui1.0-1 libgnomeui-0
libgtkhtml3.2-11 libgucharmap4 libnautilus2-2 libpanel-applet2-0 nautilus
nautilus-cd-burner python-fixedpoint python-gnome2 python-mpz python-newt
python2.3-gnome2 rhythmbox sound-juicer totem-gstreamer trashapplet tsclient
ubuntu-desktop vino yelp
```

In short, apt is attempting to fix your dependency issues, but in the process it is telling you that it will be removing Gnome -- not a good thing. My best guess is that you have installed an unofficial Ubuntu package that is causing the system deps to cross over themselves. Open Synaptic and click on Status > Installed (Local or Obsolete). Do you have entries in that window that look possibly suspicious?

---

### Post by diomedesxx on 2005-06-10
upon opening the Synaptic Package Manager, I recieved this message: "You have 1 broken package on your system! Use the "Broken" filter to locate it."

I tried the broken filter, and it showed all of my packages.

---

### Post by Xian on 2005-06-10
Try going to Edit > Fix Broken Packages

[img]http://img.photobucket.com/albums/v469/camplear/forums/1545.png[/img]

---

### Post by diomedesxx on 2005-06-10
I fixed the broken packages, but the program required me to apply before I can exit with the changes saved. When I try to apply, I get the following error

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-numeric/python2.4-numeric_23.7-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-numeric/python2.4-numeric_23.7-2ubuntu1_i386.deb)
  MD5Sum mismatch

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-ldap/python-ldap_2.0.4-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-ldap/python-ldap_2.0.4-1ubuntu2_all.deb)
  MD5Sum mismatch

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyopenssl/python-pyopenssl_0.6-1ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyopenssl/python-pyopenssl_0.6-1ubuntu3_all.deb)
  MD5Sum mismatch

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jabber.py/python2.4-jabber_0.5.0-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jabber.py/python2.4-jabber_0.5.0-1ubuntu2_all.deb)
  MD5Sum mismatch

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gadfly/python2.4-gadfly_1.0.0-8ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gadfly/python2.4-gadfly_1.0.0-8ubuntu3_all.deb)
  MD5Sum mismatch

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.23.4-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.23.4-0ubuntu3_i386.deb)
  MD5Sum mismatch

And the progrm will not fix the broken packages w/o these being done.

---

### Post by Xian on 2005-06-10
That is a file error on the server. I'm not getting those problems, so instead of those us.archive.ubuntu repos try substituting the ones listed below in their place in your /etc/apt/sources.list file:

```
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
```

---

### Post by rcmn on 2005-06-10
it is bad i just use the repository that you just gave and it work fine.I'm afraid the us servers are in bad shape...Because it was gaving me error on almost every package i tried to install.

---

### Post by Xian on 2005-06-10
[QUOTE=rcmn]it is bad i just use the repository that you just gave and it work fine.[/QUOTE]
Yeah, I switched earlier today over another issue. Sync problems I suppose.

---

### Post by diomedesxx on 2005-06-10
...Xian, sorry to say man it just made it wrost. Well my roommates uses the us servers, and his is working fine. So I dunno. Please keep trying to help me. Thanks

```
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-panel: Depends: libecal1.2-2 (>= 1.2.1) but it is not going to be installed
               Depends: libedataserver1.2-4 (>= 1.2.1) but it is not going to be installed
               Depends: libgconf2-4 (>= 2.9) but 2.8.1-0ubuntu1 is to be installed
               Depends: libgcrypt11 but it is not going to be installed
               Depends: libglade2-0 (>= 1:2.5.1) but 1:2.4.0-1 is to be installed
               Depends: libgnome-desktop-2 (>= 2.9.91) but 2.8.1-0ubuntu1 is to be installed
               Depends: libgnome-menu0 but it is not going to be installed
               Depends: libgnomevfs2-0 (>= 2.9.90) but 2.8.2-0ubuntu1 is to be installed
               Depends: libgnutls11 (>= 1.0.16) but it is not going to be installed
               Depends: libgtk2.0-0 (>= 2.6.0) but 2.4.10-1ubuntu1.1 is to be installed
               Depends: libpanel-applet2-0 (>= 2.10.1) but 2.8.1-0ubuntu2 is to be installed
               Depends: libwnck16 (>= 2.9.92.1) but it is not going to be installed
               Depends: gnome-panel-data (= 2.10.1-0ubuntu1) but 2.8.1-0ubuntu2 is to be installed
               Depends: gnome-menus (>= 2.9.4) but it is not going to be installed
  gnome-panel-data: Depends: gnome-panel (= 2.8.1-0ubuntu2) but 2.10.1-0ubuntu1 is to be installed
  smeg: Depends: python (>= 2.4) but 2.3.4-1ubuntu1 is to be installed
        Depends: python2.4-gtk2 (>= 2.5.4) but it is not going to be installed
        Depends: python-xdg (>= 0.9) but 0.5-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by diomedesxx on 2005-06-10
This is my complete /etc/apt/sources.list file.

```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu warty main restricted
deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted


## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://us.archive.ubuntu.com/ubuntu hoary universe
## deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by Xian on 2005-06-10
Okay, you are using Warty? That makes a big difference.
You've got Hoary repos in your sources.list -- those gotta go.

Use this file for your sources.list:

```
#deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ warty main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu warty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted universe

## Backports
deb http://ubuntu-backports.mirrormax.net/ warty-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ warty-extras main universe multiverse restricted
```

---

### Post by diomedesxx on 2005-06-11
Err...well. Bad news. It seems to have gotten even worse. I copied the text you provided and pasted t over the old, saved. and tried again.

```
josh@josh:~ $ sudo apt-get update
Err http://ubuntu-backports.mirrormax.net warty-backports/main Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:1 http://ubuntu-backports.mirrormax.net warty-backports/main Release [93B]
Err http://ubuntu-backports.mirrormax.net warty-backports/universe Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:2 http://ubuntu-backports.mirrormax.net warty-backports/universe Release [97B]
Err http://ubuntu-backports.mirrormax.net warty-backports/multiverse Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:3 http://ubuntu-backports.mirrormax.net warty-backports/multiverse Release [99B]
Err http://ubuntu-backports.mirrormax.net warty-backports/restricted Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:4 http://ubuntu-backports.mirrormax.net warty-backports/restricted Release [99B]
Err http://ubuntu-backports.mirrormax.net warty-extras/main Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:5 http://ubuntu-backports.mirrormax.net warty-extras/main Release [90B]
Err http://ubuntu-backports.mirrormax.net warty-extras/universe Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:6 http://ubuntu-backports.mirrormax.net warty-extras/universe Release [94B]
Err http://ubuntu-backports.mirrormax.net warty-extras/multiverse Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:7 http://ubuntu-backports.mirrormax.net warty-extras/multiverse Release [96B]
Err http://ubuntu-backports.mirrormax.net warty-extras/restricted Packages
  404 Not Found [IP: 72.36.166.18 80]
Get:8 http://ubuntu-backports.mirrormax.net warty-extras/restricted Release [96B]
Hit http://archive.ubuntu.com warty/main Sources
Hit http://archive.ubuntu.com warty/main Release
Get:9 http://security.ubuntu.com warty-security/main Packages [89.4kB]
Hit http://archive.ubuntu.com warty/restricted Sources
Hit http://archive.ubuntu.com warty/restricted Release
Get:10 http://archive.ubuntu.com warty/universe Sources [1053kB]
Get:11 http://security.ubuntu.com warty-security/main Release [102B]
Get:12 http://security.ubuntu.com warty-security/restricted Packages [3135B]
Get:13 http://security.ubuntu.com warty-security/restricted Release [108B]
Get:14 http://security.ubuntu.com warty-security/universe Packages [70.1kB]
Get:15 http://security.ubuntu.com warty-security/universe Release [106B]
Get:16 http://security.ubuntu.com warty-security/main Sources [19.7kB]
Get:17 http://security.ubuntu.com warty-security/main Release [104B]
Get:18 http://security.ubuntu.com warty-security/restricted Sources [558B]
Get:19 http://security.ubuntu.com warty-security/restricted Release [110B]
Get:20 http://security.ubuntu.com warty-security/universe Sources [12.7kB]
Get:21 http://security.ubuntu.com warty-security/universe Release [108B]
Get:22 http://archive.ubuntu.com warty/universe Release [99B]
Get:23 http://archive.ubuntu.com warty/multiverse Sources [60.9kB]
Get:24 http://archive.ubuntu.com warty/multiverse Release [101B]
Hit http://archive.ubuntu.com warty/main Packages
Hit http://archive.ubuntu.com warty/main Release
Hit http://archive.ubuntu.com warty/restricted Packages
Hit http://archive.ubuntu.com warty/restricted Release
Get:25 http://archive.ubuntu.com warty/universe Packages [2580kB]
Get:26 http://archive.ubuntu.com warty/universe Release [97B]
Get:27 http://archive.ubuntu.com warty/multiverse Packages [69.7kB]
Get:28 http://archive.ubuntu.com warty/multiverse Release [99B]
Fetched 3960kB in 24s (159kB/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-extras/main/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-extras/universe/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-extras/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/warty-extras/restricted/binary-i386/Packages.gz  404 Not Found [IP: 72.36.166.18 80]
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
josh@josh:~ $ sudo apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
  smeg: Depends: python (>= 2.4) but 2.3.4-1ubuntu1 is installed
        Depends: python2.4-gtk2 (>= 2.5.4) but it is not installable
        Depends: python-xdg (>= 0.9) but 0.5-1 is installed
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net warty-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_warty-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
```

Do you think it might be a better option to reformat the HD, and just install again?

---

### Post by Xian on 2005-06-11
Just comment out those backport repos (I'm not using Warty so I can't verify the correct paths), and then do your 'sudo apt-get update' & 'sudo apt-get -f install'.

---

### Post by diomedesxx on 2005-06-11
Thank you for the advice; the distro seems to be fine now. Programs are installing properly and  no error messages as before. 

Again, thanks,
Diomedes

---

