---
title: "installing packages from desktop (not repositories)"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-20
I don't have internet on my laptop yet to use the apt-get or aptitude commands.  I can't get internet til I install the driver.  I can't install the driver til I can compile it.  Can't do that til I get build-essential. So, I downloaded that, put it on a flash drive, and saved it to the desktop.  How do I install it from the desktop?

---

### Post by ravsh on 2006-07-20
dpkg -i PATH_TO_PACKAGE

But be careful of package dependences
First You must install package depending installed packages only

---

### Post by macogw on 2006-07-20
[http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential)
Uh, that page.  The list with the red circles.  Are those things that depend upon build-essential or are they things it depends on?  Cuz if it depends on those, and those all depend on other things...there's a huge list of things to install.

---

### Post by nalmeth on 2006-07-20
What exactly did you download onto the flash drive? build-essential is just a meta-package. unless you downloaded the whole dependency list it won't work.

All the dependencies required for build-essential are on the install CD.

Enter CD

sudo aptitude update
sudo aptitude install build-essentials

---

### Post by macogw on 2006-07-20
you can do the aptitude thing to get it from the cd instead of the online repositories? oooo nifty...

---

