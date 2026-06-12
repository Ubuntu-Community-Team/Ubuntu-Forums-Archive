---
title: "upgrade from 7.04 to 7.10 wine"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-10-28
Upon hitting the upgrade to 7.10 button it does things for a min or two, then it returns this error involving wine.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

I have run both apt-get remove wine and aptitude remove wine, and it still thinks that wine is installed on my system.  Any ideas.

Thanks

---

### Post by mc4man on 2007-10-29
Maybe you used that automatix to install wine - better to use ubuntu repo's
try editing source list
```
gksudo gedit /etc/apt/sources.list

```
find the line(s) with lowvoice.nl and comment them out
or maybe uncheck it from 3rd party software in admin. - software sources if it's listed

---

### Post by devilears on 2007-10-29
in your /etc/apt/sources.list file, just comment out the lowvoice entry like this: 

 ###deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

---

### Post by zvacet on 2007-10-29
Or you can delete that line and go to this link

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

