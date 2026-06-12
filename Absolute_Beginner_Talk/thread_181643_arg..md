---
title: "arg."
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-24
I was trying to add the wine repository in dapper but it kept erroring and messed up my whole synaptic. then i accidently deleted one of the regular needed repositories... is there any way to recover them, like set them to default again?

and as a second part to this.... how can i get wine/cedega working in dapper drake the guides didnt really work for me

thanks

---

### Post by richbarna on 2006-05-24
Firstly, wine is available already in the dapper repository, I just downloaded it.
Secondly, Here is my source list :-
> 
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



Do this :-
Open your terminal/console and type :-
> sudo gedit /etc/apt/sources.list
Delete everything, and copy and paste mine into it.

That will sort you out
Good Luck ;)

---

### Post by sotonin on 2006-05-24
thanks, ur a life saver :)

---

### Post by richbarna on 2006-05-24
No Biggie :)

---

