---
title: "cups update authentication?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by biboch on 2008-01-09
Hi, there... I've been running a desktop Ubuntu system now for over a year, and I really love it... but I'm still kind of a "basic user." (on 7.10) This morning in doing my usual update, I get a bunch of cups files to install. When I try to install them, I get a message that they are not authenticated. Oops, what's that mean? I don't want to install anything that's not sure...
I research the question a little in the fora and elsewhere, but only old and non-pertinent information. Then I came across the official Ubuntu warning message this morning that says that there is a security problem with cups, and people need to update.
So how do I know if the cups update that shows up in the Update Manager is for real, or if it is some bad guys trying to take advantage of this problem? It says it isn't authenticated...
What do I do to work this out? To install, or not to install? That is the question... 
Thanks for the help!

---

### Post by perlluver on 2008-01-09
I have it installed and the system seems fine, although it didn't warn me about not being authenticated.

---

### Post by Mular on 2008-01-09
Yup I just got the update now, and it said nothing about not being authenticated

---

### Post by bapoumba on 2008-01-09
Could you please post the error message ?

---

### Post by biboch on 2008-01-09
Hmmm... Okay, thanks for the confirmations.
I'm getting mine off the Swiss mirror site, maybe there is a problem with that.
I'll try it again later, but since I don't really know how the authentication thing works, I'm just hoping that somebody "out there" picks up on it.

---

### Post by biboch on 2008-01-09
Okay, Bapoumba, it is a window that comes up saying:
"Apply the following changes.... etc

WARNING

You are about to install software that CAN'T BE AUTHENTICATED!
Doing this could allow a malicious individual to damage or take control of your system.

(Below this appears a sub-window with :)
NOT AUTHENTICATED
  libcupsys2
  libcupsimage2
      ....etc for a total of 29 packages, followed by a list of packages to be upgraded.

Then I have buttons to either "cancel" or "install".

That's it. So far, I have chosen cancel. Thanks for your advice!

---

### Post by bapoumba on 2008-01-09
I just applied the updates, from the main ubuntu repos and it went okay. Please post your sources.list:
```
cat /etc/apt/sources.list
```
or try using the main repos if you know how to change them.

---

### Post by biboch on 2008-01-09
Here is my source list:


deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse universe
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe

What does this tell us?

---

### Post by bapoumba on 2008-01-09
As you said, you are using the ch repos ;)

One thing I'm not sure of, though, is that the two packages you mentioned did came up in the upgrade, but from the security repos, on my system. You are using the same ones. May be try again later, as several of us had the upgrade without trouble.

An authentication error will not block the upgrade, but it tells that the package you are trying to install either was not signed (but everything from Ubuntu repos is signed) or did not verify the authentication test. In this case I assume something happened when downloading the packages and that the files you got were corrupt (thus failing the md5 verification).
The safe side would be to run :
```
sudo apt-get update
sudo apt-get dist-upgrade
```
and see if you still get the error.

---

### Post by biboch on 2008-01-09
Bapoumba, I just changed the repos to main, and ran the Update Manager.
It all worked without problem. I guess something in the Swiss mirror was not reflecting properly.
Many thanks for your help! Je te souhaite beaucoup de fraises!

---

### Post by bapoumba on 2008-01-10
You're welcome, glad to see you got it solved :KS

And the line in my sig referring to strawberries (J'aime les fraises) is a little pun for a friend who coded overnight a [small script called Tagada]("http://bapoumba.wordpress.com/2007/04/30/tagada-la-vie-en-rose-according-to-xbright/"). Unfortunately, he did not maintain it :(
As a side note, another pun [in another friend's sig]("http://ubuntuforums.org/member.php?u=13538"), regarding my sig  ;)

---

### Post by static chaser on 2008-01-18
I still have the same problem. I tried bapoumba suggestion. It said that 4 were held back cupsys cupsys-bsd cupsys-client cupsys-common.  Here is what I get when I run cat /etc/apt/sources list:
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Any help would be greatly appreciated on solving this problem.

---

### Post by coolcar on 2008-04-05
I am on Gutsy and was getting this not authenticated error for the CUPS updates for the last two days. I was aborting the updates because of this errors and its suddenly stopped today. 

I am describing the updates below. Looks like it was the same problem with the mirror servers having unsigned updates. 

You are about to install software that can't be authenticated

cupsys-client (version 1.3.2-1ubuntu7.5) will be upgraded to version 1.3.2-1ubuntu7.6
cupsys-common (version 1.3.2-1ubuntu7.5) will be upgraded to version 1.3.2-1ubuntu7.6
libcupsimage2 (version 1.3.2-1ubuntu7.5) will be upgraded to version 1.3.2-1ubuntu7.6
libcupsys2 (version 1.3.2-1ubuntu7.5) will be upgraded to version 1.3.2-1ubuntu7.6
libcupsys2-dev (version 1.3.2-1ubuntu7.5) will be upgraded to version 1.3.2-1ubuntu7.6

---

