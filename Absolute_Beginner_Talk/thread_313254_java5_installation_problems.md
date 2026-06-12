---
title: "java5 installation problems"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by nitro_n2o on 2006-12-05
Hi all, 
i've been trying everything in this world to install java 5 but i couldn't.. i've tried sudo apt-get install sun-java5-jdk but no package exists i've also tried manual install using the rpm package i'v installed it using alien but it doesn't appear in the update-altrnatives --config java 

you can assume that i did nothing to install it. How to install it? 

pls help

---

### Post by kakalaky on 2006-12-05
Do you have the multiverse repo enabled?  If you don't know how to check this just post the ouput of the following here.

```
cat /etc/apt/sources.list
```

---

### Post by nitro_n2o on 2006-12-05
```

deb http://qa.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://qa.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://qa.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://qa.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://qa.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://qa.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://qa.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univer se multiverse
deb-src http://qa.archive.ubuntu.com/ubuntu/ dapper-backports main restricted un iverse multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by nitro_n2o on 2006-12-05
is the file ok.. i think its enabled?? but i still dont know why i can't find the package java-package is also unavailable

---

### Post by Sef on 2006-12-05
Java is in [multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu"), which needs to be added.

---

### Post by kakalaky on 2006-12-05
add these 2 lines to it:

```
deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
```

---

### Post by nitro_n2o on 2006-12-05
thx all that's sooooo cooool it's downloading now
i looooove ubuntu :)

---

