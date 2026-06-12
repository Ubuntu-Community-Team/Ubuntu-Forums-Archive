---
title: "How to remove only one package?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by WhO_KnOwS on 2006-08-18
I tried installing gdesklets today and was not happy with their current status.
I removed the gdesklets and gdesklets-data packages, but one package that got installed during the installation was python (not python-2.4). How do I remove it? Because currently if I do an apt-get remove python it wants to remove about 200 packages. And I am sure that the python package was installed only for gdesklets, so it is unnecessary now.

---

### Post by engla on 2006-08-18
You can find out what gdesklets depends on. It must be one of those python packages, I guess.
> $ **aptitude show gdesklets**
Paket: gdesklets
Ny: ja
Status: inte installerad
Version: 0.35.3-1ubuntu3
Prioritet: valbart
Sektion: universe/gnome
Paketansvarig: Clément Stenac <zorglub@debian.org>
Uppackad storlek: 2540k
Kräver: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.13.0),
         libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2),
         libfontconfig1 (>= 2.3.0), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>=
         2.10.0), libgnome-keyring0 (>= 0.4.3), libgnome2-0 (>= 2.8.0),
         libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.13.0), libgnomevfs2-0 (>=
         2.13.92-0ubuntu4), libgtk2.0-0 (>= 2.8.0), libgtop2-7 (>= 2.13.2), libice6,
         liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.12.2), libpopt0 (>= 1.7),
         librsvg2-2 (>= 2.13.4), libsm6, libx11-6, libxcursor1 (> 1.1.2), libxext6,
         libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2,
         libxrender1, zlib1g (>= 1:1.2.1), [B]python-gnome2 (>= 2.0), python-gtk2 (>=
         2.0), python-numeric (>= 23.0-7), python, python-xml, python-orbit,[/B]
         gdesklets-data
Konflikter: gdesklets-data (< 0.21)
Byter ut: gdesklets-data (< 0.21)
Beskrivning Architecture for desktop applets
 gDesklets is an architecture for "desklets", which are tiny applets sitting on your
 desktop in a symbiotic relationship of eye candy and usefulness.

 You can populate your desktop with status meters, icon bars, weather sensors, news
 tickers... whatever you can imagine... Virtually anything is possible and may even
 be available some day.

 This package only provides the gdesklets base, no applets.

---

### Post by WhO_KnOwS on 2006-08-18
It depends on several packages, but one of them (python) was not installed before so it was installed together with gdesklets. Now I removed gdesklets cause I don't like it and would like to clean the system (basically bring it back to how it was before I installed gdesklets).

The problem is that the python package took over all of the python-2.4 dependancies. So when I try to remove python synaptic (or apt-get) wants to uninstall all of the packages that would get uninstalled if I removed python-2.4

---

### Post by WhO_KnOwS on 2006-08-18
To elaborate:
I want to remove a package while at the same time keeping all of the packages that depend on it.

---

### Post by givré on 2006-08-18
Are you sure that it was relly just the python package that were install.
This one is quite a base package and lot's of package depend on it (alacarte, amarok, deskbar-applet, gnome-games, gnome-app-install)
So it's highly impossible that this package wasn't there before.

---

### Post by givré on 2006-08-18
And you can't remove package if some other depend on it.
(Actually you can, but it's **highly** not recommanded)

---

### Post by WhO_KnOwS on 2006-08-18
All of the apps you mentioned are dependant on the python-2.4 package. The python package I'm talking about is 
> ...a dependency package, which depends on Debian's default
Python version (currently v2.4).

Anyway, it's not really a big issue since the python package is only 500k or so in size, but I asked so I'd know for the future.

---

### Post by givré on 2006-08-18
Try that :
```
apt-cache showpkg python
```
This package is like a met-package which install the latest version of python, but not only, and it's why lot of package depend on it.

---

