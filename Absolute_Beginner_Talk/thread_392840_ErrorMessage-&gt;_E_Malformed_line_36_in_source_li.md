---
title: "ErrorMessage-&gt; E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by SaddaGocaraRupa on 2007-03-25
Hello Ubunto World,

first post..woohoo!:KS  i finally managed to break something. i came home drunk yesterday and decided it was time to install a bunch of stuff i didn't need, inc. beryl (never a good idea, i know). when i tried to run a simple update today i got the following error message:

gg@gg-laptop:~$ sudo aptitude install opera
E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

this is what my sources list says (i think): found in /etc/apt/sources.list/sources.list_backup


deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

any ideas??

---

### Post by taurus on 2007-03-25
Can you post your /etc/apt/sources.list instead of the backup one.

```
cat /etc/apt/sources.list
```

---

### Post by SaddaGocaraRupa on 2007-03-25
sure, i just didn't know that cat command. very handy. *makes a mental note* here you go


gg@gg-laptop:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy (latest: beryl 0.1.1)

better?

---

### Post by taurus on 2007-03-25
The last two lines look a little off to me.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and command out the last two lines by placing # in front of them.

```
#deb http://gandalfn.club.fr/ubuntu edgy
#deb http://www.beerorkid.com/compiz edgy main-edgy (latest: beryl 0.1.1)
```
Save the changes.  Then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by endlessurf on 2007-03-25
I believe the second to last line should be replaced with this:
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev
or 
just add dev to the end
if i counted right that was line 36 and someone else correct me if i'm wrong.

---

### Post by SaddaGocaraRupa on 2007-03-25
looks like that fixed it! thanks a lot! 

only strange thing was that i got this message when i did the gedit

gg@gg-laptop:~$ gksudo gedit /etc/apt/sources.list
(gedit:9031): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

should i worry?

---

### Post by jenhsun on 2007-03-25
Cool, man. I believe you're drunk, indeed.

Anyway, I think the last line (36) in your sources.list might be your problem.
Try to clean the (....) in the end of the line. Save it, then apt-get update.
I guess you will be fine.

---

### Post by taurus on 2007-03-25
> **SaddaGocaraRupa said:**
> looks like that fixed it! thanks a lot! 

only strange thing was that i got this message when i did the gedit

gg@gg-laptop:~$ gksudo gedit /etc/apt/sources.list
(gedit:9031): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

should i worry?

That's just a warning so don't worry too much about it.

---

### Post by SaddaGocaraRupa on 2007-03-25
> **jenhsun said:**
> Cool, man. I believe you're drunk, indeed.

Anyway, I think the last line (36) in your sources.list might be your problem.
Try to clean the (....) in the end of the line. Save it, then apt-get update.
I guess you will be fine.

i'm not drunk anymore..now just hungover :) 

taurus' instructions worked like a charm. i just installed all the updates and the mplayer-firefox plugin and all is sweet.  

:guitar: 

thank you!

---

