---
title: "total newbie problem with line 34"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-01-09
I am getting this every time I try to do anything.   How do I fix this?


E: Type '“deb' is not known on line 34 in source list /etc/apt/sources.list


Thanks
Noah

---

### Post by STREETURCHINE on 2007-01-09
can you post the out put from 

[HTML]gksudo gedit /etc/apt/sources.list [/HTML]

---

### Post by nynoah on 2007-01-09
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by nynoah on 2007-01-09
That is what I get when I tried your code.
Noah

---

### Post by nynoah on 2007-01-09
(gedit:5862): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by STREETURCHINE on 2007-01-09
remove the ones with

             [HTML]“deb http://www.getautomatix.com/apt edgy main”
“deb http://www.getautomatix.com/apt edgy main”
[/HTML]

and leave the last one

---

### Post by kj1h234lkj1234 on 2007-01-09
Replace /etc/apt/sources.list with this:

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://www.getautomatix.com/apt edgy main
```

You had a few duplicated lines.

---

### Post by STREETURCHINE on 2007-01-09
> **nynoah said:**
> (gedit:5862): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

yep dont worry about that we all get that it is a bug ,not dangerous

---

### Post by deadgobby on 2007-01-09
> **nynoah said:**
> (gedit:5862): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Delete 2 of these
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
Mainly the top two.
 So go back into 
gksudo gedit /etc/apt/sources.list
 You only need one line. If you want you can add ## before each
 “deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
It will tell Linux to ignore the line.
GObby

---

### Post by nynoah on 2007-01-09
I think I have it fixed.  I have no clue how though.  I tried a combination of what you all sugested and another thing to reconfigure and install updates.  I think I am OK now, but I wait and see.  

Thanks guys

---

### Post by nynoah on 2007-01-09
Ok maybe it is not fixed.......

I get  this now


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by STREETURCHINE on 2007-01-09
what was the error message

---

### Post by nynoah on 2007-01-09
Well wait.  I think I am OK now.  I got automatix to start now.  

How do I get Automatix (the other version with Beta Files)

I am trying to get the right drivers now for my computer

Thanks you guys are great

---

### Post by deadgobby on 2007-01-09
As some on said.. It is a bug and the rest of your repos list look fine and dandy. 
Gobby

---

### Post by deadgobby on 2007-01-09
What drivers?

---

### Post by nynoah on 2007-01-09
I just got a new computer and loaded Ubuntu onto it.  I had Ubuntu loaded onto it before, but had a problem getting the internet to work when I moved the computer from NY to Colo.  So I reloaded it.  Now I am trying to reinstall everything with out the help of my father.  He helped me before.  I am trying to break from windows and go to Ubuntu.

N

---

### Post by STREETURCHINE on 2007-01-09
automatix is having a few minor problems with there hosts ,relax arnieboy is on the job,it seems to be fine here in australia always works when i want it:D

---

### Post by deadgobby on 2007-01-09
Are you in school? What is your ISP? How are you connecting to the internet?

---

### Post by nynoah on 2007-01-09
Not is school.  Well actually I start in a few days.  I have comcast at home.
N

---

### Post by nynoah on 2007-01-09
OK I got the Nvidia driver download going now.  

How do I get the other version of automatix?  The one that has the Beta versions on it?

---

### Post by STREETURCHINE on 2007-01-09
> **nynoah said:**
> I just got a new computer and loaded Ubuntu onto it.  I had Ubuntu loaded onto it before, but had a problem getting the internet to work when I moved the computer from NY to Colo.  So I reloaded it.  Now I am trying to reinstall everything with out the help of my father.  He helped me before.  I am trying to break from windows and go to Ubuntu.

N

welcome to ubuntu hope you enjoy you'r stay ,we have a great community here,very helpfull.  8)

---

### Post by nynoah on 2007-01-09
Ok I got the automatix bleeder to work now too
N

---

### Post by STREETURCHINE on 2007-01-09
good luck..

---

### Post by nynoah on 2007-01-09
Thanks again for taking your time to help me.  I am off to down load all the stuff that I need again.

N

---

