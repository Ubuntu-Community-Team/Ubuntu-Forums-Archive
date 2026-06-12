---
title: "Need help installing K3b on Ubuntu Breezy"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Adam_V on 2007-07-08
Sudo apt-get install doesn't work and synaptic doesn't list it. Everything is enabled in my repository page. I tried getting it myself but 5.10 is really old and none of the repositories work. I managed to download the actual file but couldn't install it due to dependancy. I can't find a file holding everything so it can't install.

```
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on k3blibs (>= 0.12.2); however:
  Package k3blibs is not installed.
 k3b depends on kdelibs4c2 (>= 4:3.4.2); however:
  Package kdelibs4c2 is not installed.
 k3b depends on libdbus-qt-1-1c2 (>= 0.36.2); however:
  Package libdbus-qt-1-1c2 is not installed.
 k3b depends on libqt3-mt (>= 3:3.3.4); however:
  Package libqt3-mt is not installed.
 k3b depends on kdelibs-data (>= 4:3.1.4-2); however:
  Package kdelibs-data is not installed.
 k3b depends on kdebase-bin; however:
  Package kdebase-bin is not installed.
 k3b depends on kcontrol; however:
  Package kcontrol is not installed.
dpkg: error processing k3b (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 k3b

```

 So without the latest version I can't burn a cd and without being able to burn a cd I can't get the latest version leaving me screwed. So I was wondering if someone knew of a site where I can download everything or add the site to my  repository list and I'd be able to install k3b. Thanks

---

### Post by testube_babies on 2007-07-08
Here's the only advice I can give you:
[Get free up-to-date Ubuntu CD's!]("http://shipit.ubuntu.com")

On another note, have you tried other CD-burning software?

---

### Post by tchoklat on 2007-07-08
dont you have another burning app on your system?

---

### Post by Adam_V on 2007-07-08
Ya I have cdrecord and nautilus, I used nautilus but the cd wasn't bootable and it can't burn isos and cdrecord doesn't detect either one of my burners and says it won't work properly since I have linux 2.6 and its made for 2.5 or something like that.

And thanks testube, I placed a order a couple days ago but I don't really want to wait weeks :p. But then again last time I ordered it was shipped 5 days lafter my request and I got it within 2 weeks. But that was back in 05

---

### Post by deadgobby on 2007-07-08
How about 
sudo aptitude install k3b

Gobby

---

### Post by Adam_V on 2007-07-08
```
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  k3b: Depends: k3blibs (>= 0.12.2) which is a virtual package.
       Depends: kdelibs4c2 (>= 4:3.4.2) which is a virtual package.
       Depends: libdbus-qt-1-1c2 (>= 0.36.2) which is a virtual package.
       Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
       Depends: kdelibs-data (>= 4:3.1.4-2) which is a virtual package.
       Depends: kdebase-bin which is a virtual package.
       Depends: kcontrol which is a virtual package.

```

Same message after sudo aptitude update too.

---

### Post by bapoumba on 2007-07-08
Can your reach the repos? I have seen here and there that the breezy repos were not available any longer. Is it still the case ?

---

### Post by Adam_V on 2007-07-08
Ya, quite a few repositories aren't available.

---

### Post by bapoumba on 2007-07-08
Any particular reason for keeping breezy?

---

### Post by Adam_V on 2007-07-08
Unable to burn a newer version

---

### Post by bapoumba on 2007-07-09
Would you consider dist-upgrading to dapper?

---

### Post by Adam_V on 2007-07-10
If you suggest it :p

---

### Post by macogw on 2007-07-10
> **Adam_V said:**
> ```
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  k3b: Depends: k3blibs (>= 0.12.2) which is a virtual package.
       Depends: kdelibs4c2 (>= 4:3.4.2) which is a virtual package.
       Depends: libdbus-qt-1-1c2 (>= 0.36.2) which is a virtual package.
       Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
       Depends: kdelibs-data (>= 4:3.1.4-2) which is a virtual package.
       Depends: kdebase-bin which is a virtual package.
       Depends: kcontrol which is a virtual package.

```

Same message after sudo aptitude update too.

Hey my new Feisty install says that about everything I try to install!  I got to imagine it was RPM Hell as I went through packages.ubuntu.com gathering dependencies.

---

### Post by regomodo on 2007-07-10
Hmm, i just installed it now with no probs. Granted this is feisty.

Just out of curiosity, why are you using Breezy?

---

### Post by Adam_V on 2007-07-11
Screwed up my windows install and the only os cd I had was ubuntu breezy so I installed it and am unable to burn fiesty due to k3b not installing

---

