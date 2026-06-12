---
title: "very weird - i just uninstalled a bunch of things for no reason"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-09-19
so i was trying to install some codecs

```
sudo aptitude install lame lame-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  kaffeine kaffeine-xine konq-plugins konqueror-nsplugins kontact
  konversation kooka kopete korganizer kpersonalizer kpf kppp krdc
  kregexpeditor krfb kscreensaver kscreensaver-xsavers ksmserver ksnapshot
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-konqueror-shortcuts kwin-style-crystal latex-xft-fonts
  libavahi-compat-libdnssd1 libexiv2-0.12 libgmp3c2 libimlib2
  libjasper-runtime libjpeg-progs libkexiv2-0 libkipi0 libkpimexchange1
  libkscan1 liblockdev1 libmeanwhile1 libopenobex1 libpoppler1-qt
  libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support
  libqt4-sql librsync1 libskim0 libsmokeqt1 libsqlite0 libtdb1 ncompress
  ocrad openoffice.org-kde poster psutils pykdeextensions python-all
  python-all-dev python-dev python-elementtree python-kde3 python-qt4
  python2.4 python2.4-dev python2.4-minimal python2.5-dev qca-tls qobex
  qt4-qtconfig rdiff-backup scim-qtimm skim software-properties-kde
  speedcrunch zoo
```

i, unfortunately, did not read that part and said YES, so it started removing stuff until i noticed and closed the terminal. now programs are missing. can some1 tell me the programs it took out? i think its alphabetical, so whatever was before the kaffeine i should reinstall.

and why did that command do this? this is insane.
TIA.

---

### Post by oilchangeguy on 2007-09-19
sounds like it time to back up your data (if you can) and reinstall.

---

### Post by Miroku on 2007-09-19
is there a way to look at the logs of the terminal? so maybe i can just reinstall what i uninstalled by accident?

---

### Post by oilchangeguy on 2007-09-19
> **Miroku said:**
> is there a way to look at the logs of the terminal? so maybe i can just reinstall what i uninstalled by accident?

probably. but it may be easier just to do a reinstall. it would surely take less time.

---

### Post by rickycodie on 2007-09-19
there is no reason for this to happen as far as i can tell. re-install, that's what i would do.

---

### Post by irish_flu on 2007-09-19
Maybe I'm crazy here, but IMHO this could be solved by reinstalling the kubuntu-desktop package.

---

### Post by Miroku on 2007-09-19
yea i think i will do as you said irish_flu. but this is very strange. look at this:

```
~$ sudo apt-get install adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
amarok is already the newest version.
amarok-xine is already the newest version.
amarok-xine set to manual installed.
dcraw is already the newest version.
The following packages were automatically installed and are no longer required:
  python2.4-dev kregexpeditor acroread-escript libdc1394-13 python-all-dev
  libpythonize0 liblockdev1 libkipi0 libexiv2-0.12 libfame-0.9 libpoppler1-qt
  libpvm3 latex-xft-fonts python-all libpostproc0d python-dev libkexiv2-0
  python2.4-minimal python2.5-dev python2.4 pykdeextensions kwin-style-crystal
  poster transcode rdiff-backup psutils qobex libavcodec0d libimlib2 libdc0c2
  librsync1 libopenobex1 python-kde3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater
Suggested packages:
  khelpcenter rar
The following packages will be REMOVED:
  kubuntu-default-settings
The following NEW packages will be installed:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater akregator ark arts artsbuilder debtags
0 upgraded, 12 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7587kB of archives.
After unpacking 19.5MB of additional disk space will be used.
Do you want to continue [Y/n]?  
```

it is like deleting itself for some reason.

---

### Post by brennydoogles on 2007-09-19
> **irish_flu said:**
> Maybe I'm crazy here, but IMHO this could be solved by reinstalling the kubuntu-desktop package.

I just wonder if there is some setting screwed up in aptitude to cause this. I still recommend a fresh install.

---

### Post by Miroku on 2007-09-19
i really dont want to do a reinstall, i would lose all my settings for everything. and why would aptitude just go crazy for no reason?

---

### Post by oilchangeguy on 2007-09-19
> **Miroku said:**
> i really dont want to do a reinstall, i would lose all my settings for everything. and why would aptitude just go crazy for no reason?

you've been advised the best course of action. it's up to you to decide. and most of the time things don't go crazy on their own it's [http://en.wikipedia.org/wiki/PEBKAC](http://en.wikipedia.org/wiki/PEBKAC)

---

### Post by Miroku on 2007-09-19
it went crazy on its own!! lol

well i just did reinstall kubuntu, so lets hope its ok. the missing programs are back. but you guys are probably right, something is amiss. i will have to wait and see, ill report back.

---

### Post by insane_alien on 2007-09-19
see that list of programs it said it was removing? paste it at the end of a sudo apt-get install command. it should reinstall everything along with settings.

---

### Post by bashveank on 2007-09-19
Are you using any third-party repos?

---

### Post by vincentvee on 2007-09-20
that will do it
i'm quite certain

> **irish_flu said:**
> Maybe I'm crazy here, but IMHO this could be solved by reinstalling the kubuntu-desktop package.

---

