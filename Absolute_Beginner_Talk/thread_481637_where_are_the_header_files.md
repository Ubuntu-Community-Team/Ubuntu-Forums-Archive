---
title: "where are the header files?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-06-22
New Ubuntu 7.04 installation. Where are the standard header files - stdio.h, stdlib.h....?? I checked /usr/include, /usr/local/include. If they are not on the system, how do I get them?  Thanks!

---

### Post by kpkeerthi on 2007-06-22
search for linux-header and build-essential in synaptic

---

### Post by bhold on 2007-06-22
Installing build-essential worked. Thanks.

---

### Post by shiraj on 2007-09-14
> **bhold said:**
> New Ubuntu 7.04 installation. Where are the standard header files - stdio.h, stdlib.h....?? I checked /usr/include, /usr/local/include. If they are not on the system, how do I get them?  Thanks!

I don't find build-installer in Synaptic. How do I install it?

---

### Post by Majorix on 2007-09-14
You have to enable more repos. Go to system > admin > software sources and enable the repos from there then search again. You should find it.

---

### Post by schorsch on 2007-09-14
> **shiraj said:**
> I don't find build-installer in Synaptic. How do I install it?
.... it's called "build-essential" ....

---

### Post by shiraj on 2007-09-14
sorry, I meant build-essential. I also enabled all the "downloadable items" in software sources and I still don't find build-essential from Synaptic. Help!!

---

### Post by Majorix on 2007-09-14
Can you please post the output of
```
sudo apt-get install build-essential
```

---

### Post by shiraj on 2007-09-15
The following is the messgae when I do
sudo apt-get install build-essential.....Thanks.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

---

### Post by jordanmthomas on 2007-09-15
weird, what's the output of
```
cat /etc/apt/sources.list
```

---

### Post by shiraj on 2007-09-15
output of cat /etc/apt/sources.list ...I have removed some comment lines

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by schorsch on 2007-09-15
Did you type
```
sudo apt-get update
```
after editing your sources and before trying to install the package?

---

### Post by Majorix on 2007-09-15
I believe your sources.list is incomplete. Request someone with Feisty to upload their sources.list file for you so you can use that instead. Also don't forget to
```
sudo apt-get update
```

---

### Post by shiraj on 2007-09-15
could someone please upload here  sources.list  file. Thx.

---

### Post by Majorix on 2007-09-15
I would remove my email from here as it can be used by spam-bots.

They can also upload here, just check back.

---

### Post by shiraj on 2007-09-15
could somebody please give a pointer from where I could upload sources.list ?

---

### Post by splintercellguy on 2007-09-16
My sources.list:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


---

### Post by shiraj on 2007-09-16
thanks a lot - but I get the same error when I try sudo apt-get install build-essential after sudo apt-get update ---- package build-essential is not available....

---

