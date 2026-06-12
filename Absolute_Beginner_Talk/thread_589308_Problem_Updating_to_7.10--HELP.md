---
title: "Problem Updating to 7.10--HELP"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Robotchicken1886 on 2007-10-24
So i have been having this problem and i cant figure out how to fix it.   i have been trying to update to the new version of ubuntu and have been running into a problem.  when i go to update it everything is going good until i get this error

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

Note i do not have wine installed.  

please help

---

### Post by Maestro23 on 2007-10-24
You have a reference to that source in your /etc/apt/sources.list

You need to comment it out with a #, or delete it all together.  You can edit the file by:

> gksudo gedit /etc/apt/sources.list

Make the changes, save, exit.  Try your update again.

---

