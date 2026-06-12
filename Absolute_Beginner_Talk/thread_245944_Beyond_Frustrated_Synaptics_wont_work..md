---
title: "Beyond Frustrated: Synaptics wont work."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Maxximillian on 2006-08-28
So every bloody time I try to use my synaptics, or try to get a program via command line, I get this error:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured

Im pretty new to linux, but I can find my way around and nothing I try makes any difference.

---

### Post by nickpaton on 2006-08-28
Not sure about a direct answer, but have a look at this post where they are having similar-ish problems:

[http://www.ubuntuforums.org/showthread.php?t=232849]("http://www.ubuntuforums.org/showthread.php?t=232849")

Could be worth carrying out some of the checks listed.

Also, please could you post your Resources List by typing the following into a Terminal:

```
gksudo gedit /etc/apt/sources.list
```

Let us know how it goes.

---

### Post by Maxximillian on 2006-08-28
Ok, I did that command, and here it is:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by nickpaton on 2006-08-28
Can you please exchange the repository list you have for the following one at Psychocats website:

Backup your existing one:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Then copy this one over your existing one making sure you select the correct one for your Ubuntu version: 

[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

And Save and Quit.

Then:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Mapleman on 2006-09-23
The above didn't fix the issue with redhat/clvm, I was previously using quinns repos (beerorkid) same issue, bug reported but from previous email there is an issue with that system as well where a search won't show a bug and than you get spammed with "this has been marked a duplicate" 


Anyone have anything new???

Thanks!:-s

---

