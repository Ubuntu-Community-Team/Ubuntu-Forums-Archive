---
title: "Can t update kubuntu"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by cyberlite on 2007-11-11
Hi all

when I try to update to 7.10 I get this error.

*Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

Can somebody help me?:confused:

---

### Post by taurus on 2007-11-11
Maybe that site is down or dead.  So, why don't you edit /etc/apt/sources.list

```
kdesu kwrite /etc/apt/sources.list
```
and place a # in front of that repo to comment it out.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by por100pre1 on 2007-11-11
```
kdesu kate /etc/apt/sources.list
```

Comment out (add a # at the begining of the line of) that unsupported repository.

EDIT: Too late!

---

### Post by msak007 on 2007-11-11
I would just delete the offending entries rather than edit them out. I'm not sure what that repository is, but if you want an official Wine repository for Ubuntu just follow the instructions from the WineHQ site:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

