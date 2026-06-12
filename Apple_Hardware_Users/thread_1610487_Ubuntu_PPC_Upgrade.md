---
title: "Ubuntu PPC Upgrade"
date: 2010-10-31
forum: Apple Hardware Users
---

### Post by newbody on 2010-10-31
[FONT=Arial][SIZE=4]Hy,

I'm running Ubuntu 10.04 on my PPC.
Now I want to use 10.10.
Is that possible?
I insert: 
[/SIZE][/FONT][FONT=Arial][SIZE=4]sudo do-release-upgrade

But he said: No new release of Ubuntu found

So, can I upgrade?


[/SIZE][/FONT]

---

### Post by el_heffe on 2010-11-02
I cannot recall, but you may have to open your sources, ensure that you have chosen "Latest Distro" or something to that effect.  Essentially you are looking to change it away from the "Stable Release(LTS)" and go to the latest release.  Then, do an update, and if you open the Update Manager under the Administration menu you should see the upgrade button on the top right.  If not, you should be able to do an sudo apt-get dist-upgrade.  I think that should do you fine.  BUT, I cannot confirm this on PPC as my HD took a dump.  YMMV.

---

### Post by newbody on 2010-11-03
He didn't find new reaeases

---

### Post by linuxopjemac on 2010-11-03
in /etc/apt/sources.list you have to change all lucid entries into maverick. Then do
```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

success

---

### Post by newbody on 2010-11-03
> **linuxopjemac said:**
> in /etc/apt/sources.list you have to change all lucid entries into maverick. Then do
```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
 
success
 
 
I changed all Lucid
 
But the Code doesn't work :(

---

### Post by linuxopjemac on 2010-11-03
can you post me the output of:
```

cat /etc/apt/sources.list
```

please?

---

### Post by linuxopjemac on 2010-11-03
It's all there:
[http://ports.ubuntu.com/ubuntu-ports/dists/maverick/](http://ports.ubuntu.com/ubuntu-ports/dists/maverick/)

---

### Post by newbody on 2010-11-03
I downloaded:
[Contents-powerpc.gz]("http://ports.ubuntu.com/ubuntu-ports/dists/maverick/Contents-powerpc.gz")

What should I do now?



Output of:   
cat /etc/apt/sources.list 

[HTML]# deb cdrom:[Ubuntu 10.04 LTS _maverick Lynx_ - Release powerpc (20100428)]/ maverick  main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://ports.ubuntu.com/ubuntu-ports/ maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ maverick-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://ports.ubuntu.com/ubuntu-ports/ maverick-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ maverick-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ maverick-security multiverse
[/HTML]

---

### Post by newbody on 2010-11-03
Now it works, but he didn't find new releases

It works with:

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick main restricted universe multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick main restricted universe multiverse

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick-updates main restricted universe multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick-updates main restricted universe multiverse

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse

#deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick-backports main restricted universe multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) maverick-backports main restricted universe multiverse

---

### Post by linuxopjemac on 2010-11-03
I don't know whether it will work or not. But you have the right sources.list file I think.

---

