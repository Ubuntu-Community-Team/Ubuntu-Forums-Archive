---
title: "Firestarter install problems"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by dynacrylic on 2006-10-25
I've been trying to install firestarter but have been unsuccessful.  I'm running ubuntu 6.06.

The error i'm getting is "E: Couldn't find package firestarter".  I thought I added the right repository. Here is what I got listed in my repos:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                                                                                                                                                                      

## UNIVERSE AND MULTIVERSE REPOSITORY
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) dapper-security universe multiverse

Any help is appreciated.

---

### Post by TitusDalwards on 2006-10-25
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=dapper&release=all)

it must be in universe, i think if you use apt maybe you write wrong or didn't case-sensitive. You can try with Synaptic.

---

### Post by dynacrylic on 2006-10-25
> **TitusDalwards said:**
> [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=dapper&release=all)

it must be in universe, i think if you use apt maybe you write wrong or didn't case-sensitive. You can try with Synaptic.

I've tried "apt-get install Firestarter" and "apt-get intstall firestarter". Firestarter is not showing up in the Synaptic.  

Is my repository list wrong?

---

### Post by bswilson on 2006-10-25
Your repository list appears to be correct.  Try this command to see if **firestarter** is a listed package.  If it does not show up, then your repositories are incorrect.

```
sudo apt-cache search firestarter
```

---

### Post by TitusDalwards on 2006-10-25
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## ANA SORUN G&#304;DERME GÜNCELLEMELER&#304; son sürüm ç&#305;ktan sonra haz&#305;rland&#305;

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU GÜVENL&#304;K GÜNCELLEMELER&#304;
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


here is my repos,with this i have just checked and found firestarter, can you use mine, if you want.

---

### Post by Bachstelze on 2006-10-25
I guess you simply forgot to apt-get update after adding the repo ;)

---

### Post by dynacrylic on 2006-10-25
> **HymnToLife said:**
> I guess you simply forgot to apt-get update after adding the repo ;)

that be it. thanks for helping me look stupid ;)


(seriously, thanks so much)

---

