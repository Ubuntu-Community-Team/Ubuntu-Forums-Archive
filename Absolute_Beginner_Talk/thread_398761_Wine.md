---
title: "Wine"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-04-01
when I do

sudo apt-get install wine

it tells me

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be insta                                                                           lled
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed
        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages
brinson@brinson-desktop:~$


Would it be wise to remove these things? I want to get wine to work, but I'd prefer not do any irrepairable damage in the process.

---

### Post by rillip on 2007-04-01
I would NOT remove these.  It looks like the versions being installed are, for the most part, newer than the versions you have.  I would first run apt-get update and apt-get updgrade, then try reinstalling.  If tht fails, I would give up on installing from the packageeither add the wine repositories or to download Wine in another form (i.e. source, think they offer a .deb, etc).

---

### Post by zvacet on 2007-04-01
You are missing dependencies.Try go to the synaptic>edit>fix broken packages.If that doesn´t work
```
 sudo apt-get remove wine 
```
Install wine with synaptic or with this command
```
sudo aptitude install wine
```

---

