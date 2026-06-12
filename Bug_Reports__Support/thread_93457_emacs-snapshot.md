---
title: "emacs-snapshot"
date: 2005-11-22
forum: Bug Reports / Support
---

### Post by Gustav on 2005-11-22
It won't install and apt-get say that there is broken packages.

Following packages has dependencies that can't be fulfilled:
  emacs-snapshot-gtk: Depends: emacs-snapshot-bin-common (= 1:20051111-1~breezy1) but it won't be installed
E: Broken packages

and if I try to install emacs-snapshot-common (wich emacs-snapshot-bin-common depends on) it tries to remove OpenOffice.org

---

### Post by Manny C on 2005-11-22
What is in your /etc/apt/sources.list file?

---

### Post by Gustav on 2005-11-22
[QUOTE=Manny C]What is in your /etc/apt/sources.list file?[/QUOTE]
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe 

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy multiverse 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted multiverse universe

## The Ubuntu backports project

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) breezy-extras main universe restricted multiverse

---

### Post by Manny C on 2005-11-22
Aha. First you seem to be missing the breezy-updates repositories. Second, I get the same error on mine and I do have the breezy-updates repositories set up. 

To correct the first, add the following to your sources.list file:
```
deb http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

```

For the second error, I'm afraid that waiting will be the only solution.

---

### Post by Gustav on 2005-11-22
Thank you!

---

### Post by duffman25 on 2005-11-22
[QUOTE=Gustav]Thank you![/QUOTE]
I'm having the same problem. Cannot install the emacs-snapshot backport.

---

### Post by Manny C on 2005-11-23
The solution is to wait until jdong gets around to fixing it. Patience people, patience. :)

jdong is doing a hard job very well.

---

### Post by duffman25 on 2005-11-23
[QUOTE=Manny C]The solution is to wait until jdong gets around to fixing it. Patience people, patience. :)

jdong is doing a hard job very well.[/QUOTE]

Yes, I was only confirming the situation. I really appreciate jdong's/backport team efforts. Without them Ubuntu wouldn't rock as hard as it does :)

---

### Post by Manny C on 2005-11-30
Hi jdong...any news on this front?

---

### Post by toojays on 2005-12-03
The problem is that a newer version of dictionaries-common is required, but it isn't in backports. I downloaded a version from [http://mikesplanet.net/deb/dictionaries-common_0.62.3ubuntu1~breezy_all.deb](http://mikesplanet.net/deb/dictionaries-common_0.62.3ubuntu1~breezy_all.deb) (mentioned in another post) and it works okay for me.

---

### Post by bored2k on 2005-12-14
[QUOTE=toojays]The problem is that a newer version of dictionaries-common is required, but it isn't in backports. I downloaded a version from [http://mikesplanet.net/deb/dictionaries-common_0.62.3ubuntu1~breezy_all.deb](http://mikesplanet.net/deb/dictionaries-common_0.62.3ubuntu1~breezy_all.deb) (mentioned in another post) and it works okay for me.[/QUOTE]
Thanks. That worked.

---

### Post by simon_cheng on 2005-12-18
It really works! Cool!

---

