---
title: "update manager"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-02-01
Ok, I had to format my computer AGAIN, cuz I was an idiot trying to install xgl and compiz (which failed). When I opened my update manager in ubuntu 6.06, it said there are no new updates, which is impossible. Then I tried "sudo apt-get update", and it only said "done".
What the hell is wrong,and how can I fix it??

Thanks To All

---

### Post by Paerez on 2007-02-01
Maybe you dont have any repositories.

Post your /etc/apt/sources.list

---

### Post by ayed on 2007-02-01
Here is my sources.list, thanks anyways for replying!


# Line commented out by installer because it failed to verify:
#deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by psyne on 2007-02-01
All your repositories are commented out

```
#deb http://jo.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://jo.archive.ubuntu.com/ubuntu/ dapper main restricted
```

---

### Post by Paerez on 2007-02-01
As I though, your computer doesn't know about any updates!

See all the "#Line Commented out by installer because it failed to verify" lines?
Remove the # in front of the line right below each of those lines. Then try to update.

---

### Post by glabouni on 2007-02-01
could be that jordanians repositories are down that led the installer to comment these.
or maybe there was something wrong with your internet connection.

-edit-
I just checked, [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) is up and running.
maybe a temporary routing problem.

---

