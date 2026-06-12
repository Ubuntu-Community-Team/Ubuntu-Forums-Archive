---
title: "sources.list trouble"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by guitarmaniac on 2006-12-15
I am having trouble with my sources.list
here it is

> # Ubuntu Main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse

# Bug fix Updates

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

# Ubuntu Security Updates

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

# Backports Repository

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# Bleeding Edge Wine Packages

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

# Latest Amarok Packages

deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main

## nVidia drivers Ubuntu packages

deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END

Whenever I update I get this error

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://kubuntu.org](http://kubuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

Now i have used the gpg keys that i got from the various sites that i got the repositories from but for some reason I keep getting this error.](*,)

---

### Post by BitTorrentBuddha on 2006-12-15
You should be able to download from the repository despite most GPG key errors I believe.

---

### Post by arnieboy on 2006-12-16
delete the following lines from sources.list in the end (after AX repos start):
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
and do a
```
sudo apt-get update
```

---

### Post by guitarmaniac on 2006-12-17
I found this thread [http://ubuntuforums.org/showthread.php?t=281825&highlight=%23+seveas-edgy+contains+some+nice+stuff+including+w32codecs%2Clibdvdcss2%2Cflashplugin-nonfree+%23+with+flash+9+beta+some+nice+meta-packages+%23+http%3A%2F%2Fseveas.imbrandon.com+%23+http%3A%2F%2Fseveas.imbrandon.com%2Fdists%2Fedgy-seveas+deb+http%3A%2F%2Fseveas.imbrandon.com+edgy-seveas+custom+extras+seveas-meta+backports+deb-src+http%3A%2F%2Fseveas.imbrandon.com+edgy-seveas+custom+extras+seveas-meta+backports]("http://ubuntuforums.org/showthread.php?t=281825&highlight=%23+seveas-edgy+contains+some+nice+stuff+including+w32codecs%2Clibdvdcss2%2Cflashplugin-nonfree+%23+with+flash+9+beta+some+nice+meta-packages+%23+http%3A%2F%2Fseveas.imbrandon.com+%23+http%3A%2F%2Fseveas.imbrandon.com%2Fdists%2Fedgy-seveas+deb+http%3A%2F%2Fseveas.imbrandon.com+edgy-seveas+custom+extras+seveas-meta+backports+deb-src+http%3A%2F%2Fseveas.imbrandon.com+edgy-seveas+custom+extras+seveas-meta+backports") and it seemed to do the trick.

---

