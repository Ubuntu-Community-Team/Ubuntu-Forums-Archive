---
title: "Add remove problem"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Nick8692 on 2008-04-01
Well, i have been installing apps from the CS's using synaptic recently.  I got an internet connection today, and tried to install something with add remove.  I went into preferences and ticked all but the last two boxes (server and the CD one) but it keeps failing to connect to the servers to updated the list.  The same happens with synaptic, but Firefox works perfectly fine

Can anyone help me with this please? :confused:

---

### Post by Oldsoldier2003 on 2008-04-01
could you show us the error messages and your /etc/apt/sources.list ?

---

### Post by Nick8692 on 2008-04-01
**Error:**

'The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.'

[http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to 169.254.222.96:8080 (169.254.222.96). - connect (113 No route to host)
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to 169.254.222.96:8080 (169.254.222.96). - connect (113 No route to host)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Could not connect to 169.254.222.96:8080 (169.254.222.96). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)
[http://archive.canonical.com/ubuntu/dists/gutsy/Release](http://archive.canonical.com/ubuntu/dists/gutsy/Release)




**sources list**

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted





**i really hope this helps :)**

---

### Post by taavikko on 2008-04-01
Repositories are all commented except the restricted ones...

Open synaptic ->settings->software sources
tick main, universe,restricted and multiverse
and change the server to main server

---

### Post by Nick8692 on 2008-04-01
no, it is still failing to reload

---

### Post by Oldsoldier2003 on 2008-04-01
> **taavikko said:**
> Repositories are all commented except the restricted ones...

Open synaptic ->settings->software sources
tick main, universe,restricted and multiverse
and change the server to main server

yep his initial error message shows he is looking for a link-local address which would indicate at least to me that he is running behind a proxy. He might want to check his proxy settings as well.

---

### Post by Nick8692 on 2008-04-01
how do i do this?

---

### Post by taavikko on 2008-04-01
> **Nick8692 said:**
> how do i do this?

open command line and
```
gnome-network-preferences
```

---

### Post by Nick8692 on 2008-04-01
YEEEEEEEEEEEEE!

Thanks mate :):):)
i had it set to manual connection, so i changed it to internet :)

thank you all :)

---

