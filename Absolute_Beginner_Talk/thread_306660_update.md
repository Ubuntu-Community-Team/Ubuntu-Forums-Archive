---
title: "update"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by trachycarpus on 2006-11-25
I went to run the automatic update and I get Software index is broken, run sudo apt-get install -f. When I do I get:-
 
peter@peter-desktop:~$ sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
peter@peter-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
peter@peter-desktop:~$
Now what do I do please.
Peter

---

### Post by taurus on 2006-11-25
Probably need to see your repos...

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by trachycarpus on 2006-11-25
Is this what you want??
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END
I think its the java trying to update, I get as far as the T&C page, scroll down and cannot go any further
Hope this is enough information
Peter

---

### Post by deadgobby on 2006-11-25
> **trachycarpus said:**
> I went to run the automatic update and I get Software index is broken, run sudo apt-get install -f. When I do I get:-
 
peter@peter-desktop:~$ sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
peter@peter-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
peter@peter-desktop:~$
Now what do I do please.
Peter

[COLOR="Red"]"peter@peter-desktop:~$ dpkg --configure -a"[/COLOR]
Try ( sudo dpkg --configure -a )

---

### Post by trachycarpus on 2006-11-25
That did it, I think, Thanks very much
Peter

---

