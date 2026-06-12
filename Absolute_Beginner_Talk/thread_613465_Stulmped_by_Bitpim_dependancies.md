---
title: "Stulmped by Bitpim dependancies"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by mnb on 2007-11-14
Hi all,

As a recent posted commented, the BItpim in the repositories is way out of date.  Doesn't work for me.  So I tried to install the latest version from the Bitpim site (1.0.2).

I get the following dependency messages - how do I deal with these as many of these version numbers appear to be more recent than what is available from the Synaptic Package Manager?  Thanks for your help!

  bitpim: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
          Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
          Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
          Depends: libgcc1 (>= 1:4.1.2) but 1:4.1.1-13ubuntu5 is installed
          Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
          Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
          Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.3 is installed
          Depends: libreadline5 (>= 5.2) but 5.1-7build1 is installed
          Depends: libssl0.9.8 (>= 0.9.8c-1) but 0.9.8b-2ubuntu2.2 is installed
          Depends: libstdc++6 (>= 4.1.2) but 4.1.1-13ubuntu5 is installed
          Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is installed

---

### Post by jfinkels on 2007-11-15
Those are your most recent versions of those packages? Have you done:```
sudo aptitude update && sudo aptitude upgrade
```

If those are the most recent versions of those packages, then you need to upgrade your distribution from Edgy (6.10) to Feisty (7.04) (at the least). I assume you are using Edgy because searching for edgy packages on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) shows the same version numbers as you have installed. My advice is to upgrade to the latest distribution. by typing the following:```
gksudo "update-manager -c"
```

Upgrading to a more recent version will give you more recent packages for your system.

---

