---
title: "PPC - New Install?  Try &quot;Expert&quot; mode!"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by stream303 on 2008-04-28
Now that PPC has been moved to the ports repository, the old installer may still point to older archives, leading to hangs if you try to use a mirror as the default.

For already installed systems, we need to change our /etc/apt/sources.list file as per the release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

For a new installation, I recommend using the "expert" mode, as you can set up the proper repository beforehand, and your /etc/apt/sources.list file will be correct afterwards without any editing.

At the second stage boot: prompt, hit -tab- to stop the countdown timer.  You will be presented with a list of options.

type "expert" (without quotes - for G5 users, type "expert-powerpc64")

Unless you need to make specific changes, accept the defaults.  One default I did change was that after it detected my keyboard as a "generic pc-105" type, I kept that value, and in the NEXT menu, I chose the Macintosh variant.

The good stuff:  When you are presented with "Load Installer Components from CD", select the following by using the space bar:

**Choose mirror - choose mirror to install from**

You will be presented with two choices:

1-manually enter mirror (I forgot the exact wording)
2-*****

Highlight *

It will now automatically display
**ports.ubuntu.com**

Continue on, and unless you need to change something specific, accept the defaults.

When it arrives at "Configure the Package Manager" with "Use a network mirror?", at this stage say YES, since the ports are now pointing to the correct mirrors.

Along the way I was presented with either HTTP: or FTP:, and I chose the default of HTTP:

After installation, I found that my /etc/apt/sources.list file was created properly, but note that all the repos are listed in "Third Party" if you go into Software Sources.  All the main Ubuntu Software sources are UNCHECKED.

Here is what my /etc/apt.sources.list file looks like.  Note that at the bottom of the file, it looks like everything is cleaned up nicely by the installer - I didn't have to touch anything:

```
# deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release Candidate powerpc (20080420)]/ hardy main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy universe
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse
```

Hopefully this might help someone who runs into the same problem now that we have been moved to the ports repositories.

It is unclear if future installers will be coded to take care of this for us.  Next spin 8.04.1 maybe?  Either way, we can do it!

---

### Post by allebone on 2008-06-16
You have no idea how long i have been looking for this after ruining my ppc sources.list file.
 I have tried typing "default sources.list file ppc" into google but no luck until i finally stumbled across this late over heavy caffine intake. 

This information rocks as now after copying your default sources.list file into my ppc build i can finally update it again - 155mb later.

Thanks again this info is golden to ppc users who mess things up but dont want to reload from scratch all the time (i prefer to fix problems instead the hard way)

Ciao

Pete

---

### Post by stream303 on 2008-06-16
Thanks, I'm glad it was helpful.

This was written during the hardy-alpha stages, so I'll have to try it again at the next respin, 8.04.1 and see if it is still an issue.

---

### Post by SphereCat1 on 2009-02-18
Thankyoutthankyouthankyou! Editing the source list was my only hope to upgrade Edgy to Hardy, and now I can! You rock! :D

SphereCat1

---

