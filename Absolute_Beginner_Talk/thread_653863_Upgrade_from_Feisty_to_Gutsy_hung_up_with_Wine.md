---
title: "Upgrade from Feisty to Gutsy hung up with Wine"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by jws957 on 2007-12-30
I have tried to upgrade to 7.10 from 7.04 and each time the Update Manager hangs up when trying to download files related to Wine.  I get the following errors:

Could not download all repository indexes
[http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg)
[http://wine.budgetdedicated.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2)

I have gone into the Synaptic Package Manager and selected Wine to do a complete removal, still have the same errors (and Wine still appears under the "Applications" list).  Anybody know what I can do short of a complete clean install?

---

### Post by taurus on 2007-12-30
You need to edit your /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those repos (or all 3nd party repos) to comments them out.  Save it and see if you can upgrade to Gutsy now.

---

### Post by jws957 on 2007-12-30
I can't tell which are 3rd party repos.  The lines that do not have # in front of them are:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

I don't see any relating directly to Wine.   Which ones should I place # in front of?

---

### Post by taurus on 2007-12-30
Look in /etc/apt/sources.list.d.

```
ls -la /etc/apt/sources.list.d
```

p.s.  By the way, is the the complete list of your /etc/apt/sources.list?  Looks to me like you are missing the top half or something.

---

### Post by jws957 on 2007-12-30
That folder contains a "winehq.list" file - should I remove it?

---

### Post by taurus on 2007-12-30
You can either remove it or you can edit it and place a # in front of all the lines in there to comment them out.

---

### Post by snakeeyes on 2007-12-30
You could remoe the wine repo like others have suggested, but I really suggest a clean install cause this way who knows what could have been messes up.

---

