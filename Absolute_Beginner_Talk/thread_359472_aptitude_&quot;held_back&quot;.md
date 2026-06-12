---
title: "aptitude &quot;held back&quot;"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-02-12
I use aptitude to update my 6.06 dapper.

The system update icon says there are 8 updates available, but when I do an update-->upgrade aptitude holds back the packages which by the way are the linux686 image and the 386 as well amongst others.

I don't really like using synaptic, but I fired it up and seemed as if it would let me install the packages.  

My question is: should I force aptitude to install the packages (or do them through synaptic) or is there a reason aptitude is holding them back.

Here is what my CLI outut looks like:

charles@charles-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  linux-image-386 linux-image-686 linux-restricted-modules-386 linux-restricted-modules-686
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
charles@charles-laptop:~$

Thanks in advance for any help...

---

### Post by aysiu on 2007-02-12
Try this: ```
sudo aptitude dist-upgrade
```

---

### Post by charles.g.moore on 2007-02-12
wont that upgrade me to edgy?

---

### Post by aysiu on 2007-02-12
> **charles.g.moore said:**
> wont that upgrade me to edgy?
Not unless you change your /etc/apt/sources.list

---

### Post by charles.g.moore on 2007-02-12
Here is my sources.list

charles@charles-laptop:~$ cat /etc/apt/sources.list

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

#Webcam
# deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

---

### Post by aysiu on 2007-02-12
With that sources.list, the command will not upgrade you to Edgy.

---

### Post by charles.g.moore on 2007-02-12
cool, thank you...

if its not too much trouble...

1.why am i using the dist-upgrade in this instance?  
2.is this some kind of force?
3.why would aptitude choose to hold these particular packages back?
4.what purpose do the linux-686/386-image packages serve?
5.this has happened before, if it does again, would the "dist-upgrade" command be the thing i should automatically do?  
6.Or is it only ok in this instance?

---

### Post by aysiu on 2007-02-12
Read [this thread](http://www.ubuntuforums.org/showthread.php?t=86198). Apparently *dist-upgrade* is the preferred way to do updates all the time.

---

### Post by charles.g.moore on 2007-02-12
That is a quite involved thread, thanks for the help...
Definitely cleared things up!

---

