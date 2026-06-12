---
title: "hot to remove gnome"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by bags on 2006-06-07
hy!
I installed the base system with gnome but I prefer kde.. how can I remove gnome from my distro?

thanks
matteo

---

### Post by johnc4510 on 2006-06-07
Click on this link and follow the advice of aysiu at the bottom of the page:
[http://www.ubuntuforums.org/showthread.php?t=191181&highlight=change+gnome+kde](http://www.ubuntuforums.org/showthread.php?t=191181&highlight=change+gnome+kde)

---

### Post by richbarna on 2006-06-07
I did this and wiped out half of my operating system.
You can either :-
> sudo apt-get remove ubuntu-desktop
Then :-
> sudo aptitude update
> sudo aptitude install kubuntu-desktop

or just install Kubuntu desktop and have the best of both worlds. You will be able to choose either session at bootup/login :)

NOTE * To install desktop environments ALWAYS use aptitude instead of apt-get. If later you want to remove it, there are far less dependency problems.

---

### Post by aysiu on 2006-06-07
[quote=johnc4510]Click on this link and follow the advice of aysiu at the bottom of the page:
[http://www.ubuntuforums.org/showthre...ange+gnome+kde](http://www.ubuntuforums.org/showthre...ange+gnome+kde)[/quote] That's out of date for Dapper. The up-to-date version is here: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

[QUOTE=richbarna]
You can either :-[/quote] That won't do anything except uninstall the pointer to the Gnome files (not the Gnome files themselves).

> 
Then :-

or just install Kubuntu desktop and have the best of both worlds. You will be able to choose either session at bootup/login :)

NOTE * To install desktop environments ALWAYS use aptitude instead of apt-get. If later you want to remove it, there are far less dependency problems. You can't use *aptitude* after the fact. In order to use ```
sudo aptitude remove ubuntu-desktop
``` and have it actually remove Gnome fully, you would have had to have installed Gnome with these *two* commands: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by richbarna on 2006-06-07
Read the post aysiu
He ALREADY has GNOME. apt-get remove.
I said aptitude to INSTALL KDE.

---

### Post by aysiu on 2006-06-07
Oops! You're right. I had assumed that bags had both KDE *and* Gnome installed. Nevertheless, ```
sudo apt-get remove ubuntu-desktop
``` still does virtually nothing.

---

### Post by richbarna on 2006-06-07
[QUOTE=aysiu]Oops! You're right. I had assumed that bags had both KDE *and* Gnome installed. Nevertheless, ```
sudo apt-get remove ubuntu-desktop
``` still does virtually nothing.[/QUOTE]

Try it then ;)
Then you can "virtualy" post back from your kde desktop :)

---

### Post by bags on 2006-06-07
thank you all! I removed gnome successfully :D :D 

cheers from italy :-\" 
matteo

---

### Post by richbarna on 2006-06-07
Hey bags !! Just for the sake of it, Which method did you use ?
I'm thinking of dumping Gnome.

---

### Post by bags on 2006-06-07
I did:

> Remove Ubuntu
Paste this command into the terminal: sudo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity 

---

### Post by richbarna on 2006-06-07
I think i'll wait. I'm pretty sure i might need some of the stuff listed there.

---

### Post by aysiu on 2006-06-07
[QUOTE=richbarna]I think i'll wait. I'm pretty sure i might need some of the stuff listed there.[/QUOTE]
No worries.

Copy that into a text file. Delete from the text file the packages you want to *keep*. Then copy and paste the remaining text into the terminal.

---

### Post by richbarna on 2006-06-07
To be honest aysiu, you know a hell of a lot more than me about dependencies etc, and I have had some strange behaviour deleting stuff that are "supposedly" unconnected.
I wouldn't know where to start, gstreamer for example, or lib files.
My kde desktop had problems with sound, video, printing, and reading dvd's until I installed Gnome desktop (why?, I have completely no idea).

---

### Post by aysiu on 2006-06-07
It's probably best to keep Gnome in there, then, unless you're hard up for hard drive space.

---

