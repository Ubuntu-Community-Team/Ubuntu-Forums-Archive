---
title: "Software Sources broken"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Bölvaður on 2008-04-14
Past week I haven't been able to download and update my programs with apt-get or anything. Apparently I cannot connect to any repositories server, I've tried Iceland (my country), UK, USA, Germany.... main, but nothing works.
I know a guy from my town that has the same problem, but he just had his computer Ubuntuized so understandably he haven't been able to fix his problem.

...so what can I do?


When I try to update my repositories through Software Sources it only gives me 

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)

[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)




```
sudo apt-get update
Err http://archive.ubuntu.com gutsy Release.gpg
  Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)
Err http://archive.ubuntu.com gutsy/main Translation-en_US
  Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)
Err http://archive.ubuntu.com gutsy/universe Translation-en_US
  Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2  Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```


/etc/apt/sources.list  I have only one line that isn't commented out:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe

---

### Post by forrestcupp on 2008-04-14
Go ahead and post the contents of sources.list so we can just look at it.  Also, look in /etc/apt and see if you happen to have a backup of sources.list that you can restore to.

---

### Post by Bölvaður on 2008-04-14
Like I said the only line in /etc/apt/sources.list is

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe


```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
# deb http://is.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://is.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# deb http://download.tuxfamily.org/screenlets gutsy screenlets
# deb http://blognux.free.fr/debian unstable main
# deb http://ppa.launchpad.net/rharding/ubuntu gutsy main
# deb-src http://ppa.launchpad.net/rharding/ubuntu gutsy main
# deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
# deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator



## Wine, Ubuntu Gutsy (7.10):
# deb http://wine.budgetdedicated.com/apt gutsy main
# deb-src http://wine.budgetdedicated.com/apt gutsy main


deb http://archive.ubuntu.com/ubuntu/ gutsy main universe
```


My backups contain the following 
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://is.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://is.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
#deb http://download.tuxfamily.org/screenlets gutsy screenlets
deb http://blognux.free.fr/debian unstable main
deb http://ppa.launchpad.net/rharding/ubuntu gutsy main
deb-src http://ppa.launchpad.net/rharding/ubuntu gutsy main
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator



## Wine, Ubuntu Gutsy (7.10):
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main
```

and when I used that backup it didn't give me a single positive result :(


*edit*
I remember that the source.list that was a backup worked like a charm like 1-2 months ago. Have no idea what have changed.

---

### Post by PeterJS on 2008-04-14
> **Bölvaður said:**
> 
When I try to update my repositories through Software Sources it only gives me 

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to the-equalizer.net:8080 (86.58.130.195). - connect (111 Connection refused)

[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) **Could not connect to the-equalizer.net:*8080* (86.58.130.195). - connect (111 Connection refused)**


This is the crux of your problem, your sources list itself looks fine. The problem is that your system is trying to use a proxy and failing. Without knowing more about the reason you set using the proxy in the first place I can't recommended if it would better to try and fix the proxy set up or just not use it.

---

