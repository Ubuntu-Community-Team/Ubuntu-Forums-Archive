---
title: "w32codecs impossible to find?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by jon_k on 2007-03-15
Lots of forums (including here) and websites have

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

as a source for the w32codecs. However: [http://packages.freecontrib.org](http://packages.freecontrib.org) seems down. Won't even load in firefox for me (anyone else?)

I'm wondering if there is another (more reliable) repo that has the w32codecs. If somebody has a .deb package I can save for the future -- that would be even better.

Thanks.

---

### Post by kerry_s on 2007-03-15
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main 

For key->

In terminal->
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1F41B907
then
gpg --armor --export 1F41B907 | sudo apt-key add -

---

### Post by kambei on 2007-03-15
No need to add an extra software archive... you can download a *deb pkg of w32codecs from here:

wget -c \
[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)

...and install it:

sudo dpkg -i w32codecs_20061022-0.0_i386.deb

---

### Post by Najand on 2007-03-15
PLF repositories are dead,
Add the following repository to your /etc/apt/sources.list
```

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

```
For key do the following in the terminal
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```
Finally, run :
```

sudo apt-get update

```

---

### Post by hyper_ch on 2007-03-15
The w32codecs can be found in Seveas' repository.

[http://wiki.ubuntu.com/SeveasPackages](http://wiki.ubuntu.com/SeveasPackages)

---

### Post by ruffneck on 2007-03-15
Thanks guys.

---

