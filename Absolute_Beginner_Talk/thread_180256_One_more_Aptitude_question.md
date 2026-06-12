---
title: "One more Aptitude question"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-21
i want to know how this would work:
i have only gnome installed, but a few kde apps are installed on gnome. if i install kubuntu-desktop using aptitude, then remove it using aptitude, would those programs and libraries i had before installing kde still be there?
(that is a wordy sentence! i hope you guys get it :))

---

### Post by aysiu on 2006-05-21
Try it out and see.

You can always reinstall those few programs, too, should they be removed. Uninstalling programs does not remove their configuration files or preferences.

---

### Post by glotz on 2006-05-21
I'm a newbie, so what I say is probably wrong... ;)

But I'd think that at least, if the kubuntu destop package doesn't contain those apps you allready have, you'd be safe.

---

### Post by user1397 on 2006-05-21
[quote=aysiu]Try it out and see.[/quote]
will do :D

---

### Post by 5-HT on 2006-05-21
[quote=erik1397]i want to know how this would work:
i have only gnome installed, but a few kde apps are installed on gnome. if i install kubuntu-desktop using aptitude, then remove it using aptitude, would those programs and libraries i had before installing kde still be there?
(that is a wordy sentence! i hope you guys get it )[/quote] 
It depends on how you initially installed the KDE apps and how you have aptitude configured.

If you installed the apps using aptitude using the default configuration and then install kubuntu-desktop using aptitude and subsequently remove it, those apps you installed prior to installing kubuntu-desktop should still remain.

If you did not originally install the KDE apps with aptitude, depending on how you have aptitude configured, they may be marked as either 'automatically installed' or 'manually installed'. 

They are most likely not marked as 'automatically installed' as without kubuntu-desktop or any other package depending on them, aptitude would be trying to remove them everytime you do anything with aptitude anyway (again, depends on how you have aptitude configured).

If the KDE apps are marked as automatically installed (unlikely given your situation, but it could happen), then they will be removed when you uninstall kubuntu-desktop using aptitude (if nothing else depends on them).

The easiest thing to do would be to check if aptitude has the KDE apps you initially installed marked as 'automatically installed' or 'manually installed'.*


You want them to be set to be 'manually installed' so that they will not be removed when you remove kubuntu-desktop.*


*If you don't know how to do this, I can walk you through it. The aptitude manual describes it in detail though.

Hope that helps.

---

### Post by user1397 on 2006-05-22
thanks for all the replies.
so what happened was i did:
```
sudo aptitude install kubuntu-desktop
```
and right after that:
```
sudo aptitude remove kubuntu-desktop
```
and the KDE applications that i had installed before those commands were still there.  
So, 5-HT, i guess they were manually-installed.

---

### Post by aysiu on 2006-05-22
[QUOTE=erik1397]thanks for all the replies.
so what happened was i did:
```
sudo aptitude install kubuntu-desktop
```
and right after that:
```
sudo aptitude remove kubuntu-desktop
```
and the KDE applications that i had installed before those commands were still there.  
So, 5-HT, i guess they were manually-installed.[/QUOTE] Did you do ```
sudo aptitude update
``` before installing *kubuntu-desktop*? You'll notice that when you update with aptitude, it builds the dependency inter-relations.

---

### Post by user1397 on 2006-05-22
[quote=aysiu]Did you do ```
sudo aptitude update
``` before installing *kubuntu-desktop*? You'll notice that when you update with aptitude, it builds the dependency inter-relations.[/quote]
oops! no i didn't, completely forgot!
well now i know!
by the way, aysiu, which d.e. is your favorite?
which one do you find yourself using more?

---

### Post by aysiu on 2006-05-22
[QUOTE=erik1397]oops! no i didn't, completely forgot!
well now i know![/quote] And knowing's half the battle. > by the way, aysiu, which d.e. is your favorite? I can't decide. Right now I'm using KDE, but I switch between Gnome, KDE, and XFCE. I'm really liking the new XFCE in Xubuntu Dapper, especially the splash screen with the mouse running inside of the Ubuntu logo. > which one do you find yourself using more? Right now, KDE.

