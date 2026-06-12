---
title: "Whats up with the historic version of gimp for ubuntu?"
date: 2008-12-02
forum: Art &amp; Design
---

### Post by dgrafix on 2008-12-02
2.4.6!?!?!?

Its on 2.6.3. For some reason it doesnt seem to updatesthrough apt/syn

Is it possible to apt-get this as i would rather have it installed by the package manager than trying to muck about with a .tar.gz file (last time i tried it with gimp it ended up as a mess)

---

### Post by pietjanjaap on 2008-12-02
[http://www.getdeb.net/](http://www.getdeb.net/)

Here you can download the deb.
Of course safe is only from the ubuntu server, or at least safer.

---

### Post by Izek on 2008-12-02
>>Delete Post<< Already answered above

---

### Post by dgrafix on 2008-12-02
Hmm., says it wont work until gimp-data is installed. I tried installing that and got:

> [www.gimp.orggggdpkg:](www.gimp.orggggdpkg:) considering removing gimp-python in favour of gimp-data ...
dpkg: no, cannot proceed with removal of gimp-python (--auto-deconfigure will help):
 ubuntu-desktop depedpkg: considering removing gimp-python in favour of gimp-data ...
dpkg: no, cannot proceed with removal of gimp-python (--auto-deconfigure will help):
 ubuntu-desktop depends on gimp-python
  gimp-python is to be removed.
dpkg: regarding .../gimp-data_2.6.2-1~getdeb1_all.deb containing gimp-data:
 gimp-data conflicts with gimp-python (<< 2.6.0)
  gimp-python (version 2.4.6-1ubuntu1~hardy1) is present and installed.
dpkg: error processing /tmp/gimp-data_2.6.2-1~getdeb1_all.deb (--install):
 conflicting packages - not installing gimp-data


Lol, knew it would get messy. What does all that mean :D

---

### Post by dgrafix on 2008-12-02
ah, i tried removing (fully) the old one and it seemed to work the second time.

Thanks (cool site btw!)

---

### Post by smartboyathome on 2008-12-02
Also, the reason its not updated is because once a distro is released, it is frozen except for security and major bug fixes.

---

### Post by Giant Speck on 2008-12-02
> **smartboyathome said:**
> Also, the reason its not updated is because once a distro is released, it is frozen except for security and major bug fixes.

Isn't it frozen some time before release?  I remember the 2.6 release of GIMP took place between that freeze and the release of Intrepid.

---

### Post by smartboyathome on 2008-12-02
> **Giant Speck said:**
> Isn't it frozen some time before release?  I remember the 2.6 release of GIMP took place between that freeze and the release of Intrepid.

GIMP 2.6 was released as stable near the end of the Intrepid release, and thus was able to make it into Intrepid.

---

