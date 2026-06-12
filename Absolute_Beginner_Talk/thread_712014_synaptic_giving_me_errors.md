---
title: "synaptic giving me errors??"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-01
I'm trying to download some stuff through synaptic and every time i try to download anything it gives me this error:
```
W: Failed to fetch http://mx.archive.ubuntu.com/ubuntu/pool/universe/f/freedoom/freedoom_0.5-1_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch http://mx.archive.ubuntu.com/ubuntu/pool/universe/p/prboom/prboom_2.4.6+dfsg-1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



```

all that changes is the package name.

---

### Post by Cypher on 2008-03-01
Are you connected to the Internet? The fact that I see "localhost:4001 (127.0.0.1)" indicates that you might not be..

---

### Post by RadiationHazard on 2008-03-01
haha. i'm posting this thread:lolflag:

---

### Post by Cypher on 2008-03-01
Hehe..In that case show us the output of
```

cat /etc/apt/sources.list

```

---

### Post by SunnyRabbiera on 2008-03-01
it might be that repository, every so often the mirrors go out.

---

### Post by RadiationHazard on 2008-03-01
it's giving me this?

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
deb http://download.tuxfamily.org/screenlets gutsy screenlets

```

didn't really read it yet but from first glance i'm pretty sure i need to update something...

---

### Post by forrestcupp on 2008-03-01
Like already said, it could just be the mirror is temporarily out.  But try closing Synaptic and in a terminal type:
```
sudo apt-get update
```
Then try again and see if it helps.

Edit:
Also, are you trying to download something from a 3rd party repository?  If so, maybe you forgot to add the key.

---

### Post by RadiationHazard on 2008-03-01
When i type in sudo atp-get update i get this...

```
Err http://mx.archive.ubuntu.com gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://mx.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://download.tuxfamily.org gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://download.tuxfamily.org gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://download.tuxfamily.org gutsy/screenlets Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/gutsy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://download.tuxfamily.org/screenlets/dists/gutsy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://download.tuxfamily.org/screenlets/dists/gutsy/screenlets/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by zvacet on 2008-03-01
Under** system>admin<software sources** switch to main server.

---

### Post by RadiationHazard on 2008-03-01
when i try to do that i get this error...

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```
http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://download.tuxfamily.org/syzygy42/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://download.tuxfamily.org/screenlets/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://download.tuxfamily.org/screenlets/dists/gutsy/screenlets/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

```

---

### Post by RadiationHazard on 2008-03-01
should i just wipe my drive? and start over?

---

### Post by zvacet on 2008-03-01
Change

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets

to 

#deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
#deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
#deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets

and

# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

to 
 deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multivers

 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

save and close

```
sudo apt-get update && sudo apt-get upgrade
```

---

