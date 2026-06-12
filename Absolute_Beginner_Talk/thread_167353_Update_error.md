---
title: "Update error"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by zip_000 on 2006-04-28
Hi, I'm having some sort of error when I try to update. The package manager says that there are two updates available, but when I try it I get this error (twice):

"E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)"

Can anyone tell me what this means?

I tried sudo apt-get update instead, but that didn't work either.

I recently installed Cups and Samba on this computer, along with some Lexmark printer drivers, if that has anything to do with anything.

Thanks for any help!

---

### Post by Sef on 2006-04-28
Have you recently updated firefox?

---

### Post by zip_000 on 2006-04-28
Um, not that I'm aware of - I certainly haven't updated it on my own, but if it were in the update list, I may have - I don't usually read the update list, I just install the updates it tells me to.

---

### Post by zip_000 on 2006-05-05
I'm just bumping this up to the top - I'm still having the same problem...

...I created a directory in my root folder called "/root" - which seems redundant to me - and it seems to have let me update...what is the deal with that?  Can anyone explain it to me?

---

### Post by Sef on 2006-05-05
Copy and paste ur sources list here.

Open the terminal (Applications > Accessories > Terminal)

sudo gedit /etc/apt/sources.list

---

### Post by zip_000 on 2006-05-05
Hi - thanks for the quick response!  (I modified me previous message before I saw that you had responded).

Here goes the sources list...

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

---

### Post by Sef on 2006-05-05
> ...I created a directory in my root folder called "/root" - which seems redundant to me - and it seems to have let me update...what is the deal with that? Can anyone explain it to me?

Maybe it's getting confused by the two roots.

---

