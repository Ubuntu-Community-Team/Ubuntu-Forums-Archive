---
title: "Cannot use Package Manager"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Dav657 on 2008-02-01
I keep getting this error

A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: Error: Opening the cache (E:Type '--17:44:32--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq, E:The list of soucres could not be read) ' 
 
I have no clue what this means as i am completely new to linux/ubuntu. I have searced but found nothing useful. Help Please

---

### Post by wolfen69 on 2008-02-01
open terminal, and type
```
cat /etc/apt/sources.list
```
copy and paste the output here.

---

### Post by Dav657 on 2008-02-01
```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

deb http://us.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-security main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-security universe

deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```

---

### Post by taurus on 2008-02-01
You need to edit /etc/apt/sources.list.d/winehq.list 

```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```
and place a # in front of all the lines to comment them out.

Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Dav657 on 2008-02-01
Thank you it finally worked. Now I can upgrade to 7.10 Thank you very much!

---

