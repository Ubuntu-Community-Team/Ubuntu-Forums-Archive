---
title: "problem installing 7.10"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by grainbarcelona on 2007-11-01
Hi, can anybody help?

I get blocked when installing 7.10. (upgrading from 7.04) 
In the very beginning of the installation process (fetching), I get the message below & the program tells me to check my network settings and throws me out of the installation process. My network settings and internet connection are ok. I uninstalled Wine, to see whether that would help. No difference, same message again. 

Any suggestions what I should do?

Thnx!

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve ‘wine.lowvoice.nl’

---

### Post by damotor on 2007-11-01
edit your /etc/apt/sources.list and comment all but the official repositories.

---

### Post by grainbarcelona on 2007-11-01
Thanks, Damotor,
But can you be a bit more specific how to do this? What commands to use in the terminal? 
Sorryyy, but I'm vry new to Ubuntu

---

### Post by hoges on 2007-11-01
> **damotor said:**
> edit your /etc/apt/sources.list and comment all but the official repositories.
go to the terminal and type:
sudo gedit /etc/apt/sources.list

It will ask for your login passoword.

Then comment out all the unofficial repositories (from memory anything that doesn't have "Canonical" in the url) using #.

Or, you could go Applications-->>Add/Remove... and remove them from the option list. Terminal is probably better, though.

---

### Post by grainbarcelona on 2007-11-02
Thanks Damotor and Hoges!
I followed your instructions & it worked. I am a proud user for Gutsy now
Very kind of you

---

### Post by jeffjohn on 2007-11-02
Yep - had exactly that experience.  Just REM (##) out all those offending source.list 'fetch' failures, Save, Exit and try again! jeffjohn

worked a dream; but sleep on it as it takes a while!!

---

### Post by Tony3286 on 2007-11-03
Trying to get my system ready for upgrade from Feisty to Gutsy.
Anything below in repositories that I should remark out to be safe?

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

Thanks Tony

---

### Post by hoges on 2007-11-06
Hey Tony,

Sorry, been away for a couple of days, and just got your message. Hope you found help in the meantime, but if not...

As far as I can tell, nothing here would cause much of a concern. The urls that have restricted at the end are for the restricted repositories. They contain things such as mp3 support and packages that legally can't be included in the official release of Ubuntu. You could comment that out if you want, but there isn't really much of a need. For the OP, they probably would of had a line that contained 'wine.lowvoice.nl’ which couldn't be found. Commenting that out seemed to have worked.

Having said that, everything is downloaded and verified before an install. Best bet is to hit upgrade and see what happens. It will tell you if there's a problem, and it will stop downloading. It won't install if there's a problem with a package.

If you're really in doubt, download the alternative cd. When you boot that up, it has an upgrade option, thus eliminating the need to fix up the sources.list file.

Anyway, good luck with it and hope you get it all sorted.
Cheers
Hoges

---

