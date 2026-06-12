---
title: "Who won't some apps install through the terminal?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by sub1 on 2006-12-11
[IMG]http://www.hot.ee/sub1/shot.png[/IMG]
[LIST]
[*]I have tried to install several applications through the terminal but i have had success with only few. What could the cause be?
[/LIST]
[LIST]
[*]I have both Ubuntu 6.10 and WinXP on the same harddrive but on different partitions. When i boot up into Ubuntu, it doesn't reckognise my internet connection. I only have access to internet if i boot into XP first, and then restart to boot into ubuntu.
[/LIST]

---

### Post by igknighted on 2006-12-11
My guess is that you do not have the repositories installed to install that software... could you post your /etc/apt/sources.list file?

---

### Post by Kobalt on 2006-12-11
Hello,
Here is where you will learn how to install, remove and update your applications : [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html) you will find what repos you should add and how to do this...
Concerning your internet connection : what kind of connection is it (ethernet, wifi, xDSL, etc.) ?

---

### Post by sub1 on 2006-12-11
[My sources.list]("http://www.hot.ee/sub1/sources.list")

I have an ADSL connection. When i boot into ubuntu it seems like it doesn't reckognise my networking card - When i plug the cable into the networking card the usual yellow light doesn't start to blink as it normally does on XP.

---

### Post by igknighted on 2006-12-11
```
deb http://ee.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ee.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ee.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ee.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ee.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ee.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ee.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

^^try using this, I removed some of the comments (#) that were blocking the scanning of some servers.  Make your sources.lisy look like this (you need to use sudo, as in "sudo gedit /etc/apt/sources.list" in order to edit it).  Then run this command and post the result:
```
sudo apt-get update
```

---

