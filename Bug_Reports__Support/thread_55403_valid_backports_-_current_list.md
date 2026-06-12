---
title: "valid backports - current list"
date: 2005-08-08
forum: Bug Reports / Support
---

### Post by Benchrest on 2005-08-08
I have been testing with Ubuntu near a month and overall its going great! But I am a little confused about backports. I have the following entries I got from the Unofficial Ubuntu 5.04 Starter Guide:

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

But reading stickies and other entries about current deb entries for backports I get the impression these maynot be the most current or only backport deb entries I should be using.

It would be nice if there was a sticky listing ALL the current valid backport entries that could be cut and pasted into sources.list. Even a description of each entry and what its for would be nice, all in one entry.

If this is not possible because I don't understand something I would appreciate advice on that too.

Thanks,
Rich

---

### Post by jasmuz on 2005-08-08
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#Nerim-Debian
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

#Backup Mirror - SLOW
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

##E-17 for Ubuntu
#deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/

---

### Post by Benchrest on 2005-08-08
Thanks for the list. I've made the update and received 32 new packages. I need to review the meaning of the universe multiverse etc. I know where it is and have read it but need to read it again. I'm dangerous now cause I think I'm starting to get the hang of this. :grin:

---

### Post by Mez on 2005-08-12
Please! remove the marillat repositories people! they can cause a LOT of problems with ubuntu, espescially because things are going to be binary incompatible very VERY soon

---

