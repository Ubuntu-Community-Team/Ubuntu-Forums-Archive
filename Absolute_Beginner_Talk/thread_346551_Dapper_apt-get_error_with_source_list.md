---
title: "Dapper apt-get error with source list"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by VladTheImpaler on 2007-01-25
I've just reinstalled 6.06 Dapper after a hdd crash.  When I use apt-get I get this:

> E: Type '“deb' is not known on line 34 in source list /etc/apt/sources.list

My /etc/apt/sources.list is

> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


The last two lines are duplicates without the " ".  Can I delete the next to last line to fix this?  If not, what should I do.

Thanks in advance for the help.

---

### Post by DSn0wMan on 2007-01-25
It looks like you have some undesirable quotation marks on the second to last line.

&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;

to comment stuff out use the pound sign at the beginning of the line.

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by taurus on 2007-01-25
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
And remove the " in front and behind the second to the last line in there.

---

### Post by VladTheImpaler on 2007-01-25
If I remove the " from the second to last line, it will be identical to the last line.  Is that OK?

---

### Post by meng on 2007-01-25
Just remove the second-last line altogether. There is a leading AND a trailing " that you don't need.

---

### Post by Buck2348 on 2007-01-25
I would delete the line with " " quote marks (line 33).  I wonder how it got there.  You can back up the file first of course if you like.

Buck

EDIT:  Gee I'm slow.  Didn't know you were here tonight, Taurus.

---

### Post by taurus on 2007-01-25
> **Buck2348 said:**
> 
EDIT:  Gee I'm slow.  Didn't know you were here tonight, Taurus.

So, it's like a nightmare thing!  Better look over your shoulder...

---

### Post by VladTheImpaler on 2007-01-25
I deleted the next to last line and everything works fine.

Thanks for the help.

---

