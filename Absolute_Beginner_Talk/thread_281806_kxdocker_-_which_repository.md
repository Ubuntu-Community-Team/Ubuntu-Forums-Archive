---
title: "kxdocker - which repository?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by walding on 2006-10-21
Hi all,

I'm trying to install kxdocker, but it isn't in my repositories list.  Does anyone know which repository I need in my sources.list to be able to install it?

Thanks

AW

---

### Post by taurus on 2006-10-21
Maybe you need to able both universe & multiverse in /etc/apt/sources.list...
From a prompt,

```
sudo nano -B /etc/apt/sources.list
```
and remove the # sign in front of lines that have universe & multiverse.

---

### Post by ayoli on 2006-10-21
yes i can confirm it's in universe/x11 section.

---

### Post by walding on 2006-10-22
Thanks.  I must have something wrong with my repositories...they've been playing up since I ran Automatix.
Could you post a sources.list, please?  Or is the one at ubuntuguide.org fine to use?

AW

---

### Post by walding on 2006-10-23
I can't find kxdocker on any repository that I have (Automatix created ones or the recommended ubuntuguide ones).  Does anyone have the sources.list line that I require, please?

Thanks

Andrew

---

### Post by Marsolin on 2006-10-23
[KXDocker]("http://linuxappfinder.com/package/kxdocker") should be in this repo:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

---

