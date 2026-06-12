---
title: "kdm gdm"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-06-23
whats the difference between gdm and kdm? i'm installing kde and i'm unsure about this... tried searching for a thread about installing kubuntu desktop

---

### Post by wormser on 2007-06-23
Usually programs that start with a g like gdm are for the gnome environment and k for the KDE environment.

To learn more about a package you can use apt-cache show package.

> ~$ apt-cache show gdm
Package: gdm
Priority: optional
Section: gnome
Installed-Size: 13480
Maintainer: Sebastien Bacher <seb128@ubuntu.com>
Architecture: i386
Version: 2.18.1-0ubuntu1
Provides: x-display-manager
Depends: adduser, debconf (>= 0.5), dpkg (>= 1.9), libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libattr1 (>= 2.4.4-1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.2), libdmx1, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnomecanvas2-0 (>= 2.11.1), libgtk2.0-0 (>= 2.10.3), libpam0g (>= 0.76), libpango1.0-0 (>= 1.16.2), libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.10), librsvg2-2 (>= 2.14.4), libselinux1 (>= 1.32), libwrap0, libx11-6, libxau6, libxcursor1 (>> 1.1.2), libxdmcp6, libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0), libxrender1, zlib1g (>= 1:1.2.1), libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-22ubuntu3), libpam-modules (>= 0.79-3ubuntu3), gnome-session | xterm | x-window-manager | x-terminal-emulator, xrdb, gksu (>= 1.0.7), alsa-utils, lsb-base (>= 1.3-9ubuntu3), librsvg2-common, kbd | console-tools
Recommends: whiptail | dialog, zenity, ubuntu-artwork | edubuntu-artwork | xubuntu-default-settings, ubuntu-sounds
Suggests: locales, apmd, msttcorefonts
Conflicts: gdm2
Breaks: gnome-session (<= 2.17.91-0ubuntu1), gnome-screensaver (<= 2.17.7-0ubuntu2), fast-user-switch-applet (<= 2.17.3-0ubuntu1), powermanagement-interface (<= 0.3.11)
Filename: pool/main/g/gdm/gdm_2.18.1-0ubuntu1_i386.deb
Size: 1814224
MD5sum: 43815c4da168d64ba9d7241c9b02bb6f
SHA1: b2c776a194bbd1290a089ab489467dc471c34afc
SHA256: c892f61524c2fa4eb7a995d1ecf09474c5f6cc76c762f73ecc7ac32e8ae7c21d
Description: GNOME Display Manager
 gdm provides the equivalent of a "login:" prompt for X displays- it
 pops up a login window and starts an X session.
 .
 It provides all the functionality of xdm, including XDMCP support for
 managing remote displays.
 .
 The greeting window is written using the GNOME libraries and hence
 looks like a GNOME application- even to the extent of supporting
 themes! By default, the greeter is run as an unprivileged user for
 security.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop, xubuntu-desktop

~$ apt-cache show kdm
Package: kdm
Priority: optional
Section: kde
Installed-Size: 1532
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdebase
Version: 4:3.5.6-0ubuntu20.1
Provides: x-display-manager
Depends: kdelibs4c2a (>= 4:3.5.5-1), libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.2), libpam0g (>= 0.76), libqt3-mt (>= 3:3.3.8really3.3.7), libstdc++6 (>= 4.1.2), libx11-6, libxau6, libxdmcp6, libxtst6, kdebase-bin (= 4:3.5.6-0ubuntu20.1), kdebase-data (>> 4:3.5.6), kdebase-data (<< 4:3.5.7), debconf (>= 1.2.9) | debconf-2.0, libpam-runtime (>= 0.76-14), xbase-clients
Recommends: logrotate
Suggests: khelpcenter, ksmserver (= 4:3.5.6-0ubuntu20.1), kdepasswd (= 4:3.5.6-0ubuntu20.1), menu
Filename: pool/main/k/kdebase/kdm_3.5.6-0ubuntu20.1_i386.deb
Size: 651462
MD5sum: 0a8fdc14e4fd6da16ebc0b9e1e816f9b
SHA1: c90f41355e91d49f2318b46175f3bc3b2f3df433
SHA256: 9518d20d67c483251d0d9ea317894c12afc04566197ac5846ae03f60fb07a374
Description: X display manager for KDE
 kdm manages a collection of X servers, which may be on the local host or
 remote machines. It provides services similar to those provided by init,
 getty, and login on character-based terminals: prompting for login name and
 password, authenticating the user, and running a session. kdm supports XDMCP
 (X Display Manager Control Protocol) and can also be used to run a chooser
 process which presents the user with a menu of possible hosts that offer
 XDMCP display management.
 .
 A collection of icons to associate with individual users is included with
 KDE, but as part of the kdepasswd package.
 .
 The menu package will help to provide KDM with a list of window managers
 that can be launched, if the window manager does not register with KDM
 already. Most users won't need this.
 .
 This package is part of KDE, and a component of the KDE base module.
 See the 'kde' and 'kdebase' packages for more information.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: kubuntu-desktop

