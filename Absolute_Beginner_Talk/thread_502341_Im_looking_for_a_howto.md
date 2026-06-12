---
title: "Im looking for a howto"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-07-16
Is there a howto on how to get Virtual Box running on a PPC? and a n00b one at that?

---

### Post by wolfen69 on 2007-07-16
Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list: 
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) edgy non-free
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) dapper non-free
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) etch non-free
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) sarge non-free
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) xandros4.0-xn non-free
The innotek public key for apt-secure can be downloaded here. You can add this key with 
apt-key add innotek.asc

The key fingerprint is 
6947 BD50 026A E8C8 9AC4  09FD 390E C3FF 927C CC73
innotek GmbH (archive signing key) <info@innotek.de>

You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++. How to install these will depend on the Linux distribution you are using. 

or, if this is too difficult, you could download automatix   [http://www.getautomatix.com/](http://www.getautomatix.com/) and get it from there.

---

### Post by compiledkernel on 2007-07-16
[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

I dont believe that Automatix supports virtualbox, or will install it. 

Try the above link for a better look into it.

---

