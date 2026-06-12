---
title: "Upgrade Error"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Mr. Win on 2008-04-10
This is the error I continue to get- I'm an |newb|.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

Thanks in advance!

-Win

---

### Post by Oldsoldier2003 on 2008-04-10
> **Mr. Win said:**
> This is the error I continue to get- I'm an |newb|.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

Thanks in advance!

-Win
take those repos out of your sources and everything will be fine. System>Administration>Software Sources:
The repos you are having issues with  should be on the second tab. Just uncheck them and you wont error out on them
on the first tab if you check the first four repos it should be good. Then run 
```
sudo apt-get update
sudo apt-get upgrade
```

---

