---
title: "help with dependencys please..."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Lisa Y on 2008-01-20
hello all...i got a quick question....ive been trying to install Avant Window Navigator on ubuntu 7.10 and it says that i need certian dependency...and i went to synaptic package manager....and i have all the dependency...ive also trid the " sudo apt-get install <package> and i either installed it or i have the latest edition... but it wont let me install Avant Window Navigator....help will be greatly apprenticed

---

### Post by Paul820 on 2008-01-20
What file is missing? You need all these installed for it to work:

> Package: avant-window-navigator
Version: 0.2-1~getdeb1
Architecture: i386
Maintainer: João Pinto <joao.pinto@getdeb.net>
Installed-Size: 1860
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.13.2), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.6-1), libcairo2 (>= 1.4.0), libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libfontconfig1 (>= 2.4.0), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.14.0), libgnome-desktop-2 (>= 2.11.1), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.19.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.8), libpango1.0-0 (>= 1.18.2), libpopt0 (>= 1.10), libsm6, libstartup-notification0 (>= 0.8-1), libwnck22 (>= 2.19.5), libx11-6, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.29), libxrandr2 (>= 2:1.2.0), libxrender1, python-gtk2, python-cairo, 

---

