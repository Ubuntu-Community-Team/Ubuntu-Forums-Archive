---
title: "cannot access two repos - others are fine"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-01-27
when I reload package info in synaptic, it says it cannot download the repository indexes from these two:

[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz:) 404 Not Found

Are they down, or have I messed up my sources.list? If I have messed up sources.list, how can i fix it?

here is my sources.list:

```

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free

# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.

deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe

# deb http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe

# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com edgy-commercial main 


```

thanks in advance :)

---

### Post by lamego on 2007-01-27
They don't seem te be working (they dont have the packages list), and you should be very careful using non official repositories. You may break your system.

---

### Post by Pobega on 2007-01-27
Yeah, it seems they're down. Might want to take note that it isn't an official repository, though, and anything you find on there can break your system (Especially if it was compiled for Debian and you download it on Ubuntu).

---

### Post by moredhel on 2007-01-27
okay, thanks :)

---

### Post by MaXqUE on 2007-02-08
Hello:

I have had the same problem with that repository. If it is down, that doesn't mean that their gpg keys will not be available since they are on a key server somewhere else. I think we can infer from the response of the key server that they have not renewed their gpg keys. So they this is more than just a server that is down, that whole project is likely gone.  :(

> **Pobega said:**
> Yeah, it seems they're down. Might want to take note that it isn't an official repository, though, and anything you find on there can break your system (Especially if it was compiled for Debian and you download it on Ubuntu).

For us using multimedia application, bleeding edge is the only thing we have in many cases. These applications are new to Debian and even new to Linux. We are used to the warnings about broken packages but sometimes just have to live with it while multimedia for Linux really takes off.

The real question is where have these applications gone? What was there? There is a source for some multimedia projects for Debian but they are specific to their own particular packaging of Debian. Their developer worked on the Agnula/DiMuDi project and is employed buy[ 64Studio]("http://64studio.com/").
I just ran across and [article]("http://www.freesoftwaremagazine.com/articles/c64_studio_project") about them (which I have yet to read myself) at [Free Software Magazine]("http://www.freesoftwaremagazine.com/").

64Studio is in the pro-audio business I believe.

Cheers,
MaXqUE

---

### Post by MaXqUE on 2007-02-08
And the great search oracle at Google has revealed the answer! [Medibuntu ]("http://medibuntu.sos-sts.com/")seems to still be active!

Specific instructions on how to access their repositories is [here]("http://medibuntu.sos-sts.com/repository.php") along with instruction on how to get their sources list.

The instructions put their sources list into a separate fiile in /etc/apt/ as medibuntu.sources. I am not sure how that works in Apt though.

Cheers,
MaXqUE

---

