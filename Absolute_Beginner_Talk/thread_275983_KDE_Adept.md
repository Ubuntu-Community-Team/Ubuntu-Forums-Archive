---
title: "KDE Adept"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by glenduncanscott on 2006-10-12
Why after updating extra repositories is KDE Adept unable to find w32codecs and libdvdcss2, thus having to resort to this method?

Installing w32codecs Debian

```
#wget http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb

#dpkg -i w32codecs_20060611-0.0_i386.deb
```

Installing liddvdcss2 in Debian

```
#wget http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0sarge0.0_i386.deb

#dpkg -i libdvdcss2_1.2.9-0sarge0.0_i386.deb
```

Appreciate any thoughts on the subject :)

---

### Post by glenduncanscott on 2006-10-12
Just realised I'm having problems with the PLF repository which is where these files are located.

Error message:
> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems

---

### Post by meborc on 2006-10-12
i have the same issue... there was a fix posted somewhere, but it didn't help me... :) (btw - the same problem exists in dapper and edgy boxes)

---

### Post by mr_pouit on 2006-10-12
Did you try this :
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```
or this
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -
```
?

(found on [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) and [http://doc.ubuntu-fr.org//doc/plf](http://doc.ubuntu-fr.org//doc/plf) ;))

---

### Post by glenduncanscott on 2006-10-12
Interesting to note why there is no problems when using Gnome's Synaptic Package Manager

---

### Post by glenduncanscott on 2006-10-12
> **mr_pouit said:**
> Did you try this :
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```
or this
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -
```
?

(found on [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) and [http://doc.ubuntu-fr.org//doc/plf](http://doc.ubuntu-fr.org//doc/plf) ;))

Thanks mr_pouit that last code worked a treat ;)

---

