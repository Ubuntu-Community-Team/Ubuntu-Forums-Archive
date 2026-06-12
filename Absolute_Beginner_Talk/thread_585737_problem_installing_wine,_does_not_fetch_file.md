---
title: "problem installing wine, does not fetch file"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by frankthomas on 2007-10-21
I keep trying to install wine so that I can update to 7.10 but I get this error everytime I try to install wine does anyone know what to do or what it means?

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 206.112.100.132 80]

---

### Post by daniel_szollosi-nagy on 2007-10-21
By the looks of it the server you are trying to get wine from no longer exists. This is probably related to a customized repository list.

This wiki page may help: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Remove wine.lowvoice.nl from the repository list and you should be fine.

---

