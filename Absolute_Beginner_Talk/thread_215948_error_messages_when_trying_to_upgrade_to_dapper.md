---
title: "error messages when trying to upgrade to dapper"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-07-14
So I have tried to use update manager to upgrade from breezy to dapper, but keep encountering the same failure messages, namely:

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg) Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)


Any ideas?

---

### Post by bruce89 on 2006-07-14
> **oscar78 said:**
> So I have tried to use update manager to upgrade from breezy to dapper, but keep encountering the same failure messages, namely:

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg) Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)


Any ideas?

I cannot access these files here either, so you will have to remove the PLF repositories from the list.

---

### Post by Jagot on 2006-07-14
Those appear to be external repositories installed by EasyUbuntu or something.  Check out your /etc/apt/sources.list and remove them.

---

### Post by oscar78 on 2006-07-14
I'm sorry, im quite new at linux.  could you tell me how to remove the plf repositories?

---

### Post by Jagot on 2006-07-14
Hit Alt+F2 or from Terminal type:

```
sudo gedit /etc/apt/sources.list
```

A file should now open in Gedit, the text editor, which looks something like this:

> #
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Delete any lines referring to those repositories - so they should have packages.freecontrib.org in them.  Save the text file and those, then update.

---

### Post by bruce89 on 2006-07-14
> **oscar78 said:**
> I'm sorry, im quite new at linux.  could you tell me how to remove the plf repositories?

Assuming Gnome, System>Administration>Software Properties
There will be a list there, and remove the PLF repositories from it. (they lines will have *packages.freecontrib.org* in it)

---

### Post by oscar78 on 2006-07-14
the gedit file i opened seems to be a read only file and so I cannot delete any lines.  perhaps i dont understand...

---

### Post by bruce89 on 2006-07-14
> **oscar78 said:**
> the gedit file i opened seems to be a read only file and so I cannot delete any lines.  perhaps i dont understand...

You need to open gedit as root, did you type ```
gksudo gedit /etc/apt/sources.list
``` in the terminal?

---

### Post by oscar78 on 2006-07-14
that seemed to work.  thanks guys!

---

### Post by bruce89 on 2006-07-14
> **oscar78 said:**
> that seemed to work.  thanks guys!

No problem.

---

### Post by Jagot on 2006-07-14
> **oscar78 said:**
> the gedit file i opened seems to be a read only file and so I cannot delete any lines.  perhaps i dont understand...

Oops - that was due to a typo in my post which I have corrected.  sudo or gksudo will work.

---

