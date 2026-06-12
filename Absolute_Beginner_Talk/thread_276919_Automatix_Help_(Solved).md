---
title: "Automatix Help (Solved)"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-10-13
hi, sorry for wasting your time, but I can't seem to get automatix to install.  I do everything right, but when i type the udate install comand it says it cannot find the package.  so I made sure the list was in my source lists, it was... and now I don't know what to do to get it to work.

---

### Post by Iarwain ben-adar on 2006-10-13
Hi,
did you try this?```
sudo apt-get update && sudo apt-get install automatix
```


Iarwain

---

### Post by familyjules74123 on 2006-10-13
i just tried the command you gave me... didnt work

---

### Post by petri on 2006-10-13
Could there be something wrong with the sources.list? Paste in terminal ```
gedit /etc/apt/sources.list
``` and then paste the result here.

---

### Post by familyjules74123 on 2006-10-13
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyunbuntu


this is my source list... I'm pretty sure its ok

---

### Post by JayTee on 2006-10-13
You need to remove the # from the second from the last line in your sources list. That's the repository for Automatix. Once you do that and save your updated sources list then run the command:
sudo apt-get update && sudo apt-get install automatix
Then it should work fine.
Your source for Automatix was commented out. All of the lines in the file that have # at the beginning are treated as comments instead of a valid repository.and it should work

---

### Post by familyjules74123 on 2006-10-13
ohhh thanks a lot that helps me understand this stuff a lot more.

---

### Post by familyjules74123 on 2006-10-13
one more question... im trying to delete the # but it wont let me save because it is read only and i dont have the permission to do it

---

### Post by PriceChild on 2006-10-13
> **familyjules74123 said:**
> one more question... im trying to delete the # but it wont let me save because it is read only and i dont have the permission to do it
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by petri on 2006-10-13
This time you have to open the file with ```
gksudo gedit /etc/apt/sources.list
```

EDIT: nr 2 again :rolleyes:  I'm going to bed now :-D

---

### Post by familyjules74123 on 2006-10-13
thanks guys... it worked

---

### Post by xpod on 2006-10-13
Even though i can follow most other install methods i still install automatix before i do much else and even got automatix2 on yet another fresh install last night.....
 
Managed to mess up installing nvidia and beryl but alls well now and automatix 2 is even better than the first one......

Enjoy all those illegal codecs....;) ...lol

---

### Post by familyjules74123 on 2006-10-13
whats in automatix 2 thats dif. from one?

---

### Post by KingBahamut on 2006-10-13
In the future please refer to A-X actual documentation at 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by jhenager on 2006-10-14
I am having no luck either.
Fetched 4B in 2s (1B/s)
Reading package lists... Done
jeff@jeff-desktop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
Package automatix is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  automatix2
E: Package automatix has no installation candidate
jeff@jeff-desktop:~$ uname -a
Linux jeff-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Edit: Fixed my own problem. See what happens when you read? Now onto the next one....

---

### Post by xpod on 2006-10-14
You`d have been as well getting 2 would you not????

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

much nicer....good luck with the next calamity regardless:mrgreen:

---

