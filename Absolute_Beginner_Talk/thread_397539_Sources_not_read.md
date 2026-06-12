---
title: "Sources not read"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-30
when I try to open syaptic or just do an update either through the notification on the toolbar OR by apt-get update, I get an errorbox that says E: Type '--06:44:03--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.



how do I fix this? I get that error every time I try to do ANYTHING

---

### Post by Maestro23 on 2007-03-30
In a terminal type:

> cat /etc/apt/sources.list

Copy/Paste the output here.

---

### Post by maccawolf on 2007-03-30
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main universe

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by haricharan on 2007-03-30
could you post contents of /etc/apt/sources.list.d/winehq.list too
```
cat /etc/apt/sources.list.d/winehq.list
```

---

### Post by taurus on 2007-03-30
Can you post this?  It looks a little odd of having that file in /etc/apt/sources.list.d.

```
cat /etc/apt/sources.list.d/winehq.list
```

---

### Post by maccawolf on 2007-03-30
--06:44:03--  [http://wine.budgetdedicated.com/apt/sources.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.d/edgy.list)
           => `edgy.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
06:44:04 ERROR 404: Not Found.


Looks liek that's where I have errors, but I have No clue as to what it means, or what to do to fix it....

---

### Post by maccawolf on 2007-03-30
was reading lots of stuff trying to figure out what to do and I stumbled upon manually updating. I tried that and it seems to have fixed the problem. Still don't know WHY it happened, but at least now I'm not stuck.

Thanks all for your help!

---

