---
title: "One nagging question about automatix2"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by kpkeerthi on 2006-12-14
Is automatix2 just a graphical installer so we do not have to type apt-get install package1, package2, etc? Or has an added advantage of auto-configuring the package. And... does it add additional repos in sources.lst so that packages installed through automatix2 are more up-to-date and latest than what standard Ubuntu repos offer? What's the deal?

---

### Post by finferflu on 2006-12-14
It adds additional repositories and you can install extra stuff. There is also a version called Automatix 2 Bleeder, with which you can install bleeding edge apps, such as Beryl.

I've heard somebody say that it's not safe for your system, though. But I don't know exactly why...

---

### Post by Circus-Killer on 2006-12-14
as far as i know, its just there so that you dont have to manually install it through apt-get. as for the repos. i'm 90% sure that it only enables the universe and multiverse repositories, much like you would do if you were manually installing the packages.

personally, i prefer to go the manual route. that way i know exactly whats being installed.

---

### Post by finferflu on 2006-12-14
It adds the following:

```
#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe mult$
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe $

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiv$
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe mu$

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multi$
deb-src http://archive.ubuntu.com/ubuntu edgy-security main restricted universe m$

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse$
#AUTOMATIX REPOS END
```

---

### Post by TrendyDark on 2006-12-14
Does anyone know why the forum for Automatix was removed?

---

### Post by kpkeerthi on 2006-12-14
Thanks for those who replied.

> Does anyone know why the forum for Automatix was removed?
It has found its own home [http://getautomatix.com/forum/](http://getautomatix.com/forum/)

---

### Post by STREETURCHINE on 2006-12-14
i have automatix2 on both dapper and edgy it is just easier ,it installs all the media codecs and outher apps for you ,
as being un safe i have had no trouble what so ever,
being a total noob it was the best way to get things installed ,i am now starting to do things manually,
but i am still a long way from being confident with linux but i love it and no matter how many times i break it i will not put windows back on this computer.
all in all i would say load automatix2 and get the basics working .
 have fun either way.```

```

---

