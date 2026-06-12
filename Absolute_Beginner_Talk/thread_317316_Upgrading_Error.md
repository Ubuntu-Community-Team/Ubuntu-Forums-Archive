---
title: "Upgrading Error"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-12-12
Hei All,

Im getting an error when Im trying to update... so I ran apt-get check in terminal and heres the out put...how do I fix this?

```
jussi@jussi-laptop:~$ sudo apt-get check
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
jussi@jussi-laptop:~$ 
```

---

### Post by xyz on 2006-12-12
> E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
There seems to be a pbm at line 2.
Please post the output of your sources.list to try and identify it.

---

### Post by Kobalt on 2006-12-12
Could you please post here the content of your sources.list file ? It seems there is a problem here...

Edit: xyz was faster than me :(

---

### Post by Jussi01 on 2006-12-12
How do i do that...??

---

### Post by Kobalt on 2006-12-12
Use your file browser, go to the system files and then : /etc/apt/ the sources.list file should be there. You can open it simply with a double click (but you will only be able to read it, no writting, it's super user permission required).

---

### Post by Jussi01 on 2006-12-12
Do you want sources.list or edgy-universe.list ? the sources.list wont open, but here is the edgy-universe.list output:

```
# automatically added by gnome-app-install on 2006-11-22 08:52:56.737881
deb http://fi.archive.ubuntu.com/ubuntu/ edgy
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://fi.archive.ubuntu.com/ubuntu/ edgy-updates universe
```

---

### Post by xyz on 2006-12-12
I'm on Dapper so...
Shouldn't he/she run sudo gedit /etc/apt/sources.list.d
What's the ".d" for?
Thx.

---

### Post by Kobalt on 2006-12-12
sources.list.d is a folder... 
What we want to have an eye on is the file, "sources.list". If it doesn't open then use the command xyz gave you, removing the ".d" at the end.

---

### Post by Jussi01 on 2006-12-12
Ok, I opened it with text editor and this is what it says:

```
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://fi.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fi.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fi.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://fi.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fi.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://fi.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://easyubuntu.cafuego.net main easyubuntu

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt dapper main

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END
#Beryl
deb http://ubuntu.beryl-project.org/ edgy main
deb http://wine.budgetdedicated.com/apt edgy main
```

---

### Post by Jweaver on 2006-12-23
[COLOR="Blue"]I was having the same problem.  out of curiosity I wanted to see what would happen if I went to software sources under system, administrator and uncheck everything with a check box.  I did that, then went to the systems update, and it worked fine.  then i went back to software sources, and checked everything that _was checked before_.  now the updates and everything is working fine.  I guess that refreshed the files, and solved the error.[/COLOR]

---

