---
title: "Unable to install Midnight Commander"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Hank123 on 2007-01-04
Hey!

I got a problem installing Midnight Commander. I got Ubuntu up and running, i got version 6.06 server (so command line only). 

When i try to  do "sudo apt-get install mc"

i got the error message 

E: Couldn't find package mc

There must be something very easy that i'm overlooking, and i tried several things but i just cannot get to it.

Thanks for your assistance.

Hank

---

### Post by Iarwain ben-adar on 2007-01-04
Hiya,
Welcome!

Are you sure it's called mc? (i'm not on my linux-box atm, so can't check)

Do a ```
sudo apt-cache search midnight
```

This should show you all packages with midnight in it's description :wink:

Or if you are sure it is called that way,
enable multiverse repo's.


Iarwain

---

### Post by Pobega on 2007-01-04
Try updating and upgrading through Aptitude first, I know that has cleared up some issues for me in the past.

**Edit:** I know it's called mc, I have it downloaded at the moment.

---

### Post by Hank123 on 2007-01-04
Ok, i ran aptitude, but i'm not sure what to upgrade exactly. I upgraded all the installed packages, but there's still no Midnight commander to be found. (and i don't know where to find it in the "not installed packages list", if it's in there somewhere anyway

Thanks.

Hank

---

### Post by Pobega on 2007-01-04
> gksudo nano /etc/apt/sources.list

This is mine:

> ## Ubuntu System76 Repositories Listing

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## System76 Driver Repository
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./

---

### Post by Hank123 on 2007-01-04
Wow. it works now. I added the things you had in your sources.list, replaced edgy with dapper, did apt-get update, and suddenly after that, the package could be found.

this makes my day!

Thanks a lot for the help!

Hank

---

### Post by Pobega on 2007-01-04
No problem, my sister had this same problem, this fixed it for us too.

---

### Post by az on 2007-01-04
mc is in the universe repo.  You just need to enable that - regardless of what version of Ubuntu you are running.

---

