---
title: "Installing libICE, dependency problems"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by maxxum on 2007-08-29
I was trying to install the program recordmydesktop. The configure script stopped at:
```

configure: error: Can't find libICE

```
I downloaded libice-dev from debian.org and tried:
```

atul@ad:~/Desktop$ sudo dpkg -i libice-dev_1.0.4-1_i386.deb
Selecting previously deselected package libice-dev.
(Reading database ... 111630 files and directories currently installed.)
Unpacking libice-dev (from libice-dev_1.0.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of libice-dev:
 libice-dev depends on libice6 (= 2:1.0.4-1); however:
  Version of libice6 on system is 2:1.0.3-1build1.
dpkg: error processing libice-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libice-dev

```
Then I tried:
```

atul@ad:~/Desktop$ sudo dpkg -i libice6_1.0.4-1_i386.deb
(Reading database ... 111644 files and directories currently installed.)
Preparing to replace libice6 2:1.0.3-1build1 (using libice6_1.0.4-1_i386.deb) ...
Unpacking replacement libice6 ...
dpkg: dependency problems prevent configuration of libice6:
 libice6 depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
dpkg: error processing libice6 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libice6

```
Then I tried:
```

atul@ad:~/Desktop$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree
Reading state information... Done
libc6 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libice6: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
If I do apt-get -f install it lists a lot of programs and says:
```
0 upgraded, 0 newly installed, 291 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 897MB disk space will be freed.
Do you want to continue [Y/n]? n

```
That is when I bailed out. I know if I say yes it will remove 897MB worth of installed libraries and could break my installation.
A taste of dependency hell? :)
Kindly help.

---

### Post by maxxum on 2007-08-30
Okay, can someone at least help me fix these broken packages? it lists numerous packages starting from adept to xterm, including openoffice etc that it wants to remove. It seems  this will surely break the system with 897 MB worth of software removed. How do I get rid of the partial installation of recordmydesktop which led to all these problems?

I tried this: ```

~/Desktop$ sudo apt-get remove libice6
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  adept-manager: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  adept-updater: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  amarok: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  amsn: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  appres: Depends: libice6 but it is not going to be installed
  ark: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  beforelight: Depends: libice6 but it is not going to be installed
  bitmap: Depends: libice6 but it is not going to be installed
  digikam: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  editres: Depends: libice6 but it is not going to be installed
  ekiga: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  gparted: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  gs-esp-x: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  gstm: Depends: libice6 but it is not going to be installed
  gstreamer0.10-plugins-base: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  gstreamer0.10-x: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  gtk-qt-engine: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  gwenview: Depends: libice6 but it is not going to be installed
  iceauth: Depends: libice6 but it is not going to be installed
  imlib11: Depends: libice6 but it is not going to be installed
  k3b: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kaddressbook: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kaffeine: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kaffeine-xine: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  karm: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  katapult: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kate: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kcontrol: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kdebase-bin: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kdebluetooth: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kdegraphics-kfile-plugins: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kdelibs4c2a: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kdepim-kio-plugins: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kdepim-kresources: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kdesktop: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  keep: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kexi: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kghostview: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kicker: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kio-apt: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kipi-plugins: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  klipper: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kmail: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kmenuedit: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kmilo: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kmousetool: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kmplayer: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kmplayer-base: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kmplayer-konq-plugins: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  knetworkmanager: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  koffice-libs: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  konq-plugins: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  konqueror: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  konversation: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kopete: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  korganizer: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  krdc: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  krfb: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  ksmserver: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  ksplash: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  ksplash-engine-moodin: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  ksysguard: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  ksystemlog: Depends: libice6 but it is not going to be installed
  ktorrent: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kwin: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  kwin-style-crystal: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libarts1c2a: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libavahi-qt3-1: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libbonoboui2-0: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libgdl-1-0: Depends: libice6 but it is not going to be installed
  libgnome-desktop-2: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libgnomeui-0: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libice-dev: Depends: libice6 (= 2:1.0.4-1) but it is not going to be installed
  libjasper-runtime: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libk3b2: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libkcal2b: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libkdepim1a: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libkleopatra1: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libkpimidentities1: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libksieve0: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libmagick9: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libmetacity0: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libpanel-applet2-0: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libpulse0: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libqt-perl: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libqt3-mt: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libqt4-gui: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libqt4-qt3support: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libsm6: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libsmokeqt1: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libstartup-notification0: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libvte9: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libwnck18: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libxaw7: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libxmu6: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libxt6: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  libxtrap6: Depends: libice6 but it is not going to be installed
  listres: Depends: libice6 but it is not going to be installed
  oclock: Depends: libice6 but it is not going to be installed
  openoffice.org-core: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  python-gnome2: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  python-gnome2-desktop: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  python-gnome2-extras: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  python-vte: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  qobex: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  recordmydesktop: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  scim-qtimm: Depends: libice6 but it is not going to be installed
  smproxy: Depends: libice6 but it is not going to be installed
  viewres: Depends: libice6 but it is not going to be installed
  vlc: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  xbiff: Depends: libice6 but it is not going to be installed
  xcalc: Depends: libice6 but it is not going to be installed
  xclipboard: Depends: libice6 but it is not going to be installed
  xclock: Depends: libice6 but it is not going to be installed
  xconsole: Depends: libice6 but it is not going to be installed
  xditview: Depends: libice6 but it is not going to be installed
  xeyes: Depends: libice6 but it is not going to be installed
  xf86dga: Depends: libice6 but it is not going to be installed
  xfd: Depends: libice6 but it is not going to be installed
  xfontsel: Depends: libice6 but it is not going to be installed
  xgc: Depends: libice6 but it is not going to be installed
  xkbutils: Depends: libice6 but it is not going to be installed
  xload: Depends: libice6 but it is not going to be installed
  xlogo: Depends: libice6 but it is not going to be installed
  xmag: Depends: libice6 but it is not going to be installed
  xman: Depends: libice6 but it is not going to be installed
  xmessage: Depends: libice6 but it is not going to be installed
  xmms: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  xmore: Depends: libice6 but it is not going to be installed
  xpmutils: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  xsm: Depends: libice6 but it is not going to be installed
  xstdcmap: Depends: libice6 but it is not going to be installed
  xterm: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
  xtrap: Depends: libice6 but it is not going to be installed
  xvidtune: Depends: libice6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by maxxum on 2007-09-07
Someone please help! my Ubuntu is gonna be broken! or at least tell me some ideas to back up my installed programs and do a reinstall so I dont have to install everything again. :(

---

### Post by oldos2er on 2007-09-07
I don't really know how to help you, but I sympathize with your problems. You could try installing libc6 2.6.1 manually, using dpkg. Find it here: [http://packages.debian.org/unstable/libs/libc6](http://packages.debian.org/unstable/libs/libc6)

---

### Post by maxxum on 2007-09-09
Thanks. But I don't need to install libc6 anymore, or so it says. All I want now is to fix all these packages it says it wants to remove. I cannot update anymore as it will delete all these things and most likely break the system.

---

