---
title: "Synaptic hanging up"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-02-13
I just tried Synaptic for the first time installing Edgy. I hit reload and it went to 21 of 42 files then it stopped working. Here's some messages:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)

I don't know if that helps, but I also tried to install Abiword and it froze up. What causes this?

---

### Post by an.echte.trilingue on 2007-02-14
You might get better error messages if you do this:

```
sudo aptitude update
sudo aptitude install abiword
```

And then see what happens...

---

### Post by geovino on 2007-02-17
I got it working... thanks

---

