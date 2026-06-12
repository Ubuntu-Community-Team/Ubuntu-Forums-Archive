---
title: "Error while upgrading to Gusty"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-19
Im trying to upgrade to Gusty, but when I try it keeps telling me this message:

Failed to fetch [http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/source/Sources.gz](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/source/Sources.gz) 302 Found

What can it be?

---

### Post by linuxwizard on 2007-10-19
Try removing or disable any extra repos you added to your source list.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

