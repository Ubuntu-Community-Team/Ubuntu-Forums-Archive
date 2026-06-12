---
title: "is this the right forum to ask questions ...?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by retnug on 2007-11-24
I recently switched to ubuntu, and I find it great - although ...: 
- well, I am not very keen of Firefox - I prefer OPERA, for various reasons. however, when I tried to install it, I had an error message: Dependency is not satisfiable libqt3-mt. what can I do to install Opera (I downloaded the ubuntu specific file from the OPERA website).
another problem; I can't listen to mp3 (wav - files yes ...!), and I can't watch videos other than avi - and these without sound. my soundcard is working (ubuntu-checked), and ubuntu-restricted-extras are installed (green square in Synaptic Package Manager )

---

### Post by corney91 on 2007-11-24
For Opera you can install it from the repositories in Synaptic or by using```
sudo apt-get install opera
```
This will take care of the dependency error for you. If you want to use the file way, install libqt3-mt the same way as above:
```
sudo apt-get install libqt3-mt
```


Oh, and to answer the question in the subject: Yes this is the right forum to ask questions :)

---

### Post by aysiu on 2007-11-24
> **corney91 said:**
> For Opera you can install it from the repositories in Synaptic or by using```
sudo apt-get install opera
```
This will take care of the dependency error for you. If you want to use the file way, install libqt3-mt the same way as above:
```
sudo apt-get install libqt3-mt
```
[Opera isn't in the standard repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=opera&sourceid=mozilla-search).

I think a simple ```
sudo apt-get -f install
``` should take care of the dependencies.

---

### Post by corney91 on 2007-11-24
> **aysiu said:**
> [Opera isn't in the standard repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=opera&sourceid=mozilla-search).

Wow...didn't realised I had the third-party canonical repos enabled. Are they there (but not enabled) by default?

---

### Post by aysiu on 2007-11-24
> **corney91 said:**
> Wow...didn't realised I had the third-party canonical repos enabled. Are they there (but not enabled) by default?
Yes, I believe so.

---

### Post by steamshooter on 2007-11-24
retnug, the way I understand Ubuntu can't give you MP3 because of legal reasons. But YOU can put it in without a problem. Go here

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

This helped me tremendously.
Brad

---

### Post by aysiu on 2007-11-24
> **steamshooter said:**
> retnug, the way I understand Ubuntu can't give you MP3 because of legal reasons. That's part of it, but it's mostly for philosophical reasons:
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)

---

### Post by Fred_E _krugar on 2007-11-24
As for the Mp3 stuff go to the add/remove programs and install the Gstreamer plugins.

---

### Post by aysiu on 2007-11-24
This guide will help you get MP3 support installed the easy way:
[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)

---

### Post by gn2 on 2007-11-24
Best way I know of getting mp3 support and lots of other goodies is :

sudo apt-get install ubuntu-restricted-extras

PS: you'll never find a better forum than this one for getting your questions answered.  :-)

---

