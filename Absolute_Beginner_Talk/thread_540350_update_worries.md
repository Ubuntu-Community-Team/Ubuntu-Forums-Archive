---
title: "update worries"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-09-01
> Err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages
  Could not resolve 'wine.lowvoice.nl'
Fetched 16B in 2m55s (0B/s)         
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg)  Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_IN.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_IN.bz2)  Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'wine.lowvoice.nl'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Hello,
Above is part of the output of sudo apt-get update command.
Can anyone help me to resolve the above error?
Thanks

---

### Post by kostkon on 2007-09-01
There is a problem with the particular repository, I believe it is down. If this is a repository for Wine, why don't you use the official Wine repository for Ubuntu? It would be better, I believe.

If you want to know more about the official repository, check here:
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

