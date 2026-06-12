---
title: "Synaptic keeps timing out but 'net connection is fast"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by OOT_In_Atlanta on 2007-04-14
OK.  FIrst off I'm a TOTAL NOOBIE with Linux.  Just about everything I've done I'm looking up here and finding answers.  But this one nothing I've read seems to be working.

I'm trying to use Synaptic to include universe and multiverse (per a thread I saw here).  It connects and starts downloading but is timing out.  It starts out OK and then goes to like 203 b/s then just stops.  It's gotten to 42 of 43 parts for 2 days now.  Also, the same thing happens when I try to run Software Update (to update to linux-image-2.6.17-11-386).  It just times out.  But my connection is good (6 MB cable connection).  I have tried it during the early morning hours (3:00 am EST), mid-day, evening, night.  Same thing.

I've seen stuff about updating/editing a source list but when I try to edit that file I am told I don't have permission.

Any ideas?

Thank you in advance for any and all help/suggestions/ideas/etc.  It is greatly appreciated.

OOT_In_Atlanta

---

### Post by taurus on 2007-04-14
Try to run these two commands from a terminal and make sure you don't have synaptic or Add/Remove open.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by OOT_In_Atlanta on 2007-04-14
> **taurus said:**
> Try to run these two commands from a terminal and make sure you don't have synaptic or Add/Remove open.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```
OK.  I ran the first command and it stopped at multiverse (16%) which then changed to 13%.  More to the left of that line it showed 243 b/s and something like 19 hours remaining.

So here's the output that the second part showed:> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


---

### Post by taurus on 2007-04-14
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and then run those two commands from a terminal again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

