---
title: "cant upgrade"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-04-21
when i try to upgrade with synaptic i get AUthentication failed 
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

any ideas??

thanks

---

### Post by GSF1200S on 2007-04-21
> **jinxjinx said:**
> when i try to upgrade with synaptic i get AUthentication failed 
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

any ideas??

thanks

Upgrade what? The Distribution? Is it if you try to upgrade anything?

Let us know..

---

### Post by jinxjinx on 2007-04-21
ya, trying to upgrade the distribution from 6.10 to 7.04...any ideas whats wrong?

---

### Post by supergrapeman on 2007-04-21
> **jinxjinx said:**
> ya, trying to upgrade the distribution from 6.10 to 7.04...any ideas whats wrong?

Same here..

---

### Post by supergrapeman on 2007-04-21
> **supergrapeman said:**
> Same here..

oh, looks like the problem is mentioned here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading). Hopefully this fixes it..

---

### Post by bobbob1016 on 2007-04-21
I got the upgrade working by installing the "update manager" release something or other.  I search  for "update-manager" or "update" and install the "update realease something".

---

### Post by jinxjinx on 2007-04-28
ok now i get this error when i try to upgrade:


Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://media.blutkind.org/xgl/dists/edgy/main/binary-i386/Packages.gz](http://media.blutkind.org/xgl/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://media.blutkind.org/xgl/dists/edgy/(latest:/binary-i386/Packages.gz](http://media.blutkind.org/xgl/dists/edgy/(latest:/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://media.blutkind.org/xgl/dists/edgy/beryl/binary-i386/Packages.gz](http://media.blutkind.org/xgl/dists/edgy/beryl/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://media.blutkind.org/xgl/dists/edgy/0.1.1)/binary-i386/Packages.gz](http://media.blutkind.org/xgl/dists/edgy/0.1.1)/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/edgy/Release](http://download.tuxfamily.org/3v1deb/dists/edgy/Release) Unable to find expected entry  (/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://beryl.xglusers.de/dists/edgy/main/binary-i386/Packages.gz](http://beryl.xglusers.de/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://beryl.xglusers.de/dists/edgy/(latest:/binary-i386/Packages.gz](http://beryl.xglusers.de/dists/edgy/(latest:/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://beryl.xglusers.de/dists/edgy/beryl/binary-i386/Packages.gz](http://beryl.xglusers.de/dists/edgy/beryl/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://beryl.xglusers.de/dists/edgy/0.1.4;/binary-i386/Packages.gz](http://beryl.xglusers.de/dists/edgy/0.1.4;/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://beryl.xglusers.de/dists/edgy/no/binary-i386/Packages.gz](http://beryl.xglusers.de/dists/edgy/no/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://beryl.xglusers.de/dists/edgy/aquamarine)/binary-i386/Packages.gz](http://beryl.xglusers.de/dists/edgy/aquamarine)/binary-i386/Packages.gz) 404 Not Found

---

### Post by Seisen on 2007-04-28
Those repo's might have been moved or they no longer exist.

---

