---
title: "virtualbox for 64bit feisty"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-10-15
Can anyone help me with installing VirtualBox on the 64bit version of Feisty?

I download/install it but when I enter [HTML]deb http://virtualbox.org/debian feisty non-free[/HTML]

I get an error about the PUBKEY

This is what it tells you to do, can anyone tell me what I am doing wrong please

[HTML]     * Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list:

      deb http://www.virtualbox.org/debian feisty non-free
      deb http://www.virtualbox.org/debian edgy non-free
      deb http://www.virtualbox.org/debian dapper non-free
      deb http://www.virtualbox.org/debian etch non-free
      deb http://www.virtualbox.org/debian sarge non-free
      deb http://www.virtualbox.org/debian xandros4.0-xn non-free

      The innotek public key for apt-secure can be downloaded here. You can add this key with

      apt-key add innotek.asc

    The key fingerprint is

    6947 BD50 026A E8C8 9AC4  09FD 390E C3FF 927C CC73
    innotek GmbH (archive signing key) <info@innotek.de>

    You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++. How to install these will depend on the Linux distribution you are using.
[/HTML]

Cheers

---

### Post by Skweek on 2007-10-16
I had this "problem" too.  Can anyone advise us please?

---

### Post by FredB on 2007-10-16
Grab the key, and add it.

1) Grabbing the key :

[http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc)

You'll get the key.

2) Adding it.

Open a terminal, go where you save the key, and enter :

```
apt-key add innotek.asc

```

In Synaptic, you'll get all the key you add, and the new packages.

Hope it helps a little ;)

---

### Post by Skweek on 2007-10-16
Many thanks FredB, will try when I get home.

---

