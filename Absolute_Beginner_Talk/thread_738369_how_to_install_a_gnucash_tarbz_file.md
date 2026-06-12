---
title: "how to install a gnucash tarbz file"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by corkscrew on 2008-03-28
I have gnucash 2.2.1 installed, i have been to the gnucash web site and there is a new version 2.2.4, but it is in a tar.bz2 file, I have no idea how to install this, I have looked at the readme and install files within the package and there are pages and pages of instructions that for a newbie to linux like my self are above my level at the moment. Is there not a simple how to anywhere or a deb file i can use?

---

### Post by Oldsoldier2003 on 2008-03-28
> **corkscrew said:**
> I have gnucash 2.2.1 installed, i have been to the gnucash web site and there is a new version 2.2.4, but it is in a tar.bz2 file, I have no idea how to install this, I have looked at the readme and install files within the package and there are pages and pages of instructions that for a newbie to linux like my self are above my level at the moment. Is there not a simple how to anywhere or a deb file i can use?

try[ getdeb.net]("http://www.getdeb.net/") they have[ it]("http://www.getdeb.net/search.php?keywords=gnucash")

---

### Post by corkscrew on 2008-03-28
thanks, there are 2 to download gnucash 1.8mb and gnucash-common 4.6 mb any idea what the difference is and do i have to uninstal previous version first?

---

### Post by Oldsoldier2003 on 2008-03-28
> **corkscrew said:**
> thanks, there are 2 to download gnucash 1.8mb and gnucash-common 4.6 mb any idea what the difference is and do i have to uninstal previous version first?

you need both. and yes its usually best to uninstall the old version first:
```
sudo apt-get remove gnucash
```

---

### Post by qamelian on 2008-03-28
> **corkscrew said:**
> thanks, there are 2 to download gnucash 1.8mb and gnucash-common 4.6 mb any idea what the difference is and do i have to uninstal previous version first?
You need both files, but you do not need to uninstall the previous version first unless instructed to do so.

---

### Post by Oldsoldier2003 on 2008-03-28
> **qamelian said:**
> You need both files, but you do not need to install the previous version first.

when installing something from getdeb its usually safer to uninstall your current version because they do not follow Debian and Ubuntu package management guidelines.* Better safe than sorry...*

---

### Post by qamelian on 2008-03-28
> **Oldsoldier2003 said:**
> when installing something from getdeb its usually safer to uninstall your current version because they do not follow Debian and Ubuntu package management guidelines.* Better safe than sorry...*
Maybe so, but I have never had to do so and I frequently use packages from getdeb.

---

### Post by Oldsoldier2003 on 2008-03-28
> **qamelian said:**
> Maybe so, but I have never had to do so and I frequently use packages from getdeb.

one particular package that WILL mess you up if you don't uninstall is pidgin.When you don't follow the standards the change of a botched install goes up exponentially. odds are if you use getdeb enough something WILL break... GIMP tends to act silly too if you mix getdeb with Ubuntu repos.

---

### Post by corkscrew on 2008-03-28
ok i have both downloaded does it matter which order i use them in?

---

### Post by LowSky on 2008-03-28
i beleve you need to install common first

---

### Post by Oldsoldier2003 on 2008-03-28
> **LowSky said:**
> i beleve you need to install common first

+1 Common data is usually the first package to install. what sucks is when you get about 4 packages and have to figure out the order they need to be installed.

---

### Post by corkscrew on 2008-03-28
thanks for your help, i'll give it a go now

---

