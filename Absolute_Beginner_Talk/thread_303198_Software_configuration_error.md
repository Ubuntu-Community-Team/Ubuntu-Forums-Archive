---
title: "Software configuration error"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by bloodfyr on 2006-11-19
I'm trying to compile software to install, and I think I'm starting to get the hang of it (being used to, you guessed it, Windows). 

I ran sudo ./confgure for a program that doesn't have a package on the repositories, and got this error:

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

Help?

---

### Post by taurus on 2006-11-19
You need to install the development package for X before you can build it!

```
sudo aptitude update
sudo aptitude install xserver-xorg-dev
```
p.s.  You don't need to use sudo when you run the ./configure, not until you want to install it on your system, i.e. "sudo make install" or "sudo make checkinstall".

---

### Post by bloodfyr on 2006-11-19
I ran those commands, and it downloaded the packages okay, but I still get the same errors.

---

### Post by taurus on 2006-11-19
Or the xorg-dev package!

```
sudo aptitude install xorg-dev
```

---

### Post by bloodfyr on 2006-11-19
Now I get this error. Sorry to be such a pain.

```
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!
```

---

### Post by sbassett on 2006-11-19
Which version of Ubuntu are you using, Dapper or edgy? in edgy you would need libqt4-dev.

---

### Post by bloodfyr on 2006-11-20
I'm running Edgey, but after installing that, I still get the same error.

I've been meaning to do a fresh install anyway. Would you say that all of these packages posted are the basics required to compile software, or are there more? That way I can just grab them all in one go.

One last noobish question: Is there a difference between "aptitude" and "apt-get"?

---

### Post by dwblas on 2006-11-20
> Qt (>= Qt 3.2 and < 4.0)This package won't accept qt4.  You either have to install qt3.x or find a newer version of the package you want to install.  On the second question, I don't use KDE but I think that aptitude is just a gui for apt_get.

---

### Post by CatKiller on 2006-11-20
> **bloodfyr said:**
> I've been meaning to do a fresh install anyway. Would you say that all of these packages posted are the basics required to compile software, or are there more? That way I can just grab them all in one go.

They aren't the basics, really. **build-essential** is the **basic** package, and everything else depends on what you're trying to install. In an ideal world, the developers of the software will tell you, either on the download page, or in the README file included with the source, what the dependencies are. That's why it's so nice when the package is in the repositories already.

> One last noobish question: Is there a difference between "aptitude" and "apt-get"?

[ aptitude versus apt-get]("http://psychocats.net/ubuntu/aptitude")

---

