---
title: "How can I make a custom installation (ie Kubuntu, Xubuntu, Mint, etc.)?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Rob00141977 on 2007-01-28
What I am trying to do is have an Ubuntu set up with only a few applications. I know that I can have a text only installation from my 6.10 DVD (no X.org, GUI Desktop, apps). Is it possible to have a set up with just a desktop, Firefox, Synaptic, and a Terminal? I tried starting from text only install and getting X.org, Xterm, Synaptic, GDM, Firefox and Ubuntu-Desktop. Everything worked but the Ubuntu-Desktop installed a host of programs I don't want or need. I have no problem using apt-get over Synaptic if I must, but I don't know what packages are essential. Any suggestions?

---

### Post by MkfIbK7a on 2007-01-28
yes install the server version then do

sudo aptitude install ubuntu-desktop

this installs the desktop

you can then install whatever programs you want

---

### Post by Rob00141977 on 2007-01-28
Thanks for the info.

---

### Post by Pobega on 2007-01-28
> **wert613 said:**
> yes install the server version then do

sudo aptitude install ubuntu-desktop

this installs the desktop

you can then install whatever programs you want

Yeah but the desktop package comes with a lot of unwanted things.> pobega@ackbar:~$ aptitude show ubuntu-desktop 
Package: ubuntu-desktop
State: not installed
Version: 1.30
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 45.1k
Depends: acpi, acpi-support, acpid, alacarte, anacron, apmd, apport-gtk,
         avahi-daemon, bc, bug-buddy, cdparanoia, cdrecord,
         contact-lookup-applet, cupsys, cupsys-bsd, cupsys-client,
         cupsys-driver-gutenprint, dc, deskbar-applet, desktop-file-utils,
         diveintopython, doc-base, dvd+rw-tools, ekiga, eog, esound, evince,
         evolution, evolution-exchange, evolution-plugins, evolution-webcal,
         f-spot, file-roller, firefox, firefox-gnome-support, foo2zjs,
         foomatic-db, foomatic-db-engine, foomatic-db-hpijs, foomatic-filters,
         fortune-mod, gaim, gcalctool, gconf-editor, gdebi, gdm, gedit, gimp,
         gimp-print, gimp-python, gnome-about, gnome-app-install, gnome-applets,
         gnome-btdownload, gnome-control-center, gnome-cups-manager,
         gnome-icon-theme, gnome-keyring-manager, gnome-media, gnome-menus,
         gnome-netstatus-applet, gnome-nettool, gnome-panel,
         gnome-pilot-conduits, gnome-power-manager, gnome-session, gnome-spell,
         gnome-system-monitor, gnome-system-tools, gnome-terminal, gnome-themes,
         gnome-utils, gnome-volume-manager, gnome2-user-guide, gs-esp,
         gstreamer0.10-alsa, gstreamer0.10-esd, gstreamer0.10-plugins-base-apps,
         gthumb, gtk2-engines, gucharmap, hal, hal-device-manager, hotkey-setup,
         hwdb-client-gnome, landscape-client, language-selector, lftp,
         libgl1-mesa-glx, libglut3, libgnome2-perl, libgnomevfs2-bin,
         libgnomevfs2-extra, libpam-foreground, libpt-plugins-v4l,
         libpt-plugins-v4l2, libsasl2-modules, libstdc++5, libxp6, metacity,
         min12xxw, mkisofs, nautilus, nautilus-cd-burner, nautilus-sendto,
         notification-daemon, openoffice.org, openoffice.org-evolution,
         openoffice.org-gnome, pnm2ppa, powermanagement-interface, readahead,
         rhythmbox, rss-glx, screen, screensaver-default-images, scrollkeeper,
         serpentine, slocate, smbclient, sound-juicer, ssh-askpass-gnome,
         synaptic, tangerine-icon-theme, tango-icon-theme,
         tango-icon-theme-common, tomboy, totem, totem-mozilla, tsclient,
         ttf-bitstream-vera, ttf-dejavu, ttf-freefont, ubuntu-artwork,
         ubuntu-docs, ubuntu-sounds, unzip, update-notifier, usplash,
         usplash-theme-ubuntu, vino, wvdial, x-ttcidfont-conf, xkeyboard-config,
         xorg, xsane, xscreensaver-data, xscreensaver-gl, xterm, xvncviewer,
         yelp, zenity, zipTaken from aptitude's description of the ubuntu-desktop metapackage. You may want to just install mozilla firefox and synaptic, although I don't see synaptic being useful if you're going to attempt to use it from a terminal session.

Also, how are you going to use Firefox from a terminal? I assume you *will* be installing a GUI, I suggest Xfce over Gnome personally.

---

### Post by slybob on 2007-01-28
Ive been playing with xubuntu for a while. comes with xfce and is very slim on apps.

really really tasty!

---

### Post by MkfIbK7a on 2007-01-28
yes i was going to suggest that but since he asked for ubuntu i gave him gnome...

sudo aptitude install xubuntu-desktop

is xfce4

you could also just install something like 

fluxbox

icewm

fvwm-crystal

they are all in the repos and have instruction on the wiki on how to set up

just 

apt-get install <name of the window manger>

---

### Post by Rob00141977 on 2007-01-28
Even more options. Thanks for all the help.

---

### Post by MkfIbK7a on 2007-01-28
no prob rob

---

### Post by Pobega on 2007-01-28
Just so you know, if you're looking for something lightweight aptitude search searchs the package names and apt-cache search searches the descriptions and names. So to look for a window manager you'd probably have to use apt-cache search, there are loads of choices available! And this is what makes Linux and Ubuntu so great ;D

---

