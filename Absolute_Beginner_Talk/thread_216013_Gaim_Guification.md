---
title: "Gaim Guification"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by jadedknight on 2006-07-14
I am looking into linux a lot these days and would probably totally switch over if it wasnt for gaming. But one thing I cannot live without is MSN. So I got Gaim and I love it. The only thing I HATE about it is that when a contac signs on my MSN list there is no popup notification. SO I researched a  little bi and found guifications for Gaim. So I downloaded the souce and Installed the GCC through the package manager so I could compile the source in terminal. Everything goes fine until I get this error.

> 
checking for GAIM... configure: error: Package requirements (gaim) were not met:
No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Now I read the INSTALL readme when I got it and it says to change the configure script to point where I installed Gaim. But Gaim was already installed with Ubuntu. It says find "gaim.pc" but no matter how much I search I cant find it. So can someone please!!! help me install Guifications for Gaim. THANK YOU :D

---

### Post by bollix47 on 2006-07-14
Gaim Guifications is in the synaptic package manager.  Just start up synaptic and search for gaim.

---

### Post by jadedknight on 2006-07-14
I searched for Gaim and did not find it.

---

### Post by scxtt on 2006-07-14
do you have the universe repo enabled?, i see guifications ...

---

### Post by jadedknight on 2006-07-14
How do I enable the universal repositories?

---

### Post by scxtt on 2006-07-14
here's my /etc/apt/sources.list```
:> cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

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
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.canonical.com/ubuntu dapper-commercial main
```if you replace yours w/ it - you'll see what i see ...

---

### Post by jadedknight on 2006-07-14
I still do not see it...its not there :(

---

### Post by scxtt on 2006-07-14
don't know what to tell you, i can see it w/ my sources.list -- i'd provide a screenshot of it in synaptic, but that won't help ... did you refresh synaptic after changing sources.list (the Reload  button on the left)?

---

### Post by jadedknight on 2006-07-14
Yes I did. I will do it again. Please provide a screen anyways.

Edit: After pushing refresh like ten times it now works. THANK YOU VERY MUCH :D :KS

---

### Post by scxtt on 2006-07-14
that's strange it gave you a hard time like that ... but at least it's working now :D

---

