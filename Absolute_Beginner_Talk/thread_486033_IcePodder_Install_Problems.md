---
title: "IcePodder Install Problems"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Pete89 on 2007-06-27
Hello,

I am trying to install a podcatcher called Icepodder and on thier webpage they say you need to have the following installed first:

python
python-xmms
bittorrent
python-wxgtk
python-pyrss2gen
python-feedparser
libwxgtk

When I try and *apt-get* python-wxgtk I get this error:

```
E: Package python-wxgtk has no installation candidate
```

And when I try and *apt-get* libwxgtk I get this error:

```
E: Couldn't find package libwxgtk
```

Whats up?

Thanks,

Pedro

---

### Post by Seisen on 2007-06-27
You need to enable the universe repos in you source list.

---

### Post by Pete89 on 2007-06-27
This is the current sources.list file:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
## Repository for Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

Do you see a problem?

Thanks again for your help

---

### Post by Seisen on 2007-06-27
Try uncommenting these to repos and see what happens

```
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
``` don't forget after you do that do this

```
sudo apt-get update
sudo apt-get upgrade
``` or aptitude

---

### Post by Pete89 on 2007-06-27
Almost there!

The error I got for python-wxgtk went away but I am still getting the same error for libwxgtk

```
E: Couldn't find package libwxgtk
```

---

### Post by Seisen on 2007-06-27
Depending on which version you need you have to add the number after it

```
sudo apt-get install libwxgtk2.4-1
``` 
or
```
libwxgtk2.6-0
```
or
```
libwxgtk2.8-0
```

---

### Post by Pete89 on 2007-06-27
But I think I already have it .... I ran:

```
$ dpkg -l | grep libwxgtk*
```

and I got back:

```
ii  libwxgtk2.6-0                          2.6.3.2.1.5ubuntu6                     wxWidgets Cross-platform C++ GUI toolkit (GT

```
 
I should be good to go no? I am not to sure what the ii symbols mean though.

Pedro

---

### Post by Seisen on 2007-06-27
If its installed then you should have any problems, it will spit some out if their is and then its back to the drawing board.

---

### Post by Pete89 on 2007-06-27
OK. I appreciate your help very much. I am VERY interested in getting all the way over to LINUX but this (podcast aggregator) and VPN client software are the only things left that I cant get to work on Ubuntu.

Hasta Luego,

Pedro

---

