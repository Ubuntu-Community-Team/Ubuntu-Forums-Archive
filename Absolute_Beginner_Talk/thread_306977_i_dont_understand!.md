---
title: "i dont understand!"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2006-11-25
i dont understand the whole thing with universes and what not??!!?!?!!?!?! can some one enlighten me on what that is ?:confused:

---

### Post by scxtt on 2006-11-25
it's a way to divide the repositories ubuntu uses to install software:

:> cat /etc/apt/sources.list
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

[color=blue]## Uncomment the following two lines to add software from the **'universe'**
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.[/color]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper **universe**
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper **universe**
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted **universe** multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted **universe** multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security **universe**
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security **universe**

---

### Post by junglepeanut on 2006-11-25
These are like adresses. It tells your computer where to look for programs the best way would be tool look at this file instead of using synaptic.

/etc/apt/sources.list

It explains what to do to make your computer look everywhere.
If you want to make chanes with it make sure to open root

---

### Post by junglepeanut on 2006-11-25
Also read
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by kvonb on 2006-11-25
Software is organised into categories and is available only from certain "repositories".

Repository just means servers, or places that hold the software.

The "restricted" repo holds software that is not "free" or "opensource", which usually means that it is written by a commercial entity ie ATI video drivers, flash player etc'.  This is not part of the standard Ubuntu repo because it goes against the opensource values and mindset of Ubuntu.

When you add a repository to synaptic, it allows you to download and install this software.

Hope that makes sense :)

---

