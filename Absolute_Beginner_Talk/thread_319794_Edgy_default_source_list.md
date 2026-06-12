---
title: "Edgy default source list"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-12-16
I updated from dapper to Edgy and would like an updated source list.  When I do an update I always get a notice that one of my sources isn't responding or isn't right.  It is really annoying.  I feel I might be missing updates due to it.  Can some expert post their source.list for me to copy that isn't having any errors updating.  Thanks.

---

### Post by Bachstelze on 2006-12-16
Here's mine (actually it's my Dapper source.list where I just changed dapper to edgy but it will work fine) :

```
deb http://fr.archive.ubuntu.com/ubuntu edgy main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://fr.archive.ubuntu.com/ubuntu edgy-updates main restricted

#deb-src http://fr.archive.ubuntu.com/ubuntu edgy main restricted
#deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
#deb-src http://fr.archive.ubuntu.com/ubuntu edgy-updates main restricted

deb http://fr.archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb http://fr.archive.ubuntu.com/ubuntu edgy-updates universe multiverse

#deb-src http://fr.archive.ubuntu.com/ubuntu edgy universe multiverse
#deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse
#deb-src http://fr.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
```

It uses fr.archive.ubuntu.com but you can use another mirror closer to you if you want.

---

### Post by morequarky on 2006-12-16
bows humbly.  Thanks.

---

### Post by araz on 2006-12-16
Search in [this]("http://ubuntuforums.org/showthread.php?t=265326") examples what you want

---

### Post by morequarky on 2006-12-19
Ok, Can someone post a sourse.list full of TRUSTED repos only please :)

Thanks ARAZ

---

### Post by macogw on 2006-12-19
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```

^^^^
That's the one listed in the UbuntuGuide.  They're all trusted, as is the first list posted.  Remove backports and plf if you want to.

---

### Post by ubuntu27 on 2007-01-04
This could be useful for you, an utility to create a source list:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

