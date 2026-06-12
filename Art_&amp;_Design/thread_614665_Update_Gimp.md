---
title: "Update Gimp?"
date: 2007-11-16
forum: Art &amp; Design
---

### Post by Naatan on 2007-11-16
The Ubuntu repos still has GIMP 2.4 RC 3, I'd like to install GIMP 2.4.1 but I don't want to sacrifice my current installation (eg. I want to keep all my settings and plugins)

If I do a normal remove of GIMP 2.4 RC 3 with apt-get and build GIMP 2.4.1 from source will I still have all these settings?

---

### Post by rsambuca on 2007-11-16
> **Naatan said:**
> The Ubuntu repos still has GIMP 2.4 RC 3, I'd like to install GIMP 2.4.1 but I don't want to sacrifice my current installation (eg. I want to keep all my settings and plugins)

If I do a normal remove of GIMP 2.4 RC 3 with apt-get and build GIMP 2.4.1 from source will I still have all these settings?

What is in 2.4.1 that you need?  You can't just wait?

---

### Post by CarpKing on 2007-11-16
> **rsambuca said:**
> What is in 2.4.1 that you need?  You can't just wait?

Bugfixes and peace of mind ^_^

I got mine from

```
deb http://ppa.launchpad.net/madman2k/ubuntu gutsy main restricted universe multiverse
```

Just make sure you uncheck all the non-GIMP updates (I don't know what they do).

---

### Post by _sAm_ on 2007-11-16
I got mine from:
[http://www.getdeb.net/category.php?id=4](http://www.getdeb.net/category.php?id=4)

(uninstall the version in Ubuntu first)

---

### Post by Naatan on 2007-11-26
Thanks guys, and like CarpKing said: bugfixes and peace of mind (nicely said :))

For one thing the current version in the repos has a bug that makes GIMP crash at times, I havent managed to pinpoint it and am not putting any effort into doing so, but the newer versions dont seem to have this problem.

---

### Post by Paul820 on 2007-11-26
> **Naatan said:**
> Thanks guys, and like CarpKing said: bugfixes and peace of mind (nicely said :))

For one thing the current version in the repos has a bug that makes GIMP crash at times, I havent managed to pinpoint it and am not putting any effort into doing so, but the newer versions dont seem to have this problem.

If you do find bugs it would be helpful to **everyone** if you report them. Reporting bugs will make the development of your favourite programs move along much faster and let the developers concentrate on adding some new features when the bugs have been squashed. So please, report the bug, don't leave it to someone else who might take longer to find it. :)

---

### Post by ronmarley1 on 2007-12-01
> **CarpKing said:**
> Bugfixes and peace of mind ^_^

I got mine from

```
deb http://ppa.launchpad.net/madman2k/ubuntu gutsy main restricted universe multiverse
```

Just make sure you uncheck all the non-GIMP updates (I don't know what they do).

Thank you.

---

### Post by Giradman on 2007-12-01
Just out of curiosity, I'm new to Ubuntu 7.1 which installed the GIMP version mentioned in the OP; I have just started to explore this imaging program and installed the newer version on my Windows computer in the office - will the Update Manager eventually alert me to the presence of this newer GIMP version on my Ubuntu installation?  Thanks - :confused:

---

### Post by Islington on 2007-12-01
yes

---

### Post by smartboyathome on 2007-12-01
It probably won't come to Gutsy though (which is what you are running), so you will probably have to download the latest gimp from the repo posted above or from getdeb.net.

---

### Post by rsambuca on 2007-12-01
> **Islington said:**
> yes

Actually No.  At least it isn't listed on the developers site as a priority item for Gutsy.

---

