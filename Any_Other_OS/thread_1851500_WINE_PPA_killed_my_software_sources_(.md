---
title: "WINE PPA killed my software sources :("
date: 2011-09-28
forum: Any Other OS
---

### Post by travlemon on 2011-09-28
Hello,

I am having an issue on Linux Mint 10 KDE (based on Maverick).  I know they have their own forum, but I can't seem to get any help over there, it seems a bit dead.  Also, I think this issue is more so related to Maverick than Mint 10.  

**The Problem:**  I was going to apply a patch to WINE, which requires me to recompile.  To recompile, I have to in stall a bunch of development packages.  The WINE site suggested to add their repository.  I added their repository, and now when I try to mark any of the packages for installation, I get a message like the one below.  This is just one example:

```
libcups2-dev:
 Depends: libgnutls-dev but it is not going to be installed
```

I didn't want to mess around any further on my machine, so I fired up a VirtualBox to do more testing on the problem.  I used another Maverick-based KDE distro and got the same issue.  This packages seemed to be available before I added the WINE PPA.  As soon as I added the WINE PPA and reloaded the package list, I get the error.  Even removing the WINE PPA will not fix it now, I'm not sure what change is causing this.

I also tried running ```
sudo apt-get clean && sudo apt-get autoclean
```

Any help would be much appreciated!  I'm doing more testing, but I just don't know where to go from here.  Thanks in advance!

---

### Post by tgm4883 on 2011-09-28
How did you add the repository?

---

### Post by travlemon on 2011-09-28
> **tgm4883 said:**
> How did you add the repository?


I added it by opening Synaptic, going to Settings>Repositories and going to the "Other Software" tab and click "Add".  Then I pasted the **  *ppa:ubuntu-wine/ppa***line referenced here:  [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu).

I traced the trail of dependencies down to this package:  **libgpg-error0**.  This package is already installed,  but the package at the bottom of the dependencies requires it and gives this error: 

```
libgpg-error-dev:
  Depends: libgpg-error0 (=1.6-1ubuntu2) but 1.10-0ubuntu2~maverick1~ppa1 is to be installed
```

I'm not able to reinstall libgpg-error0.  I can remove it, but it makes me weary, as it then forces me to remove a bunch of packages that look important.

Any thoughts?

---

### Post by tgm4883 on 2011-09-28
> **travlemon said:**
> I added it by opening Synaptic, going to Settings>Repositories and going to the "Other Software" tab and click "Add".  Then I pasted the **  *ppa:ubuntu-wine/ppa***line referenced here:  [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu).

I traced the trail of dependencies down to this package:  **libgpg-error0**.  This package is already installed,  but the package at the bottom of the dependencies requires it and gives this error: 

```
libgpg-error-dev:
  Depends: libgpg-error0 (=1.6-1ubuntu2) but 1.10-0ubuntu2~maverick1~ppa1 is to be installed
```

I'm not able to reinstall libgpg-error0.  I can remove it, but it makes me weary, as it then forces me to remove a bunch of packages that look important.

Any thoughts?

Do you have any other PPA's enabled? If you go into synaptic and search for libgpg-error0 are you able to force an older version?

---

### Post by travlemon on 2011-09-28
> **tgm4883 said:**
> Do you have any other PPA's enabled? If you go into synaptic and search for libgpg-error0 are you able to force an older version?

Actually, just before you posted your response, I was messing around in Synaptic and found the option to force an older version.  I never knew about this option before, as I'm still kind of new to Linux and learning new things all the time.

Anyway,  I was able to force the older version of the package.  This required that I uninstall a few packages, but nothing critical.  I was able to install all of the required dependencies and my system is fine now.

Thanks so much for your response!

---

### Post by Perfect Storm on 2011-09-28
Moved to Other OS/Distro Talk.

---