---

### Post by user1397 on 2006-05-22
i just asked because i was thinking about getting KDE, but i'm not sure.  one time i installed KDE using apt-get, and when i logged into it, i didn't know where anything was and i was frightened and confused by my surroundings ;)
so i just uninstalled it, but instead of following your "howto" on getting rid of KDE apps and libs, i followed a weird one that didn't work and it uninstalled my ubuntu-desktop! i had to reinstall the ubuntu-desktop and many apps that i had installed before! so i was scared of KDE for a while, but now i think i've built up enough courage to try it again...:p

---

### Post by aysiu on 2006-05-22
[QUOTE=erik1397]i just asked because i was thinking about getting KDE, but i'm not sure.  one time i installed KDE using apt-get, and when i logged into it, i didn't know where anything was and i was frightened and confused by my surroundings ;)
so i just uninstalled it, but instead of following your "howto" on getting rid of KDE apps and libs, i followed a weird one that didn't work and it uninstalled my ubuntu-desktop! i had to reinstall the ubuntu-desktop and many apps that i had installed before! so i was scared of KDE for a while, but now i think i've built up enough courage to try it again...:p[/QUOTE] If you want, you can also use the Kubuntu live CD. Tha'ts an easy non-committal way to try out KDE.

---

### Post by user1397 on 2006-05-22
[quote=aysiu]If you want, you can also use the Kubuntu live CD. Tha'ts an easy non-committal way to try out KDE.[/quote]
i agree, but i do hate the slow-ness of the live cd, and the whole rebooting process (lazy)

---

### Post by encho on 2006-05-22
While we are here, I've always wanted to know the following: is it possible to remove ie. kubuntu-desktop with all its dependencies as well. I found myself using xfce more and more, and wish to remove everything related to kde or gnome. Removing it normal way would just remove the metapackage, but dependencies will stay. Any idea?

Edit:
I basically want to start from scratch, but rather than installing from cd again, I want to remove everything but xubuntu-desktop and its dependencies. Is it possible???

---

### Post by 5-HT on 2006-05-22
[quote=encho]While we are here, I've always wanted to know the following: is it possible to remove ie. kubuntu-desktop with all its dependencies as well. I found myself using xfce more and more, and wish to remove everything related to kde or gnome. Removing it normal way would just remove the metapackage, but dependencies will stay. Any idea?[/quote] 
If you installed the metapackage with aptitude, then removing it with aptitude will remove all the dependencies of the metapackage if no other installed package requires them.

If you did not install the metapackage with aptitude, then you could find all the dependencies of the metapackage with aptitude/synaptic/apt etc... and mark them as 'automatically installed' in aptitude.

The easiest way would be to this would be to (using kubuntu-desktop as an example):
1.
```
 aptitude show kubuntu-desktop 
``` and copy all the listed dependencies to a file.

2. ```
 aptitude markauto <paste the list of dependencies here without> 
``` 


Then you can just remove the metapackage in aptitude, and all used dependencies will go along with it.

Hope that helps

---

### Post by 5-HT on 2006-05-22
[quote=encho]Edit:
I basically want to start from scratch, but rather than installing from cd again, I want to remove everything but xubuntu-desktop and its dependencies. Is it possible???[/quote]

If have some other *ubuntu-desktop metapackages installed, then you could follow my last post to remove the other metapackages but leave xubuntu-desktop.

That should leave you with *almost* the same system as just installing xubuntu-desktop.

---

