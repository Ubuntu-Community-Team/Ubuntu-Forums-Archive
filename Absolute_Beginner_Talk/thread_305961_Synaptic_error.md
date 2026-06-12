---
title: "Synaptic error"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by ajpkboy on 2006-11-24
I've seen a lot of people that have had similar problems in synaptic package manager. I have experienced an error like many others in similar threads. The error is 

' Error: Opening the cache (E:Type '-' is not known on line 35 in source list /etc/apt/sources.list, E:The list of sources could not be read.)'

I typed in the code "sudo gedit /etc/apt/sources.list" in terminal to view my source list but I'm not sure where the error is or what to do. Can someone point it out. Heres my sources.list

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


- i686:

I'll check back later for any replies or I can be emailed at [email]asim10101@hotmail.com[/email]

---

### Post by rlozano on 2006-11-24
is that -i686: included in your sources.list? if that is, you may want to take that out or comment (#) it to solve your problem.

---

### Post by kenweill on 2006-11-24
The "-686" line should be removed.
Thats the problem.
Theres no "-" command. Synaptic cant read it.

---

