---
title: "Couldn't find package amanda-server"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by philostik on 2008-02-09
Greetings:

I am running Gutsy and when I try to run the command
sudo apt-get install amanda-server
it gives me an error saying 'E: Couldn't find package amanda-server'

Has anyone received this error before? Can someone please guide me on this...

Regards,
Manish

---

### Post by jan quark on 2008-02-09
you probably have to enable the sources

please post the result of 

```
cat /etc/apt/sources.list
```

---

### Post by spiderbatdad on 2008-02-09
it is definitely in there. It is a common problem that if you installed Ubuntu without a working internet connection, your sources get commented out. Edit your sources list to look like mine, by removing the # marks in front of the downloadable sources:```
gksu gedit /etc/apt/sources.list
```

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

save the file. then run ```
sudo apt-get update
```

---

### Post by philostik on 2008-02-09
Folks:

Thanks you very much for this sharp reply. I realize a problem to be somewhere else.

I had tried assigning my VM machine to new IP and with new host name. Now, when I open /etc/apt/apt.conf, it reads 
Acquire::http::Proxy "http://<username>:<password>@<old_host_name>:80/";

Any idea how should I modify this file?

Once again, thank you for such quick replies.


Regards,
Manish

---

### Post by spiderbatdad on 2008-02-09
maybe this: ```
HTTP_PROXY=
http_proxy=
```

---

### Post by philostik on 2008-02-09
Friends:

I emptied the file after reading few blogs and it worked! Thanks alot for your timely help...

Have a great weekend...TC

Regards,
Manish

---

