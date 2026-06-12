---
title: "Is it just me?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-03-11
I just had to do a clean install again after messing up badly with my Ubuntu install... and  it seems kinda weird but I just finished setting up all my hardware and now I'm installing my software... and when I went to install acrobat it said it couldn't find the repositories >.>.  When I did an aptitude search for acrobat I got this...


```
jeremy@ubuntu:~$ sudo aptitude search acro
i   anacron                         - a cron-like program that doesn't go by tim
p   libapache2-mod-macro            - Create macros inside apache2 config files 
p   xmacro                          - Record / Play keystrokes and mouse movemen
v   xorg-build-macros  
```

Did I mess up my sources list? I checked it and it didn't seem so...

---

### Post by yabbadabbadont on 2007-03-11
Did you make sure to enable the multiverse repository?

---

### Post by starcraft.man on 2007-03-11
Heres my sources file

```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

I even ran sudo aptitude update several times >.>

---

### Post by dhughes on 2007-03-11
Looks liek you have Universe but no Multiverse selected.

edit:

 Oops, yes you do I see it when I scroll to the right of your sources list.

---

### Post by yabbadabbadont on 2007-03-11
You only have multiverse enabled for edgy-backports.  Enable it for the others too.

---

### Post by starcraft.man on 2007-03-11
looooool *smacks self* 

my bad :P

---