Package: kdm
Priority: optional
Section: kde
Installed-Size: 1532
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdebase
Version: 4:3.5.6-0ubuntu20
Provides: x-display-manager
Depends: kdelibs4c2a (>= 4:3.5.5-1), libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.2), libpam0g (>= 0.76), libqt3-mt (>= 3:3.3.8really3.3.7), libstdc++6 (>= 4.1.2), libx11-6, libxau6, libxdmcp6, libxtst6, kdebase-bin (= 4:3.5.6-0ubuntu20), kdebase-data (>> 4:3.5.6), kdebase-data (<< 4:3.5.7), debconf (>= 1.2.9) | debconf-2.0, libpam-runtime (>= 0.76-14), xbase-clients
Recommends: logrotate
Suggests: khelpcenter, ksmserver (= 4:3.5.6-0ubuntu20), kdepasswd (= 4:3.5.6-0ubuntu20), menu
Filename: pool/main/k/kdebase/kdm_3.5.6-0ubuntu20_i386.deb
Size: 651278
MD5sum: de4867300e0b9b968751543b3b9a4640
SHA1: 80f531b06139b173955edb6d33ca9614b5bff0c8
SHA256: 816602d3df57b6983214af66f0090361865ddb7bec2aa653fc0bd0c3462fffda
Description: X display manager for KDE
 kdm manages a collection of X servers, which may be on the local host or
 remote machines. It provides services similar to those provided by init,
 getty, and login on character-based terminals: prompting for login name and
 password, authenticating the user, and running a session. kdm supports XDMCP
 (X Display Manager Control Protocol) and can also be used to run a chooser
 process which presents the user with a menu of possible hosts that offer
 XDMCP display management.
 .
 A collection of icons to associate with individual users is included with
 KDE, but as part of the kdepasswd package.
 .
 The menu package will help to provide KDM with a list of window managers
 that can be launched, if the window manager does not register with KDM
 already. Most users won't need this.
 .
 This package is part of KDE, and a component of the KDE base module.
 See the 'kde' and 'kdebase' packages for more information.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: kubuntu-desktop


---

### Post by manuleka on 2007-06-23
so if i choose gdm does that mean i'm getting the default gnome that i'm running at the moment before installing k desktop?  i'm confused, i thought gnome and k are totally different desktops...

---

### Post by wormser on 2007-06-23
> **manuleka said:**
> so if i choose gdm does that mean i'm getting the default gnome that i'm running at the moment before installing k desktop?  i'm confused, i thought gnome and k are totally different desktops...

Gnome and KDE are 2 different desktops.  GDM is designed for Gnome.  

A guide to installing [KDE]("https://help.ubuntu.com/community/InstallingKDE").

---

### Post by manuleka on 2007-06-23
ok

so for display management, would you recommend kdm or gdm?

whats the difference if i install kdm or gdm?

---

### Post by Songwind on 2007-06-23
> **manuleka said:**
> ok

so for display management, would you recommend kdm or gdm?

whats the difference if i install kdm or gdm?

Functionally they are not that different.  If you are going to use KDE I suggest using KDM just because the tools for configuring KDM are more integrated with KDE than those for GDM.

---

### Post by scxtt on 2007-06-23
you could just use xdm and not worry about it :p

just another option, since i'm not using KDE or GNOME, but i wanted a login manager ... not aware of one for XFCE ...

---

