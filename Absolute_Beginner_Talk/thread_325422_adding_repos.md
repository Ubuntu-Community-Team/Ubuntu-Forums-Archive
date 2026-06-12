---
title: "adding repos"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by s_x_g_t on 2006-12-25
OK so iam in the pre steps of adding Beryl and when i go to System>admin> software sources,  I can add any othe the third party things BUt when i click close in the Software sources window I get a message saying " the info about availbe software is out of date. To install software and updates from newly added or changed sources you have to reload the information about available software". I click reload   and it downloads some package information BUT THEN gives me error message when its done saying public key is not availiable.

---

### Post by r4ik on 2006-12-25
-

---

### Post by s_x_g_t on 2006-12-25
nathan@the-machine:~$ sudo apt-get update
**E: Type 'To' is not known on line 1 in source list /etc/apt/sources.list**



should it say that?

---

### Post by s_x_g_t on 2006-12-25
also 


nathan@the-machine:~$ wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
--18:57:40--  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
           => `-'
Resolving packages.freecontrib.org... 88.191.33.6
Connecting to packages.freecontrib.org|88.191.33.6|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:57:41 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.

---

### Post by taurus on 2006-12-25
There is something wrong with the first line in your /etc/apt/sources.list.  Therefore, you need to correct that or if you don't know how, just paste your /etc/apt/sources.list here then...

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by s_x_g_t on 2006-12-25
nathan@the-machine:~$ sudo apt-sourse.list
sudo: apt-sourse.list: command not found
nathan@the-machine:~$ cat /etc/apt/sources.list
To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code)
e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
# deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
# deb [http://beryl.limitless.lupine.me.uk](http://beryl.limitless.lupine.me.uk) edgy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by bruenig on 2006-12-25
> **s_x_g_t said:**
> nathan@the-machine:~$ sudo apt-sourse.list
sudo: apt-sourse.list: command not found
nathan@the-machine:~$ cat /etc/apt/sources.list
To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code)
e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
# deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
# deb [http://beryl.limitless.lupine.me.uk](http://beryl.limitless.lupine.me.uk) edgy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

You need to put # in front of the first two lines to comment them out. Do

```
# To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code)
# e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
```

To edit this, do
```
gksudo gedit /etc/apt/sources.list
```
add the #'s and then save.

---

### Post by spockrock on 2006-12-25
open terminal and do this, 
```
gksudo gedit /etc/apt/sources.list
```

and add #'s to at the beginning of lines that do not start with deb.

kinda like what I did here.

#To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country #code)
#e.g.
#deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
# deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
# deb [http://beryl.limitless.lupine.me.uk](http://beryl.limitless.lupine.me.uk) edgy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by s_x_g_t on 2006-12-25
well that fixed it , thank you very very much and sorry for being a noob sauce.

---

### Post by spockrock on 2006-12-25
no problems,

---

