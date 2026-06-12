---
title: "Flash installed but still no flash??"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Beastybob on 2007-12-19
Hey,

I have just installed Ubuntu for the first time, I'm very new to Linux. I have almost everything I need up and running except one thing.

I can't seem to get flash to work with Firefox. I have tried installing it through the prompt that I get in Firefox when ever I visit a site that needs flash. The first time I did that it installed fine, but when the page reloads it still asks me to install flash. When I go through the install process again it says that it's already installed?

I have tried installing it all the ways I can find and they all seem to install or tell me that it's already installed, but I still get the prompt in Firefox for flash and no flash seems to load on the page?

Does anyone have any ideas how to fix this?

Please be gentle, I'm very n00b so I will need very clear explanations.

Thanks

---

### Post by Inxsible on 2007-12-19
how did you install flash?

i think you need to install the mozilla plugin too. Try [this thread]("http://ubuntuforums.org/showthread.php?t=632107") if you havent already done so

---

### Post by NateMan on 2007-12-19
try sudo apt-get install ubuntu-restricted-extras

if not then manually install flash.

---

### Post by jan quark on 2007-12-19
Had a similar problem. I installed flash via packet manager and it did not work. Some md5sum mismatch problem. Try to google this. Then i installed flash Version: 9,0,115,0 manually from the official adobe web site and now have no problems anymore.

---

### Post by SyL on 2007-12-19
If it doesn't work with the package.

Download the tar.gz here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN")

untar and run
```
./flashplayer-installer 
```

---

### Post by NilsE on 2007-12-19
This is a known problem with the version in the repositories.  The above recommendation works plus there are other options for the install. I used the following deb file.

First uninstall the one that is in the repos and then install this one via gdebi which actually installs the same file as above from Adobe..

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

### Post by Beastybob on 2007-12-19
> **NateMan said:**
> try sudo apt-get install ubuntu-restricted-extras

if not then manually install flash.

Ok,

I have run that but now when I get:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I have ran 'dpkg --configure -a in the terminal and I get :

```
dpkg: requested operation requires superuser privilege
```

What now?

Please excuse my utter n00bishnes

Thanks for the help so far.

---

### Post by LaRoza on 2007-12-19
> **Beastybob said:**
> 
I have ran 'dpkg --configure -a in the terminal and I get :

```
dpkg: requested operation requires superuser privilege
```


Run it again, but with "sudo"

```

sudo dpkg --configure -a

```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by NilsE on 2007-12-19
Put sudo in front of it like this

sudo dpkg --configure -a

Question: Did you **completely remove** flashplugin-nonfree before you tried the install?

---

### Post by 4iko on 2007-12-19
I had the same problem
the easiest way is to open Synaptic manager
type flashplugin (or plashplugin-nonfree)
and install it from there
let me know if it worked?

---

### Post by Beastybob on 2007-12-19
You guys are awesome. All working great now.

The manual install seemed to do the trick.

I tried from Synaptic manager at the start and it installed just didn't seem to work.

Anyway, all is well for me now.

Thanks for all your help :)

---

### Post by NilsE on 2007-12-19
> **Beastybob said:**
> You guys are awesome. All working great now.

The manual install seemed to do the trick.

I tried from Synaptic manager at the start and it installed just didn't seem to work.

Anyway, all is well for me now.

Thanks for all your help :)
Yup, the one in Synaptic is BAD and may not be fixed for awhile.

---

### Post by LaRoza on 2007-12-19
> **NilsE said:**
> Yup, the one in Synaptic is BAD and may not be fixed for awhile.

Actually, it should be fixed soon, and the good flash can be installed if you enable "Pre-release Updates" in System->Administration->Software Sources.

---

### Post by NilsE on 2007-12-19
> **LaRoza said:**
> Actually, it should be fixed soon, and the good flash can be installed if you enable "Pre-release Updates" in System->Administration->Software Sources.
Correct but it is not there yet so we need to continue to recommend alternatives until it is.

---

### Post by LaRoza on 2007-12-19
> **NilsE said:**
> Correct but it is not there yet so we need to continue to recommend alternatives until it is.

If you enable the other source, it is in the repos.

---

### Post by NilsE on 2007-12-19
> **LaRoza said:**
> If you enable the other source, it is in the repos.
I did enable ALL sources and installed it and got the same problem. I believe the "source" is in the repos but not the installable file.

I am up in Hardy right now or I would show you my source list.

---

### Post by LaRoza on 2007-12-19
> **NilsE said:**
> I did enable ALL sources and installed it and got the same problem. I believe the "source" is in the repos but not the installable file.

I am up in Hardy right now or I would show you my source list.

I don't know about Hardy, sorry. In Gutsy, what I said will fix it.

---

### Post by NilsE on 2007-12-19
> **LaRoza said:**
> I don't know about Hardy, sorry. In Gutsy, what I said will fix it.
My answer was based on Gutsy.  I was just saying I happened to be up in Hardy and could not show you my Gutsy sources list.

I do see another version in the repos "9.0.48.0.2+really0ubuntu12 (Gutsy)"  but when installed it has the same problem where it does not install the plugin in FF,

Maybe my Gutsy sources list is not correct even though I have selected Pre-Release updates so here it is for your reading pleasure:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu gutsy-backports main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by NilsE on 2007-12-19
So you don't think I am going crazy here are screen shots of my sources gui

---

### Post by jan quark on 2007-12-19
Congratulation. You are the first person in  the forum whom my short Ubuntu experience did really help.:lolflag:

---

### Post by coloured on 2007-12-19
> **NilsE said:**
> This is a known problem with the version in the repositories.  The above recommendation works plus there are other options for the install. I used the following deb file.

First uninstall the one that is in the repos and then install this one via gdebi which actually installs the same file as above from Adobe..

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

is there an AMD64 version of the above mentioned deb?

cheers
Jurgen

---

### Post by RomeReactor on 2007-12-19
Hi. Yes, [here it is]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466"). More information on that in the [original thread]("http://ubuntuforums.org/showthread.php?p=3929669").

---

