---
title: "Synaptic Error"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by mr2v6 on 2007-09-25
Hello,
I got this error while working on an app for the synaptic to read.

E: Malformed line 50 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I need help, I don't want to reinstall ubuntu again.
thanks,
Raymond

---

### Post by Maestro23 on 2007-09-25
Post your sources.list file:

> cat /etc/apt/sources.list

---

### Post by overdrank on 2007-09-25
> **mr2v6 said:**
> Hello,
I got this error while working on an app for the synaptic to read.

E: Malformed line 50 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I need help, I don't want to reinstall ubuntu again.
thanks,
Raymond

Hi you can edit your source list with this command
```
gksudo gedit /etc/apt/sources.list

```
It is telling you there is a problem with line 50 if your need help post the output here.

---

### Post by mr2v6 on 2007-09-26
Hello,
This is the lines 43-50 from sources.list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary  <<<<<<--- LINE 50

thanks,
Raymond

---

### Post by zvacet on 2007-09-26
Delete last two lines and save the file.Try this

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

