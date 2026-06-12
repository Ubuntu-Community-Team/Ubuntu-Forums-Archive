---
title: "installing rpm packages"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by cdot85 on 2006-07-09
When i try to install an rpm file my prompt says "bash: rpm: command not found." I also can't extract the file when i right click on it because it says it is not supported. Am i missing something that will allow me to extract rpm files? Thanks!

---

### Post by John.Michael.Kane on 2006-07-09
To install rpm files under debian you need to use alien ```
sudo aptitude install alien
```

---

### Post by mostwanted on 2006-07-09
and then

alien -i package.rpm

---

### Post by taurus on 2006-07-09
You need to use alien (as SD-Plissken already told you) to convert the .rpm to .deb...
```

sudo apt-get install alien <-- to install alien if you don't have it on your system
alian <filename>.rpm <-- to convert .rpm to .deb
sudo dpkg -i <filename>.deb <-- to install the program

```

---

### Post by cdot85 on 2006-07-09
thank you for the help! do you know if theres any way to install alien if i dont have my install disc on me?

---

### Post by loell on 2006-07-09
then after alien is installed

you then enter the command

   
     alien filename.rpm

it will then be converted to deb package :)

---

### Post by kc5hwb on 2006-07-09
I am new to Ubuntu also, but shouldn't he be able to install Alien with the Synaptic Pkg Manager?

---

### Post by loell on 2006-07-09
> **kc5hwb said:**
> I am new to Ubuntu also, but shouldn't he be able to install Alien with the Synaptic Pkg Manager?

yes kc5hwb, anyone can with synaptic

---

### Post by taurus on 2006-07-09
> **cdot85 said:**
> thank you for the help! do you know if theres any way to install alien if i dont have my install disc on me?
And I assume you don't have network connecting on your machine either!  Well, you can download from another machine and copy to your machine to install it.  Here is what you need...

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Falien%2Falien_8.50_all.deb&md5sum=96aa7edafdc2961f771d836354b34b3a&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Falien%2Falien_8.50_all.deb&md5sum=96aa7edafdc2961f771d836354b34b3a&arch=all&type=main)

You can install that with (from a terminal)
```

sudo dpkg -i alien_8.50_all.deb

```

---

### Post by cdot85 on 2006-07-09
> **taurus said:**
> 
You can install that with (from a terminal)
```

sudo dpkg -i alien_8.50_all.deb

```

When i did that it said,

```
Selecting previously deselected package alien.
(Reading database ... 63654 files and directories currently installed.)
Unpacking alien (from alien_8.50_all.deb) ...
dpkg: dependency problems prevent configuration of alien:
 alien depends on debhelper (>= 3); however:
  Package debhelper is not installed.
 alien depends on rpm (>= 2.4.4-2); however:
  Package rpm is not installed.
 alien depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 alien depends on make; however:
  Package make is not installed.
dpkg: error processing alien (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alien

```

Any ideas?

---

### Post by Apple 101 on 2006-07-09
Install *alien* and its dependencies (should be automatically selected) in Synaptic and then try again.

---

