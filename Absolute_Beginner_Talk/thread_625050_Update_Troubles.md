---
title: "Update Troubles"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by barabaskid on 2007-11-27
I have been trying to update from Feisty to Gutsy using the update manager. Midway through fetching files for the update, I receive an error message saying "A Problem Occured during update. This is usually a problem with the network". The message then reads:

> 
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


This happens every time I try to update. I tried uninstalling wine, but the problem persisted. Any thoughts would be appreciated!

BarabasKid

---

### Post by angryfirelord on 2007-11-27
Looks like a problem with the server. I would remove those repositories and use this one instead: [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

