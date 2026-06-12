---
title: "What plugins are needed to play *.avi files"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-01-07
Tia

---

### Post by bored2k on 2006-01-07
Automatix: install nonfree codecs. [http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)
Totem-xine too.

---

### Post by The Pinny Parlour on 2006-01-07
That installs a whole heap of stuff I dont know about or want.  Is there something else?  Thank you

---

### Post by bored2k on 2006-01-07
```
sudo gedit /etc/apt/sources.list

```Replace whatever you have with these lines:```
#KDE 3.5
deb http://kubuntu.org/packages/kde35 breezy main

##PLF (tempo)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

##Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging restricted

##OOo2 Final
deb http://people.ubuntu.com/~doko/OOo2 ./

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```After doing so (and saving),
```
sudo apt-get update
```
```
sudo apt-get install w32codecs totem-xine 
```

---

### Post by The Pinny Parlour on 2006-01-07
Is it safe to do so?  What am I deleting and replacing with?  Will it do harm?

---

### Post by bored2k on 2006-01-07
You're replacing them because the default Ubuntu ones do not contain certain files. No, they won't do harm. Yes, they're safe.

---

### Post by bored2k on 2006-01-07
[QUOTE=The Pinny Parlour]That installs a whole heap of stuff I dont know about or want.  Is there something else?  Thank you[/QUOTE]
It does not install anything you don't tell it to, and it's pretty much the best script Ubuntu has ever seen.

---

### Post by The Pinny Parlour on 2006-01-07
Thanks for your encouragement to install it.  It's is great  :)

---