### Post by catlett on 2006-05-22
Aysiu must be busy but Aysiu already covered it. [http://www.ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kubuntu-desktop](http://www.ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kubuntu-desktop)

---

### Post by encho on 2006-05-22
That was fast! 5-HT, it removed lots of applications, but some still remain (don't know why).
Guess I've installed some packages out of the list that still need them. Is there a way to force it? Like removing everything apart from xubuntu-desktop and ubuntu-minimal packages (and dependencies)?

catlett, that Aysiu's post is very useful, but unfortunately, it is for breezy and I'm using dapper (guess some additional packages are part of the kubuntu-desktop metapackage). And still have some other kde packages that do not belong to the metapackage, but want to remove them as well...

Thanks for the input

---

### Post by aysiu on 2006-05-22
[QUOTE=encho]
I basically want to start from scratch, but rather than installing from cd again, I want to remove everything but xubuntu-desktop and its dependencies. Is it possible???[/QUOTE] This should work for Dapper: > sudo apt-get remove adept akregator alacarte amarok amarok-xine app-install-data app-install-data-commercial ark arts artsbuilder at-spi bicyclerepair bittorrent blt bluez-cups bluez-pcmcia-support bluez-pin bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty bsh bug-buddy ca-certificates capplets-data cdrdao contact-lookup-applet debtags deskbar-applet diveintopython ekiga enscript eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal example-content fastjar festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gdb gedit gedit-common gij-4.1 gimp-python gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-mag gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-crux gtk2-engines-gtk-qt gtk2-engines-highcontrast gtk2-engines-lighthouseblue gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs gwenview hal-device-manager hwdb-client imagemagick java-common java-gcj-compat k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector language-selector-common language-selector-qt libadns1 libakode2 libarts1-akode libarts1c2a libartsc0 libatspi1.0-0 libaudio2 libavahi-qt3-1 libavc1394-0 libbeagle0 libbluetooth1 libbrlapi1 libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcurl3 libcurl3-gnutls libdbus-qt-1-1c2 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libflac++5c2 libflac7 libgadu3 libgail-common libgail-gnome-module libgail17 libgcj-common libgcj7 libgcj7-jar libgd2-noxpm libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgeoip1 libglew1 libglib-perl libgmp3c2 libgnome-desktop-2 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecupsui1.0-1c2a libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgpgme11 libgphoto2-2 libgphoto2-port0 libgpod0 libgsl0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libhsqldb-java libicu34 libid3-3.8.3c2a libidn11 libieee1284-3 libjasper-1.701-1 libjaxp1.2-java libjessie-java libjline-java libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpathsea4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblircclient0 liblockdev1 liblpint-bonobo0 libmagick9 libmdbtools libmetacity0 libmimelib1c2a libmpcdec3 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libneon25 libnetcdf3 libnotify1 libnspr4 libnss-mdns libnss3 liboggflac3 liboil0.3 libopal-2.2.0 libopenexr2c2a libopenobex-1.0-0 libpam-foreground libpanel-applet2-0 libpisock8 libpisync0 libpoppler1-glib libpoppler1-qt libportaudio0 libpq4 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libpythonize0 libqt3-mt libqthreads-12 libraptor1 librasqal0 libraw1394-5 librdf0 librsvg2-2 librsvg2-common librsync1 libruby1.8 libsamplerate0 libsane libsdl1.2debian libsdl1.2debian-alsa libsensors3 libservlet2.3-java libsexy2 libshout3 libskim0 libsmbclient libsndfile1 libsoup2.2-8 libsqlite0 libsqlite3-0 libstlport4.6c2 libtdb1 libtotem-plparser1 libtunepimp2c2a libvorbisenc2 libvorbisfile3 libwnck-common libwnck18 libxalan2-java libxerces2-java libxklavier10 libxml2-utils libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxres1 libxt-java menu-xdg metacity mysql-common nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-java-common openoffice.org-kde openoffice.org-math openoffice.org-writer openssl perl-suid pkg-config poster psutils pykdeextensions python-adns python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kde3 python-kjbuckets python-launchpad-integration python-ldap python-libxml2 python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4-adns python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dev python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kde3 python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-mysqldb python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-qt3 python2.4-reportlab python2.4-simpletal python2.4-sip4-qt3 python2.4-soappy python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml python2.4-xmpp qca-tls qobex rdesktop rdiff-backup rhythmbox rss-glx scim-qtimm serpentine skim sound-juicer speedcrunch ssh-askpass-gnome system-tools-backends tangerine-icon-theme tango-icon-theme-common tcl8.4 tk8.4 totem totem-gstreamer tsclient ttf-gentium ttf-opensymbol ubuntu-artwork ubuntu-docs update-notifier vino vnc-common vorbis-tools whois wlassistant xsane xsane-common xsltproc xvncviewer yelp zenity

---

### Post by catlett on 2006-05-22
[QUOTE=aysiu]This should work for Dapper:[/QUOTE]
That is impressive just in text!!! I don't even know how you know what all those packages are, nevermind which ones go with what metapackage and can be removed.:D  
P.S. Could that be copy and pasted? Do that many  selections run after a command, in this case obviously apt-get.

---

### Post by aysiu on 2006-05-22
[QUOTE=catlett]That is impressive just in text!!! I don't even know how you know what all those packages are, nevermind which ones go with what metapackage and can be removed.:D[/quote] You probably won't be as impressed when I tell you how I got that list.

I popped in a Xubuntu live CD, opened a terminal, and typed in ```
sudo apt-get update && sudo apt-get install ubuntu-desktop kubuntu-desktop
``` Then, I highlighted all of the new packages to be installed and pasted them into a post.

> 
P.S. Could that be copy and pasted? Do that many  selections run after a command, in this case obviously apt-get. And, yes, it can be copied and pasted. Just highlight it all, open a terminal, and press Shift-Insert.

---

### Post by encho on 2006-05-23
[QUOTE=aysiu]You probably won't be as impressed when I tell you how I got that list.[/QUOTE]

Still good idea nevertheless :D Thanks for your effort.

---

### Post by aysiu on 2006-05-23
[QUOTE=encho]Still good idea nevertheless :D Thanks for your effort.[/QUOTE] So, encho, did it work?

I'm not 100% sure it'll work because I was using the Xubuntu Dapper *Beta*, not the most up-to-date version, so the package listings might have changed.

Please let me know if it worked out for you.

---

### Post by encho on 2006-05-23
Almost, it really removed everything, but some still remain that are not directly part of any of the metapackages (like some packages from multiverse, mostly multimedia). But it is close enough, thanks.

---

### Post by catlett on 2006-05-23
I'm still impressed. What is the &&command?

---

### Post by aysiu on 2006-05-23
[QUOTE=catlett]I'm still impressed. What is the &&command?[/QUOTE] The && strings two commands together.

So instead of this: ```
sudo apt-get update
sudo apt-get install *blah*
``` I can do this: ```
sudo apt-get update && sudo apt-get install *blah*
```

---

### Post by user1397 on 2006-05-24
Just proud to say i have GNOME, KDE and XFCE installed on my system.  (not much to be proud of, hehe).  Trying out each one till im sick.  (i really like how in KDE or XFCE you can click only one time to open stuff, i hate that double-click business...

---

### Post by encho on 2006-05-24
[QUOTE=erik1397]Just proud to say i have GNOME, KDE and XFCE installed on my system.  (not much to be proud of, hehe).  Trying out each one till im sick.  (i really like how in KDE or XFCE you can click only one time to open stuff, i hate that double-click business...[/QUOTE]

You can change that in nautilus. Go to preferences, and you'll find single click somewhere.

Only thing I don't like in XFCE is that you have to double-click desktop icons. But I love the ability to display minimized windows instead of 'real' desktop.

---

### Post by user1397 on 2006-05-24
[quote=encho]You can change that in nautilus. Go to preferences, and you'll find single click somewhere.[/quote] Thanks! That worked flawlessly :D

---

