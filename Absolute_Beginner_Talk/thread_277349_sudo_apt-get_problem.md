---
title: "sudo apt-get problem"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by unrealmstr on 2006-10-14
when i type ```
sudo apt-get update
``` into the terminal i get this: "E: the method driver /usr/lib/apt/methods/htp could not be found." is there a way to fix this?

---

### Post by Kateikyoushi on 2006-10-14
Might be a typo in your sources list.

Post the output of this command

```
cat /etc/apt/sources.list
```

---

### Post by unrealmstr on 2006-10-14
```
ryan@unrealmstr:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb htp://www.beerorkid.com/automatix/apt dapper main
ryan@unrealmstr:~$

```

---

### Post by Kateikyoushi on 2006-10-14
Change the last line there is a typo in it, should be http not htp.

```
gksudo gedit /etc/apt/sources.list
```

```
deb http://www.beerorkid.com/automatix/apt dapper main
```

---

### Post by unrealmstr on 2006-10-14
thanks its fixed guess i need to be more careful:p

---

### Post by Kateikyoushi on 2006-10-14
Creating a backup before editing the config files is also a good idea.

---

