---
title: "apt not working"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by zach12 on 2007-09-15
Hi i feel like a noob here but some how i messeed up apt when i added the wine reps
and now add or remove programs, apt-get don't work

I've had this happen before and have fix it by removeing what ever rep i had added
But now that not working 

here's my /etc/apt/sources.list it  looks ok to me
> 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main


dapper.list -O /etc/apt/sources.list.d/winehq.list



 
thanks

---

### Post by Maestro23 on 2007-09-15
Why is that one dapper security universe entry commented out?

Also, why is there a Feisty entry in there if you are running dapper?

---

### Post by Majorix on 2007-09-15
The very last line shouldn't have been there. You followed the instructions in an incorrect way.

---

### Post by zach12 on 2007-09-15
The feisty rep is for ubuntu sudio and will work dapper
any way that has been ther for weeks and i have apt-get a ton of things so thats not it
thanks

---

### Post by zach12 on 2007-09-15
Thanks:oops::oops:

---

### Post by Majorix on 2007-09-15
Wait you fixed it? Would be kind of you to tell how you did it :)

---

### Post by diatribe on 2007-09-15
> **Majorix said:**
> Wait you fixed it? Would be kind of you to tell how you did it :)

removing the last line ;p

---

### Post by Maestro23 on 2007-09-15
> **diatribe said:**
> removing the last line ;p

Good deal.  Can you edit your 1st-post and mark this thread SOLVED.

---

