---
title: "Disable error reporting in Ubuntu Edgy [Resolved]"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by tauko on 2006-12-12
Hello!

To the point: could someone tell me how to disable the automatic bug reporting? It really gets annoying to have it popping up every time bittornado crashes, or any other programs.

By the way, if there isn't an option to enable/disable (I was unable to find one) there should be. One of the many good things in GNU\Linux it's that there aren't those windows-like pop ups asking/informing every time some stupid things.

Thanks in advance!

---

### Post by aysiu on 2006-12-12
Have tried this? ```
sudo apt-get remove bug-buddy
```

---

### Post by tauko on 2006-12-12
That worked!

Thank you very much!!!

---

### Post by ciscosurfer on 2006-12-15
> **aysiu said:**
> Have tried this? ```
sudo apt-get remove bug-buddy
```What's the best way to go about this without removing ubuntu-desktop (or does that even matter; will an immediate reinstall of ubuntu-desktop take care of that? Or is there something else I'm missing.  I haven't tried removing any packages that also say remove ubuntu-desktop, so I don't know.)  Both aptitude *and* apt-get seem to want to grab ubuntu-desktop. :-k  Seems like they're intertwined, bug-buddy and the metapackage, that is.

---

### Post by yabbadabbadont on 2006-12-15
The ubuntu-desktop meta-package depends on bug-buddy, so if you remove bug-buddy, ubuntu-desktop will be removed as well.  It normally shouldn't hurt anything.  I believe that for every day use, the only time it would matter is when they decide to add a new package to the default ubuntu-desktop installation.  However, if you decide to upgrade to a new release of Ubuntu, then you should reinstall ubuntu-desktop before performing the upgrade.  (I'm pretty sure that is one the steps that was listed when upgrading from Dapper to Edgy)

---

