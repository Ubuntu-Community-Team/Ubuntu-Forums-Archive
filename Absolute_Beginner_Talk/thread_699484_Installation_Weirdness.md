---
title: "Installation Weirdness"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by LionTamerX on 2008-02-17
My sources list looks like this :

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

Did I botch something while doing the install ?

Any thoughts ?

---

### Post by uberlube on 2008-02-17
I am assuming that you are trying to upgrade to 7.10? Just use the Repositories :)

---

### Post by jan quark on 2008-02-17
puhh

go to system > administration > software sources and try to enable them all except the cd

then run 

```
sudo apt-get update
```

---

### Post by LionTamerX on 2008-02-17
> **jan quark said:**
> puhh

go to system > administration > software sources and try to enable them all except the cd

then run 

```
sudo apt-get update
```

Thanks.

That was the bit I was missing.


I am now windows free. :guitar:

---

