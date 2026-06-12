---
title: "Unable to add freecontrib.org repositories"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by taugust04 on 2006-12-11
Hello,

I am following the steps from ubuntuguide.org to add the additional repositories for adding and updating additional software.  I am unable to get the pgp key from packages.freecontrib.org, nor am I able to see the repositories.  Is anyone else having this problem here getting these errors?  Thanks in advance.

Error messages:

[I][INDENT]taugust04@MCK002TA-Ubuntu:~$ wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
Password:--16:03:18--  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
           => `-'
Resolving packages.freecontrib.org... 88.191.33.6
Connecting to packages.freecontrib.org|88.191.33.6|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:03:18 ERROR 404: Not Found.
[/INDENT][/I]

[I][INDENT]Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT][/I]

---

### Post by bapoumba on 2006-12-11
Hi, before you add these repositories, were you able to perform updates/upgrades ?

Could you post the output of **cat /etc/apt/sources.list** ?

---

### Post by taugust04 on 2006-12-11
> **bapoumba said:**
> Hi, before you add these repositories, were you able to perform updates/upgrades ?

Could you post the output of **cat /etc/apt/sources.list** ?

Sure can.  Here you go.  And to answer your first question, yes I was able to update before the modifications were made.  I installed on Friday and ran updates, and today was when I was adding additional repositories.  I just ran software update and it found and downloaded 82 updates after adding the additional repositories.  Freecontrib seems to be the only one giving me problems.

[I][INDENT]## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen
[/INDENT][/I]

Thanks for your assistance!

---

### Post by bapoumba on 2006-12-11
I have the exact same repositories.

```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg; sudo apt-key add 12B83718.gpg
```
To get the key

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -
```
To put it in your trusted keys. You may have more luck with a 2 different steps process, rather than doing it all at once (as you indicated in your first post) ;)

---

### Post by xabbott on 2006-12-11
Freecontrib has been timing out for the last two days for me. So maybe that is the problem.

---

### Post by bapoumba on 2006-12-11
> **xabbott said:**
> Freecontrib has been timing out for the last two days for me. So maybe that is the problem.

OK, sorry (I comment out these repositories, just check them up when I need something) :/
```
Err http://packages.freecontrib.org edgy-plf/free Packages
  404 Not Found

```

---

### Post by yabbadabbadont on 2006-12-11
The PLF dropped support for Ubuntu.  However, I read in another thread that a new maintainer may have been found.

---

### Post by bapoumba on 2006-12-12
Okay, here are new edgy repositories for proprietary packages :
```
## PLF
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free

```

And the gpg key :
```
 wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```

For breezy :
```
deb http://medibuntu.sos-sts.com/repo/ breezy free
deb http://medibuntu.sos-sts.com/repo/ breezy non-free
deb-src http://medibuntu.sos-sts.com/repo/ breezy free
deb-src http://medibuntu.sos-sts.com/repo/ breezy non-free
```

For dapper :
```
deb http://medibuntu.sos-sts.com/repo/ dapper free
deb http://medibuntu.sos-sts.com/repo/ dapper non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free
deb-src http://medibuntu.sos-sts.com/repo/ dapper non-free
```

These are maintained by a french team, documentation in [french]("http://blog.racoon97.net/index.php?2006/12/11/70-les-plf-sont-morts-vive-medibuntu").

Here are other [repositories]("http://ubuntuforums.org/showpost.php?p=1873933&postcount=2").
[https://help.ubuntu.com/community/RestrictedFormats#w32codecs]("https://help.ubuntu.com/community/RestrictedFormats#w32codecs")

---

### Post by xabbott on 2006-12-12
Thank you Bapoumba

---

### Post by bapoumba on 2006-12-12
Welcome :)

---

### Post by kibbled_bits on 2006-12-12
Yes thanks very much bapoumba.  Thanks to you some wikis will be up to date.

---

### Post by bapoumba on 2006-12-12
How funny, I am currently writing an email to the wiki team ;)

---

### Post by taugust04 on 2006-12-19
Thanks for your help.  I noticed that the documentation has changed.  I'm glad it was an actual problem and not something that required me to wake up my brain with several cups of coffee, as I was trying to troubleshoot this for several hours last week! :) 

-Ted

---

