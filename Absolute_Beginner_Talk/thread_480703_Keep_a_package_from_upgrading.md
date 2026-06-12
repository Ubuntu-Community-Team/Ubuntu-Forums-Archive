---
title: "Keep a package from upgrading?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Megatog615 on 2007-06-21
I've built a package from source. I'd like to know if it's possible to prevent a dist-upgrade from trying to upgrade the package to the one that is online(which is exactly the same version), and only try to upgrade it if there is a newer version available.

---

### Post by paparucino on 2007-06-21
> **Megatog615 said:**
> I've built a package from source. I'd like to know if it's possible to prevent a dist-upgrade from trying to upgrade the package to the one that is online(which is exactly the same version), and only try to upgrade it if there is a newer version available.

If you use synaptic you can mark the program as not to upgraded.
but this works in synaptic, if you use apt-get, that flag is not seen and the program will be upgraded.

Or... you could try by changing the version number to a very high one (e.g. 99.99.99.99)

---

### Post by mbsullivan on 2008-01-29
Although this question was asked fairly long ago, I'll make a point for those who stumble across the thread... From the command line (i.e. using apt-get or aptitude instead of synaptic), you can use "apt-pinning" to prevent packages from being upgraded.

This involves having multiple Ubuntu releases in your /etc/apt/sources.list file and editing your /etc/apt/preferences to give certain packages a higher priority than others.  A tutorial can be found[here]("http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu") and a description of apt/preferences can be found [here]("http://ccrma.stanford.edu/planetccrma/man/man5/apt_preferences.5.html").

For example, I am currently running Ubuntu Gutsy.  However, I want to prevent uswsusp from upgrading, because the new version doesn't have s2ram, and it sucks.  Also, I want to keep kvm as new as possible, so I use the following preferences file:


```
Package: *
Pin: release a=feisty
Pin-Priority: 400

Package: *
Pin: release a=gutsy
Pin-Priority: 500

Package: *
Pin: release a=hardy
Pin-Priority: 300

Package: uswsusp
Pin: release a=feisty
Pin-Priority: 1000

Package: kvm
Pin: release a=hardy
Pin-Priority: 1000
```

This will install most packages from Gutsy repositories (Feisty ones if it can't find the pacage under Gutsy).  However, it will keep uswsusp pinned under Feisty, and keep kvm as new as possible.  Note: in order for this to work, you must have repositories from multiple versions of Ubuntu added to your /etc/apt/sources.list file.

Hope this helps!
Mike

---

