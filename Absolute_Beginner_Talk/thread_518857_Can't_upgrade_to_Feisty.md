---
title: "Can't upgrade to Feisty ?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mchnhed on 2007-08-06
Everytime I try upgrading to Feisty from the "Update Manager" I get the following error...

Failed to fetch [http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz) 301 Moved Permanently


...and the only option I have is to close the window. Any ideas would be greatly appreciated!

---

### Post by Inxsible on 2007-08-06
This might not help but have you considered doing a fresh install for Feisty?

---

### Post by mchnhed on 2007-08-20
No I haven't... but if I do that won't it overwrite what I already have? I would like to keep the fstab and menu.lst files, as well as all the user logins and information. How can I upgrade to Feisty though?

Does anyone know why the Update Manager won't let me upgrade?

---

### Post by hyper_ch on 2007-08-20
Well, add other sources than the one you are using...

User settings and stuff are all in /home

Do you have that on a seperate partition?

---

### Post by jordanmthomas on 2007-08-20
Could you post your /etc/apt/sources.list?

If you just comment out your section that seems to have been added for Listen media player, you should be back in business.

---

### Post by hyper_ch on 2007-08-20
I have feisty repos and use medibuntu and some others... however for the official ones you could use the sources.list generator:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by jordanmthomas on 2007-08-20
> I have feisty repos and use medibuntu and some others... 
I was asking for mchnhed's in case you were directing that at me.  Sorry for any confusion.  ;)

---

### Post by hyper_ch on 2007-08-20
I thought it was directed at me because it was just after what I posted ;)

---

### Post by bme on 2007-08-20
Can the alternate cd of feisty be used to update?

---

### Post by hyper_ch on 2007-08-20
Those are install and not upgrade CDs... they can't be used for an upgrade.

---

### Post by bme on 2007-08-20
According to this -http://www.ubuntu.com/getubuntu/upgrading go to "upgrading using alternate cd" you can upgrade using alternate cd from 6.10 to 7.04 which is what the post is about.

---

### Post by hyper_ch on 2007-08-20
Oh you can?
My mistake ;) sorry!

---

### Post by bme on 2007-08-20
no harm done....Anyway this is better than having problems with repos...everything is already on the cd(better still the whole kitchen sink with the dvd!)
Cheers!

---

### Post by mchnhed on 2007-10-10
> **jordanmthomas said:**
> Could you post your /etc/apt/sources.list?

If you just comment out your section that seems to have been added for Listen media player, you should be back in business.


I commented out the section for Listen media player and it worked! But do you know why this was disabling the upgrade in the first place???

For the record, here is my sources.list file:

```



deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ edgy free non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
## deb http://theli.free.fr/packages/ edgy listen

```

---

