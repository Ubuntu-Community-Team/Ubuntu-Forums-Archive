---
title: "Problems with installing skype"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by DesignerX on 2006-05-31
good day everyone, 

I downloaded a debian package of skype from their official site.
Now when I use the dpkg -i skype...  I get the following error :

"
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3-mt | libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
"

as I understand, I need to install the libqt3-mt package.
I tired installing it with the synaptic manager but the version there is lower than needed.
So I downloaded the desired libqt3-mt package and when installing I got these 
errors :

"
libqt3-mt depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu15.
 libqt3-mt depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 libqt3-mt depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
 libqt3-mt depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0-0pre6ubuntu7.
"

As you can see, ubuntu got lower versions.
Where can I upgrade all of these packages for ubuntu ?

Your help is appriciated.

---

### Post by Jagot on 2006-05-31
Try:

```
sudo apt-get -f install
```

---

### Post by hotbrainz on 2006-05-31
I am not an expert but the way i got it done was using Automatix. It is like a huge bundle of useful software. Once you install it. It has a graphical interface and asks you which software you want to install. Skype is one of them:

This thread has all the instructions u need :)

[Automatix]("http://ubuntuforums.org/showthread.php?t=138405")

---

