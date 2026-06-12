---
title: "Drupal Feisty Fawn install"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by tipalm73 on 2007-05-13
owner@tipalm:~$ sudo apt-get install drupal
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package drupal
owner@tipalm:~$ 


not finding package =[ any idead? have apache2/php5 installed 

Thanks in advance

---

### Post by wormser on 2007-05-13
I think you just need to open up the universe and multiverse repositories.

```
sudo nano /etc/apt/sources.list
```

Just uncomment the urls.

---

### Post by tipalm73 on 2007-05-13
I have all the URLs un-commented. just the cd-rom is commented.

still cannot find drupal package =[

---

### Post by Bachstelze on 2007-05-13
It definitely *is* in Universe... Did you do an *apt-get update* after you uncommented those lines ?

---

### Post by tipalm73 on 2007-05-13
yessir, and just did it again to make sure =[

Still says cant find drupal package. Should I have something other then cdrom commented in source.list?

pasting in source.list:

#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by RomeReactor on 2007-05-13
Hi. Try it like this:

```
sudo apt-get install drupal-5.1
```

---

### Post by Bachstelze on 2007-05-13
Yes indeed, it should work better that way ;)

*slaps self for not having noticed*

---

### Post by tipalm73 on 2007-05-13
YOU, I, love children?

---

### Post by wormser on 2007-05-13
> **RomeReactor said:**
> 
```
sudo apt-get install drupal-5.1
```

That should work.  When you are searching or having trouble installing a package try this first:

```
apt-cache search filename
```

---

### Post by tipalm73 on 2007-05-13
well im new =[

here is latest problem [http://tipalm.mine.nu/drupal-5.1](http://tipalm.mine.nu/drupal-5.1)

printout of file contents available upon request!

gonna break for a few and breathe = ]

Thanks in advance!

---

### Post by tipalm73 on 2007-05-13
P.S.  Is there a quick way to get to a clean slate?...without reinstalling OS can i can apache2/php5/drupal-5.1?

---

### Post by tipalm73 on 2007-05-15
Scrapped...reinstalling. Keep you all posted.

LIKE YOU CARE! \\:D/

---

