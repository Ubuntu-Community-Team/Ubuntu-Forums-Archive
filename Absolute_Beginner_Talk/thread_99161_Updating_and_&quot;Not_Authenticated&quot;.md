---
title: "Updating and &quot;Not Authenticated&quot;?"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by GoUbuntu on 2005-12-05
Hi,

I had a go trying to add some repositories, and then I got told that I had some updates to install.  When I clicked to install, it warned me that some of them were 'Not Authenticated'.  Should I be worried?  Or just install them anyway?

I don't really understand what all of the updates are.


Thanks,
Brendon

---

### Post by timfrost on 2005-12-05
You willl get a warning about packages that are not authenticated if you install packages from any source other than the default ones.

This warning means that the package has not been digitally signed using one of the trusted PGP/gnupg keys.

---

### Post by Zentropic on 2005-12-05
Not just non-default. I am using a stock sources list and began to get it constantly from the US mirrors. It was suggested to remove the "us" from the url to fix it. This worked, but now the issue has returned.

This is for a security update for the mysql client, so we're not talking multi or universe either.

This is a serious problem if keys can't remain trusted.

---

### Post by kalos on 2005-12-05
Not having signed repos trivializes the security. Maybe this should be submitted as a bug.
Zentropic: What is the name of the packages you are trying to install?

GoUbuntu: What sources are in your sources.list Find out: ```
sudo cat /etc/apt/sources.list
```

-kalos

---

### Post by GoUbuntu on 2005-12-09
Hi,

Thanks for the help.

Here's the result from sudo cat /etc/apt/sources.list

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main r estricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-backports main restricted unive rse multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-backports main restricted u niverse multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
```


Do these need to be edited manually, or can it be changed from Update Manager -> Preferences?

BTW, I tried to remove "Universe" using Update Manager -> Preferences just before I got the list.

Thanks once again,
Brendon

---

