---
title: "Can't update"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by dummyhead3 on 2007-12-16
Hi!
I'm pretty new to Ubuntu, I am having a problem updating some packages related to compiz. the udate manager won't let me check the box. I attached a screenshot.

[IMG]http://www.hamstermadness.com/mainsite/pics/Screenshot.png[/IMG]

---

### Post by PmDematagoda on 2007-12-16
Could you post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by lamalex on 2007-12-16
You probably just need to hit "check" again. Try doing it from the command line
```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by ayumi_alive on 2007-12-16
I have the same problem as well. My Ubuntu is behind the company proxy therefore it requires proper authentication. I do not have any problem surfing the net, but stuck at the update. Can any help me?

I had tested to put the http_proxy and http_ftp as well as the server.cfg to add in the NT_domain, user, password.

What else I can do to make the update works? :confused:

---

### Post by dummyhead3 on 2007-12-16
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy main restricted multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-updates main restricted multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-security main restricted multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-security main restricted
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-security universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) gutsy-security universe
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
# deb [http://apt.wicd.net](http://apt.wicd.net) gusty extras
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy



This is it. I got compiz fusion back on fiestey from the tuxfamily site (last one). They don't have a gusty repo...

---

### Post by dummyhead3 on 2007-12-17
Fixed it, I removed the tuxfamily repo and reinstalled compiz with ubuntu's repos, works perfecto!!
:)!

---

### Post by kj7lo on 2007-12-17
> **Iamalex said:**
> You probably just need to hit "check" again. Try doing it from the command line
```

sudo aptitude update
sudo aptitude upgrade

```

I am trying to upgrade from 7.04 to 7.10 and the message to update to 7.10 does not appear.  I tried it from the menu and also the command line below.

I want to upgrade rather than new install.

---

### Post by PmDematagoda on 2007-12-17
Could you please post your result of:-

```
cat /etc/apt/sources.list
```

---

