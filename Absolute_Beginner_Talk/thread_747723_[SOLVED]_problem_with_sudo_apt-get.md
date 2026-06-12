---
title: "[SOLVED] problem with sudo apt-get"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by chechojp on 2008-04-06
I am absolutely new to linux and/or ubuntu and quite frankly i have been doing fine till now, with all the info available in the forums (thanks for that). However when i tried to install a bibliographic database base manager (bibus) i just couldn't get the update to work. I have messed a little bit with the source.list file with other sources (such as thr R system) and the update didn' work either. I am using ubuntu 6.06 and i am planning to upgrade when the new lts release appears. but till then i need to know what i am doing wrong and why i cant get the packages i want

Here is the error i find when udating:

sergio@sergio-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

I hope you can help me. thanks

just in case, the source.list is as follows:

deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

---

### Post by wormser on 2008-04-06
Try using sudo.  [More on sudo and gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo").

```
sudo apt-get update
```

---

### Post by bsharp on 2008-04-06
you need to run the command with root permissions
```
sudo apt-get update
```

---

### Post by kerry_s on 2008-04-06
also there is a gui "synaptic" which is great if your just starting out.
look for it in your menu's.

---

### Post by chechojp on 2008-04-07
thank you very much guys. this specific problem was solved. i will post other threads with the ones i still cannot solve

---

