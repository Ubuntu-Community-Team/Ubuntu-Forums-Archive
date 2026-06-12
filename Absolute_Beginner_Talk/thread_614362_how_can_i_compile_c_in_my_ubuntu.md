---
title: "how can i compile c in my ubuntu"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by kokophone on 2007-11-15
Dear sir or madam,
I am new user of ubuntu and i unable to compile C in my comouter..My ubuntu is 6.06 and if i run this command
...[B][SIZE="4"]sudo apt-get install build-essential
 build-essential: Depends: libc6-dev but it is not going to be installedor
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages[/SIZE][/B]

please pay me advise for me....
best regards
blazer

---

### Post by taurus on 2007-11-15
Can you post your /etc/apt/sources.list (and stop the large and bold font, okay)?

```
cat /etc/apt/sources.list
```

---

### Post by kokophone on 2007-11-15
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

that is my ..cat /etc/apt/sources.list

---

### Post by taurus on 2007-11-15
> **kokophone said:**
> **[COLOR="Blue"]deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted[/COLOR]**
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

that is my ..cat /etc/apt/sources.list

If you are running Dapper, how come you have an entry for Feisty?  It's not a good idea to mix repos in /etc/apt/sources.list.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom for feisty.  Then, remove the # in front of all the lines that start with **deb** and **deb-src**.

Save it and run

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by AkGw on 2007-11-15
try:

apt-get install gcc libc6-dev

---

### Post by kokophone on 2007-11-16
Dear all
Now i can compile...c
but i can't output of it.....
there is no a.out...???when i type a.out...
sh: a.out: command not found
pls why is that???

---

### Post by KentS on 2007-11-16
Exactly what do you type to compile your program?

To be able to run a program, you need to check that it's executable.
To run it, type
```
./a.out
```
if your in the same directory as a.out.

---

### Post by kokophone on 2007-11-16
hello it is not running with 
a.out???
./a.out
it is ok....and it is running
amazing!!!
I wanna know about  running with a.out or other ways...
please

---

### Post by KentS on 2007-11-16
To run just using
```
a.out
```
you must either place your directory in your PATH variable, or place a.out in a directory that's already in your PATH variable, e.g. /bin /usr/bin /usr/local/bin, or similar.

---

### Post by kokophone on 2007-11-16
thank u so much for my question guy..:guitar:

---

