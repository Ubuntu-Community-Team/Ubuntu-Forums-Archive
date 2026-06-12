---
title: "sudo apt-get install -f"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-12-26
I got the error in the screenshot below and it tells me to run sudo apt-get install -f in a window.


I run it and the following comes up:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpopt-dev libgnutlsxx13 libtasn1-3-dev libatk1.0-dev libaudiofile-dev
  libgpg-error-dev x11proto-xinerama-dev libpango1.0-dev libopencdk8-dev
  libhal-storage-dev libgcrypt11-dev libxi-dev libavahi-client-dev
  x11proto-composite-dev libxcursor-dev libbonobo2-dev python-compizconfig
  libgnutls-dev x11proto-randr-dev x11proto-damage-dev libdbus-1-dev
  libxdamage-dev libxml2-dev libart-2.0-dev libesd0-dev x11proto-fixes-dev
  libcroco3-dev libgnomevfs2-dev libxcomposite-dev libhal-dev libgsf-1-dev
  liblzo2-dev libxrandr-dev libgconf2-dev libselinux1-dev libxft-dev
  libxfixes-dev libgnome2-dev libavahi-glib-dev libavahi-common-dev
  libxinerama-dev libsepol1-dev libbz2-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte apport-gtk apturl at-spi bluez-gnome brltty-x11 bug-buddy compiz
  compiz-gnome compiz-plugins compizconfig-settings-manager
  contact-lookup-applet deskbar-applet displayconfig-gtk ekiga emerald eog
  evince evolution evolution-exchange evolution-plugins evolution-webcal
  f-spot fast-user-switch-applet file-roller firefox firefox-gnome-support
  flashplugin-nonfree gcalctool gconf-editor gdebi gdm gedit gimp gimp-print
  gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install
  gnome-applets gnome-btdownload gnome-control-center gnome-games
  gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media
  gnome-menus gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca
  gnome-panel gnome-panel-dbg gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-screensaver gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes
  gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-plugins-good
  gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14
  gucharmap hal-cups-utils hal-device-manager human-theme hwdb-client-gnome
  language-selector language-support-en libatspi1.0-0 libbonoboui2-0
  libbonoboui2-dev libdeskbar-tracker libedataserverui1.2-8 libeel2-2
  libemeraldengine-dev libemeraldengine0 libexchange-storage1.2-3
  libgail-common libgail-dev libgail-gnome-module libgail18 libgconf2.0-cil
  libgdl-1-0 libgdl-gnome-1-0 libgimp2.0 libgksu2-0 libgksuui1.0-1 libglade2-0
  libglade2-dev libglade2.0-cil libgnome-desktop-2 libgnome-keyring-dev
  libgnome-keyring0 libgnome-window-settings1 libgnome2-canvas-perl
  libgnome2-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-dev
  libgnomekbd1 libgnomekbdui1 libgnomeprintui2.2-0 libgnomeui-0 libgnomeui-dev
  libgpod2 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-dev
  libgtkhtml2-0 libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15
  libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtksourceview2.0-0 libgtkspell0
  libgucharmap6 libgutenprintui2-1 liblaunchpad-integration0 liblpint-bonobo0
  libmetacity0 libnautilus-burn4 libnautilus-extension1 libnotify1
  libpanel-applet2-0 libpanel-applet2-dev libpoppler-glib2 librsvg2-2
  librsvg2-common librsvg2-dev librsvg2.0-cil libsexy2 libtotem-plparser7
  libtracker-gtk0 libvte9 libwmf0.2-7 libwnck22 macmenu-applet metacity
  mozilla-firefox-locale-en-gb nautilus nautilus-cd-burner nautilus-sendto
  network-manager-gnome notification-daemon onboard openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human
  openoffice.org-thesaurus-en-us openoffice.org-writer pidgin python-at-spi
  python-glade2 python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-gnomecanvas python-gtk2 python-gtkhtml2 python-launchpad-integration
  python-notify python-pygtksourceview python-sexy python-uno python-virtkey
  python-vte restricted-manager rhythmbox scim scim-gtk2-immodule
  scim-modules-table scim-tables-additional screensaver-default-images
  serpentine software-properties-gtk sound-juicer ssh-askpass-gnome synaptic
  system-config-printer tangerine-icon-theme thunderbird-locale-en-gb tomboy
  totem totem-gstreamer totem-mozilla tracker tracker-search-tool tsclient
  ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs update-manager
  update-notifier vino xdg-user-dirs-gtk xsane xscreensaver-data
  xscreensaver-gl yelp zenity
0 upgraded, 0 newly installed, 231 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 784MB disk space will be freed.
Do you want to continue [Y/n]? 

```


It looks like it wants to remove a lot of stuff that I use.  Do I still use it?

---

### Post by wormser on 2007-12-26
What did you do to get the error because the results of sudo apt-get install -f look extreme to me.

---

### Post by Hork on 2007-12-26
> **wormser said:**
> What did you do to get the error because the results of sudo apt-get install -f look extreme to me.

I downloaded the tarball from [https://wiki.ubuntu.com/global_menu#deb](https://wiki.ubuntu.com/global_menu#deb) ( [http://rapidshare.com/files/70248395/GutsyOSX.tar.bz2.html](http://rapidshare.com/files/70248395/GutsyOSX.tar.bz2.html) ) and ran was installing every deb like it said and when I installed 'libgtk2.0-common_2.12.0-1ubuntu3.1_all.deb' it gave me that error.

---

### Post by wormser on 2007-12-26
Get another confirmation before moving on.  I would also search for more help with global menu.  It now makes sense why all those gnome packages are being removed.  You are installing a new desktop look.  I think it is ok but as I stated, get another confirmation.

---

### Post by Hork on 2007-12-26
*NOTE: At no time during this should there be Error messages. If there are try not to restart your system until any errors are resolved. Look for further help posting your Error message here:*

Dang, I guess I'll repost the error in that thread. :|

Thanks though

---

