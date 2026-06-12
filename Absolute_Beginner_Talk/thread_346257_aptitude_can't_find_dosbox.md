---
title: "aptitude can't find dosbox"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by PaperPilot on 2007-01-25
Hey All;

I tried installing dosbox using the root command line:

aptitude install dosbox

The messages I got indicated aptitude couldn't find dosbox.

I am running Ubunto 6.06 and using pppd with a dial-up connection.

What am I doing wrong?

Thanks in advance.

---

### Post by Lord Illidan on 2007-01-25
Can you give us your /etc/apt/sources.list please?

---

### Post by lamego on 2007-01-25
Have you enabled the extra repositories ?
Read about it here:
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by PaperPilot on 2007-01-25
> **Lord Illidan said:**
> Can you give us your /etc/apt/sources.list please?

It looks like this:
```


deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Does it help?

---

### Post by sumguy231 on 2007-01-25
See the lines which end in 'universe'? Remove the # in front of them, and then run sudo apt-get update. Then you should be able to get dosbox.

---

