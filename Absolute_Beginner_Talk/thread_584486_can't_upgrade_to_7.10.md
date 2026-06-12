---
title: "can't upgrade to 7.10"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by sahilsapre on 2007-10-21
i've been trying to upgrade to 7.10 for the past few days through update manager, only to get the same error everytime. it says:
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz) 302 Found

i'm attaching the screenshot of the error message..
what do i do??
i even tried downloading the 7.10 live cd and upgrading through that, but apparently, you can't use the live cd to upgrade.. so am i supposed to download the alternate text based installer instead??

---

### Post by NeoLithium on 2007-10-21
Try disabling all the third-party repositories before doing the upgrade, such as Medibuntu, etc.

---

### Post by PmDematagoda on 2007-10-21
Open up the sources.list file for editing by:-

```
sudo gedit /etc/apt/sources.list
```

Then disable all the medibuntu repositories by putting # infront of them, save and try again.

---

