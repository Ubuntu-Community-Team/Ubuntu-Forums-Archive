---
title: "software sources change causes add/remove software problem"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by commander_dave on 2006-12-15
I'm learning how to install and uninstall new software. I have edited my sources list about a month ago and have had no problems with updates, etc... I was viewing system > administration > software sources and accidentally changed the source code dash to a check mark (in the ubuntu 6.10 tab) and I save the change. Everytime I try to run add/remove programs I get this error. 

**Failed to check for installed and available applications **
This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

If I run SPM I get the following error msg,

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

My sources.list has not been a problem until I made the change in software sources. My sources.list follows just in case it's needed.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
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
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dappper multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse

Thanks for your help,

David

---

### Post by an.echte.trilingue on 2006-12-15
The problem probably is not in  /etc/apt/sources.list.  It is in /etc/apt/sources.list.d/edgy-multiverse.list.  Would you mind posting that one for us?

---

### Post by commander_dave on 2006-12-15
These are the lines from */etc/apt/sources.list.d/edgy-multiverse.list*

# automatically added by gnome-app-install on 2006-11-06 06:49:39.892597
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse

---

### Post by Kobalt on 2006-12-15
Hello,

Try running this command and tell us what happens next : 
```
sudo aptitude update -f
```

---

### Post by commander_dave on 2006-12-15
I ran the command and got the following....

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.

---

### Post by an.echte.trilingue on 2006-12-16
> **commander_dave said:**
> These are the lines from */etc/apt/sources.list.d/edgy-multiverse.list*

# automatically added by gnome-app-install on 2006-11-06 06:49:39.892597
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse

You have an extra dash in the security line.

It should look like this:
```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy security multiverse
```

Please note that I took out the dash between edgy and security.

Take care
-mat.

EDIT!  NO I WAS WRONG!  Leave the security line like it was.  You have to add "multiverse" to the end of the line above security, like this:
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy multiverse
```
 Sorry.

---

### Post by commander_dave on 2006-12-19
I added that one simple word and bingo, it works. Thanks for your help. Next time I play with a tool I'm not familiar I'll try to remember to use a little caution.

---

