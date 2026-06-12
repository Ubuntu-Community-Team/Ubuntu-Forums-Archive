---
title: "E: Malformed line 23 in source list /etc/apt/sources.list (dist parse) [Resolved]"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by mikewhatever on 2007-01-15
After a reboot I got an error message :
E: Malformed line 23 in source list /etc/apt/sources.list (dist parse)
Here is the sources.list:
# 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main #Added by software-properties


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security

This is the content of /etc/apt directory

/etc/apt$ ls
apt.conf     secring.gpg    sources.list~    sources.list.save   trusted.gpg
apt.conf.d   sources.list   sources.list.d   trustdb.gpg         trusted.gpg~

What is sources.list.d?

Needless to say that I have not edited the list.

---

### Post by mikewhatever on 2007-01-15
The following is a quote from heere [http://ubuntuforums.org/showthread.php?t=334416&highlight=malformed+line+23](http://ubuntuforums.org/showthread.php?t=334416&highlight=malformed+line+23)
```
I solved it helped by Taurus, so I am posting it if someone has a similar problem
this is what I did I remove the source.list.d, I still do not know how it was created but it worked

Terminal

sudo rm /etc/apt/sources.list.d/*
(hit y for each question...)
sudo aptitude update
sudo aptitude upgrade
```

can anyone confirm?

---

### Post by mikewhatever on 2007-01-15
Hmm..., it looks like this is not an infrequent problem, but what can be the solution? :-k

---

### Post by STREETURCHINE on 2007-01-15
hash out this line and try again

            ```
deb http://us.archive.ubuntu.com/ubuntu/ edgy
```

---

### Post by aysiu on 2007-01-15
Actually, you can just delete that line altogether. It serves no purpose.

---

### Post by mikewhatever on 2007-01-15
Thanks for trying. If possible, what was wrong with that line?

```
~$ sudo aptitude update
Password:
E: Malformed line 40 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 40 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

As you can see, another error poped up.:-D

---

### Post by aysiu on 2007-01-15
Save yourself the trouble of putting out these little fires and just [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources).

When you're following those instructions, make sure you paste **over** your old sources.list. Don't add to it. Replace it.

---

### Post by mikewhatever on 2007-01-15
> **aysiu said:**
> Save yourself the trouble of putting out these little fires and just [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources).

When you're following those instructions, make sure you paste **over** your old sources.list. Don't add to it. Replace it.

Tried that from sources.list.save before posting here. I don't think the new list was any different thou.

---

### Post by STREETURCHINE on 2007-01-15
hash or delete this line

                              ```
deb http://security.ubuntu.com/ubuntu edgy-security

```

---

### Post by STREETURCHINE on 2007-01-15
> **mikewhatever said:**
> Thanks for trying. If possible, what was wrong with that line?

```
~$ sudo aptitude update
Password:
E: Malformed line 40 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 40 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

As you can see, another error poped up.:-D

the lines are incomplete,that is all,

---

### Post by mikewhatever on 2007-01-15
All is well after following Aysiu's suggestion. Thanks alot.

STREETURCHINE, your right, that line was definitely incomplete. Thanks for help.

---

