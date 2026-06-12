---
title: "installing The Mana World"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by metuwi on 2006-01-04
Help!
I have looked at some threads, but they are a little too confusing for me. Please help us newbs. Could anyone give us explicit instructions on how to install the mana world and get it to work on ubuntu/kubuntu breezy? If would be nice to have a howto for this...

---

### Post by metuwi on 2006-01-04
here is what happens:

```
sudo apt-get install tmw tmw-data tmw-music
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tmw: Depends: libcurl3-gnutls (>= 7.15.0-1) but it is not installable
       Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
       Depends: libgnutls12 (>= 1.2.5) but it is not installable
       Depends: libguichan0 but it is not going to be installed
       Depends: libidn11 (>= 0.5.18) but 0.5.13-1.0 is to be installed
       Depends: libkrb53 (>= 1.4.2) but 1.3.6-4 is to be installed
       Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
E: Broken packages

```

how can this be resolved?

---

### Post by antenagora on 2006-04-03
I' ve made some packages for themanaworld & guichan for breezy, they are here:

[http://antenagora.homeunix.org/index.php/tmw-themanaworld/](http://antenagora.homeunix.org/index.php/tmw-themanaworld/)

Just download them & dpkg -i them.
If you miss some dependency, apt-get install it. This will save you a little compilation time, even if compiling it's very easy & fast (10 minutes on a PII @ 400). Music pack it' s separate; you have to download & deflate in /usr/tmw/data/music (if i correctly remember, else find it).

bye

---

